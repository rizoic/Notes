# HOLD AREA

Misc notes which may/may not get converted to full ones

## Get Data

Often when you want to get some bioinformatics mapping data i.e. genes for an organism, gtf files there are bascially 3 places you should think of first

- [Biomart](http://ensembl.org/biomart) - This is the swiss army knife. It can help you in mapping things. If you want something like the mouse gene names mapped to something like PDB ID for example this will do that for you. The web interface is a good starting point to get a feel for what you can do. When you are familar with it you can use the equally powerfull bioconductor module [BioMArt](https://bioconductor.org/packages/release/bioc/html/biomaRt.html) to fetch things in an automated fashion

- [UCSC Table Browser](https://genome.ucsc.edu/cgi-bin/hgTables) - This is another powerful tool to fetch data and perform operations on it on the server itself. I am currently unaware of a autoamted way of doing it. 

- [Gencode Genes](https://www.gencodegenes.org/) - You can go here to fetch the reference genomes for humaan/mouse and the transcript seqeunces. If you use gencode it becomes very easy to update with new versions. The gencode transcripts are the same as encode except for some differences the details of which can be found [here](https://www.gencodegenes.org/faq.html)

## Refseq Accession Numbers

The key to refseq accession numbers :-

| Accession prefix | Molecule type | Comment                                                                 |
|------------------|---------------|-------------------------------------------------------------------------|
| AC_              | Genomic       | Complete genomic molecule, usually alternate assembly                   |
| NC_              | Genomic       | Complete genomic molecule, usually reference assembly                   |
| NG_              | Genomic       | Incomplete genomic region                                               |
| NT_              | Genomic       | Contig or scaffold, clone-based or WGSa                                 |
| NW_              | Genomic       | Contig or scaffold, primarily WGSa                                      |
| NZ_b             | Genomic       | Complete genomes and unfinished WGS data                                |
| NM_              | mRNA          | Protein-coding transcripts (usually curated)                            |
| NR_              | RNA           | Non-protein-coding transcripts                                          |
| XM_c             | mRNA          | Predicted model protein-coding transcript                               |
| XR_c             | RNA           | Predicted model non-protein-coding transcript                           |
| AP_              | Protein       | Annotated on AC_ alternate assembly                                     |
| NP_              | Protein       | Associated with an NM_ or NC_ accession                                 |
| YP_c             | Protein       | Annotated on genomic molecules without an instantiatedtranscript record |
| XP_c             | Protein       | Predicted model, associated with an XM_ accession                       |
| WP_              | Protein       | Non-redundant across multiple strains and species                       |


[Source](https://www.ncbi.nlm.nih.gov/books/NBK21091/table/ch18.T.refseq_accession_numbers_and_mole/?report=objectonly)

## Guide to gene naming

These are a couple of guides which can tell the rules behind the naming of genes

- [HGNC](https://www.genenames.org/about/guidelines)
- [MGI](http://www.informatics.jax.org/nomen/gene.shtml)

Will try to go through them later and find some interesting and relevant to day to day rules

## Get insert size and its sd for GEO

When uploading datasets to GEO one of the entries that is optionally required in the template is the insert file and its SD. You can easily get this by using the [CollectInsertSizeMetrics](https://software.broadinstitute.org/gatk/documentation/tooldocs/4.0.1.2/picard_analysis_CollectInsertSizeMetrics.php) utility that comes as a part of Picard. This should give you both the required metrics [Source](https://translate.googleusercontent.com/translate_c?depth=1&hl=en&prev=search&rurl=translate.google.com&sl=zh-CN&sp=nmt4&u=http://t43983006.lofter.com/post/1d0b3057_c4734ba&xid=17259,15700022,15700124,15700149,15700186,15700191,15700201&usg=ALkJrhg2252KYIttBsJ1c_hgcu24x7VqxQ).

## Handling GTF files in R

A few interesting ways of doing this are - 

1. [GTF](https://github.com/jokergoo/GTF) - A simple class for reading in GTF files. Can be expanded further if required
2. []