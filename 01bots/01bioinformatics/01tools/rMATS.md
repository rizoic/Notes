# rMATS

rMATS is a tool to detect alternative splicing events from RNA-seq data. Its statistical model calculates a p-value and FDR that the difference in isoform ratio of a gene between two conditions exceeds a given user defined threshold. It can be used to detect all major types of splicing i.e. Skipped exon, Alternative 5' splice site, Alternative 3' splice site, Mututally exclusive exons, Retained intron. It can handle replicate data.

## Key Notes.

1. The statistical model for rMATS can be downloaded seprately from [Github](https://github.com/Xinglab/rMATS-STAT/)
2. You can convert the output of rMATS to a sashimi plot using the tool [rmats2sashimiplot](https://github.com/Xinglab/rmats2sashimiplot/)


