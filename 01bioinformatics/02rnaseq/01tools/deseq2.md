# DESEQ2

Deseq2 is a bioconductor package for differential gene expression analysis. [More Info](https://bioconductor.org/packages/release/bioc/html/DESeq2.html)

### Handling Batch Effects in DESeq2

Having samples belonging to different batches in you experiment can have a confounding effect and needs to be handled. The recommended way to handle for different batches is to add them to the design formula like shown below

```R
dds <- DESeqDataSetFromMatrix(countData = cts,
                              colData = coldata,
                              design= ~ batch + condition)
```
[Source](https://bioconductor.org/packages/release/bioc/vignettes/DESeq2/inst/doc/DESeq2.html)

