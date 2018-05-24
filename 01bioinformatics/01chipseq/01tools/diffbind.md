# Diffbind Notes

This is a bioconductor package which can be used to find differentially bound sites for Chip Seq experiments. More details on [Bioconductor](https://bioconductor.org/packages/release/bioc/html/DiffBind.html)

### Diffbind Output Format
Quoting from the [reference manual](https://bioconductor.org/packages/release/bioc/manuals/DiffBind/man/DiffBind.pdf)

| Col Name | Description |
| :--- | :--- |
|`Chr` | Chromosome of binding site|
|`Start`|  Starting base position of binding site|
|`End` |  End base position of binding site|
|`Conc`|  Concentration – mean (log) reads across all samples in both groups
|`Conc_group1` |  Group 1 Concentration – mean (log) reads across all samples first group|
|`Conc_group2` |  Group 2 Concentration – mean (log) reads across all samples in second group|
|`Fold` |  Fold difference – mean fold difference of binding affinity of group 1 over group2 |
|`(Conc1 - Conc2)`|  Absolute value indicates magnitude of the difference, and sign indicates which one is bound with higher affinity, with a positive value indicating higher affinity in the first group
|`p-value` |  p-value calculation – statistic indicating significance of difference (likelihood difference is not attributable to chance)|
|`FDR` |  adjusted p-value calculation – p-value subjected to multiple-testing correction|

If bCalled is TRUE and caller status is available, two more columns will follow:

Called1 Number of samples in group 1 that identified this binding site as a peak

Called2 Number of samples in group 2 that identified this binding site as a peak

If bCounts is TRUE, a column will be present for each sample in group 1, followed by each sample in group 2. The Sample ID will be used as the column header. This column contains the read counts for the sample.

### Details on bCounts

> The normalized counts returned by dba.report()are the raw reads divided by the normalization factors, obtained by calling DESeq2::sizeFactors().[Source](https://support.bioconductor.org/p/68134/#68168)

> OK, I've looked into this a bit more deeply. For the default case when using DESeq2, where bFullLibrarySize=TRUE, DiffBind sets the factors to be the full library sizes (the number of reads in the .bam files) normalized to the smallest library (dividing by the minimum library size). So the smallest library size gets a normalization factor equal to 1, while the others are greater than one. This simple normalization method is only used when bFullLibrarySize=TRUE and method=DBA_DESEQ2.  If you set bFullLibrarySize=FALSE, using only the number of reads that overlap consensus peaks, then estimateSizeFactors() is called and the standard mean ratio method is used to calculate the normalization factors, none of which should be equal to 1.*[Source](https://support.bioconductor.org/p/85046/#85060)

> Yes, if there isn't a big imbalance in the signal between sample groups, bFullLibrarySize=FALSE is preferred. This used to be the default, but we changed it to be more conservative as the consequences are worse that way if the assumptions are not met.[Source](https://support.bioconductor.org/p/85046/#85069)

> The bFullLibrarySize option determines the total read count used for normalization. If bFullLibrarySize=FALSE, the number of reads that overlap consensus peaks is used for each sample (basically, the sum of all the counts). This is the best option for cases where most of the peaks are not expected to change their binding affinity significantly. For the more conservative default, bFullLibrarySize=TRUE, the total number of aligned reads in the .bam file is used (basically the sequencing depth). This is more appropriate in cases where you expect dramatic shifts in binding affinities, or if you are not sure what to expect.[Source](https://support.bioconductor.org/p/79469/#79473)

So in summary it depends on if you used bFullLibrarySize=FALSE/TRUE. If you set that to be `true` then the full library sizes will be used for normalization and you will find one of sample to have integer counts indicating that sample had the least number of reads and it had a normalizaion denominatior of 1, If you set it to `false` then it will get the normalization factors per peak.

### Getting common peaks between replicates
Ok you can get common peaks between replicates in different combinations using the plotVenn function in diffbind. This function will return a list which will have different dataframes like onlyA, notinA,inAll. You can use these combinations along with rbind(after subsetting to first 3 columns Chr,Start,End) to get a bed file for a required intersection

```R
# Get overlap between all members of Condition1
df <- dba.plotVenn(diff.dba, diff.dba$masks$Condition1, DataType = DBA_DATA_FRAME)

# Get merged df for something like called in atleast 2 of 3 replicates
df.merged <- rbind(df$notA[,c(1,2,3)], df$notB[,c(1,2,3)], df$notC[,c(1,2,3)], df$inAll[,c(1,2,3)])

# Save file
write.table(df.merged, file = "Cond1_atleast_2_replicates.xls", sep = "\t", quote = FALSE, row.names = FALSE)
```

### Details on how the correlation is calculated

>First, each peak set is read in separately. The scores are normalized to a 0-1 scale as follows `scores <- scores/max(scores) (if LowerBetter was specified, this is followed by scores <- 1-scores.)` Second, all the peaksets are merged. Any overlapping peak regions are extended to encompass the contiguous peaks, so peaks are consider to overlap if at least one base position overlaps. Third, each interval in the merged peakset is assigned a score for each sample. If a sample had one peak called that overlaps the merged interval, it receives the (normalized) score for that peak. If a sample has more than one peak called that overlaps a merged interval, it is assigned the maximum value of the overlapping peak scores for that sample. If a sample has no peaks that overlap a merged interval, it is assigned a score of -1. At this point, there is a binding matrix with rows corresponding to the merged intervals, and columns corresponding to each sample. Each column then is a vector representing the peak scores for that sample (with -1 scores for all the regions that were not identified as peaks for that sample). To make the correlation heatmap (by calling dba.plotHeatmap() or just plot(), which maps to the same thing),  the log2() values of the scores are obtained, then a correlation value is computed for each pair of score vectors. This is a **pearson** correlation by default, although it is changeable using the distMethod parameter to dba.plotHeatmap(). The whole matrix of correlations is returned silently by dba.plotHeatmap(), so if you assign this to a value, you can see the correlation values. [Source](https://support.bioconductor.org/p/63034/#63036)

> The correlation heatmaps are generated using the correlations between the binding patterns for each sample. After the peaks are initially loaded, using dba(), the peaks are merged and the scores (normalized to 0..1) are retained. If a peak was not called for a sample, it gets a score of -1. So each sample has a vector of scores for each peak, which may contain -1 scores for peaks not associated with that sample.After a call to dba.count(), the reads are counted in every sample for every peak, and a score computed. The default score is a normalized read count (after subtracting control counts). So each sample has a vector of scores for each consensus peak. Generally there are at least some counts for each peak, so the scores are more uniform. I find that if there is a big difference in clustering between the peak-based and read-based correlation heatmaps, this may be due to the noisy nature of how peaks are called or left out for individual samples. The count-based scores generally exhibit higher correlations. After a call to dba.analyze(), a correlation heatmap is plotted using only differentially bound peaks. As these peaks differentiate between two conditions, one would expect to see the samples clustering into those two conditions (although this will not necessarily be the case). [Source](https://support.bioconductor.org/p/66901/#66917)

So here is the procedure i think is followed:-

1. You load you peakset. Lets assume this if from MACS. Macs will assign a p-value to each peak. This p-value is going to be considered as the score after being normalized to a scale of 0-1 by dividing the scores in each peakset by the maximum score. If a peak is not called for a sample it is assigned a score of -1. 
2. This creates a matrix with samples in the columns and merged peaks in the rows. This matrix is used to calculated a pairwise peason correlation and that is what is plotted in the heatmap.


