# Bedtools

## Tips

1. **Filter a BAM file against a blacklist** 

   You can filter a bam file to remove any reads overlapping r-RNA genes. This can be done with the following command

   ```bash
   bedtools intersect -abam reads.bam -b sample.bed -v > reads.nosample.bam
   ```

   [Source](https://www.biostars.org/p/121494/#121499)