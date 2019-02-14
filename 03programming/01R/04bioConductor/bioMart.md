# BIOMART

## Access hg19/grch37

You can access data for hg19 using the biomart module by initializing your mart as follows

```R
grch37 = useMart(biomart="ENSEMBL_MART_ENSEMBL", host="grch37.ensembl.org", path="/biomart/martservice", dataset="hsapiens_gene_ensembl")
```

[Source](https://support.bioconductor.org/p/62347/)