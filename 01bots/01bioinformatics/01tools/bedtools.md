# Bedtools

## Tips

1. **Filter a BAM file against a blacklist** 

   You can filter a bam file to remove any reads overlapping r-RNA genes. This can be done with the following command

   ```bash
   bedtools intersect -abam reads.bam -b sample.bed -v > reads.nosample.bam
   ```

   [Source](https://www.biostars.org/p/121494/#121499)

2. One thing to remember for bedtools `intersect` is that by default if you dont specify `-u` or `-v` it will give multiple times the same peak for each overlap encountered. It is given clearly in the documentatation but you may miss it and sometimes when the total peak count is important this may lead to erronous counts

`