# STAR

1. ribosomal RNA's comprise of 90% of all the RNA and these are usually depleted during RNA seq by doing something like a Poly A selection. However if these are not sufficinetly depleted then you may say a high rate of multi mapping. This is because a large amout of rRNA are repeats/paralogs of each other[Source](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4631051/)

2. STAR output logs

- **Log.out**: main log file with a lot of detailed information about the run. This file is most useful
  for troubleshooting and debugging.
- **Log.progress.out**: reports job progress statistics, such as the number of processed reads, %
  of mapped reads etc. It is updated in 1 minute intervals.
- **Log.final.out**: summary mapping statistics after mapping job is complete, very useful for
  quality control. The statistics are calculated for each read (single- or paired-end) and then
  summed or averaged over all reads. Note that STAR counts a paired-end read as one read,
  (unlike the samtools flagstat/idxstats, which count each mate separately). Most of the information 
  is collected about the UNIQUE mappers (unlike samtools flagstat/idxstats which does not
  separate unique or multi-mappers). Each splicing is counted in the numbers of splices, which
  would correspond to summing the counts in SJ.out.tab. The mismatch/indel error rates are
  calculated on a per base basis, i.e. as total number of mismatches/indels in all unique mappers
  divided by the total number of mapped bases.

3. STAR can by itself detect chimeric(fusion) alignments. And gives you a lot of parameters to control this
4. [STAR-Fusion](https://github.com/STAR-Fusion/STAR-Fusion/wiki) can be used to detect fusion in RNA seq reads.