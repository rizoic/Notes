## Diffbind Notes

This is a bioconductor package which can be used to find differentially bound sites for Chip Seq experiments. More details on [Bioconductor](https://bioconductor.org/packages/release/bioc/html/DiffBind.html)

#### Diffbind Output Format
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

#### Details on bCounts

`The normalized counts returned by dba.report()are the raw reads divided by the normalization factors, obtained by calling DESeq2::sizeFactors().`[Source](https://support.bioconductor.org/p/68134/#68168)

`OK, I've looked into this a bit more deeply. For the default case when using DESeq2, where bFullLibrarySize=TRUE, DiffBind sets the factors to be the full library sizes (the number of reads in the .bam files) normalized to the smallest library (dividing by the minimum library size). So the smallest library size gets a normalization factor equal to 1, while the others are greater than one. This simple normalization method is only used when bFullLibrarySize=TRUE and method=DBA_DESEQ2.  If you set bFullLibrarySize=FALSE, using only the number of reads that overlap consensus peaks, then estimateSizeFactors() is called and the standard mean ratio method is used to calculate the normalization factors, none of which should be equal to 1. `[Source](https://support.bioconductor.org/p/85046/#85060)

`Yes, if there isn't a big imbalance in the signal between sample groups, bFullLibrarySize=FALSE is preferred. This used to be the default, but we changed it to be more conservative as the consequences are worse that way if the assumptions are not met.`[Source](https://support.bioconductor.org/p/85046/#85069)

`The bFullLibrarySize option determines the total read count used for normalization. If bFullLibrarySize=FALSE, the number of reads that overlap consensus peaks is used for each sample (basically, the sum of all the counts). This is the best option for cases where most of the peaks are not expected to change their binding affinity significantly. For the more conservative default, bFullLibrarySize=TRUE, the total number of aligned reads in the .bam file is used (basically the sequencing depth). This is more appropriate in cases where you expect dramatic shifts in binding affinities, or if you are not sure what to expect. `[Source](https://support.bioconductor.org/p/79469/#79473)

So in summary it depends on if you used bFullLibrarySize=FALSE/TRUE. If you set that to be `true` then the full library sizes will be used for normalization and you will find one of sample to have integer counts indicating that sample had the least number of reads and it had a normalizaion denominatior of 1, If you set it to `false` then it will get the normalization factors per peak.


