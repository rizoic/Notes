# HOLD AREA

Misc notes which may/may not get converted to full ones

## Get Data

Often when you want to get some bioinformatics mapping data i.e. genes for an organism, gtf files there are bascially 3 places you should think of first

- [Biomart](http://ensembl.org/biomart) - This is the swiss army knife. It can help you in mapping things. If you want something like the mouse gene names mapped to something like PDB ID for example this will do that for you. The web interface is a good starting point to get a feel for what you can do. When you are familar with it you can use the equally powerfull bioconductor module [BioMArt](https://bioconductor.org/packages/release/bioc/html/biomaRt.html) to fetch things in an automated fashion

- [UCSC Table Browser](https://genome.ucsc.edu/cgi-bin/hgTables) - This is another powerful tool to fetch data and perform operations on it on the server itself. I am currently unaware of a autoamted way of doing it. 

- [Gencode Genes](https://www.gencodegenes.org/) - You can go here to fetch the reference genomes for humaan/mouse and the transcript seqeunces. If you use gencode it becomes very easy to update with new versions. The gencode transcripts are the same as encode except for some differences the details of which can be found [here](https://www.gencodegenes.org/faq.html)
