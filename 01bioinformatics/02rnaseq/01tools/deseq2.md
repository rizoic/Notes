# DESEQ2

DESeq2 is a bioconductor package for differential gene expression analysis. [More Info](https://bioconductor.org/packages/release/bioc/html/DESeq2.html)

## Handling Batch Effects in DESeq2

Having samples belonging to different batches in you experiment can have a confounding effect and needs to be handled. The recommended way to handle for different batches is to add them to the design formula like shown below

```R
dds <- DESeqDataSetFromMatrix(countData = cts,
                              colData = coldata,
                              design= ~ batch + condition)
```

[Source](https://bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html)

## Understanding DESeq2 calculations

A rough understanding of what DESeq2 does could be as follows:-

1. It will first try an have an estimate of dispersion for each gene. Dispersion studies the within group variability for each gene. Once it gets dispersion estimates for each gene it will try and adjust these estimates so that they come closer to a smooth curve fitted on these dispersion estimates. A simplistic way of thinking about dispersion would be the something like [standard deviation/mean](https://support.bioconductor.org/p/75260/#75261). Dispersion is the reason we are using Negative Binomial Models which account for dispersion besides the mean. The higher the dispersion for a gene the more the chances on it getting shrunk when doing logfoldshrinking in DESeq2.
2. There is an optional logfold shrinking that can be done. Which will apply shrinkage to the log2folds depending on the counts, dispersion and degrees of freedom.