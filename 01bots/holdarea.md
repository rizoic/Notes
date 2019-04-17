# HOLDAREA



1. A good set of [resource](http://www.csun.edu/~cmalone/pdf562/) for understanding epigenetic parts

   

2. CTCF binding seems to be another important dataset that can be very helpful and needs to be looked into

3. t-SNE, MDS and SOM(Self organising maps) need to be seen in.

4. [DREAMSeq](http://tanglab.hebtu.edu.cn/tanglab/Home/DREAMSeq) - A differential relative expression analysis method for RNA-seq data mining. A new method for RNA seq DEG analysis seems interesting

5. BETA a tool to do integrative analysis of chip and RNA seq has a forum which can be accessed at [here](https://groups.google.com/forum/#!topic/cistromebeta/ZVPt2tUgYpg)

6. BWA aln for smaller reads and BWA mem for longer ones seem fine. Many pipelines are using that now. I think we will need a teaser face off for this

7. A good introduction to [probability](https://seeing-theory.brown.edu/index.html#secondPage)


1. [PEPATAC](https://github.com/databio/pepatac) - A modular, containerized pipeline for ATAC-seq data processing. Used in the TCGA paper for ATAC seq

2. [iGenomes](https://support.illumina.com/sequencing/sequencing_software/igenome.html) - Standard ref genomes from illumina

3. [refgenie](https://github.com/databio/refgenie) - Refgenie creates a standardized folder structure for reference genome files and indexes. You can download pre-built genomes or use the script to build your own for any genome you like. 

4. [elmer](http://bioconductor.org/packages/release/bioc/html/ELMER.html) - ELMER is designed to use DNA methylation and gene expression from a large number of samples to infer regulatory element landscape and transcription factor network in primary tissue.

5. Overhang in star is the number of based after a denovo or annotated junction. The higher the overhang the more is your accuracy however you may also sacrifice a bit on sensitivity.

6. Using [GeneID](https://cdn.technologynetworks.com/TN/Resources/PDF/0367.pdf) for U12 prediction

7. [FLUXSimulator](http://confluence.sammeth.net/display/SIM/Home) is used in a lot of experiments for simulating RNA Seq data. Seems faily feature rich.

8. We need a python/C based tool to detect U12/U2 from GTF and fa file.

9. rMATS requirement for end to end does not make so much sense to me so i am going to skip it[Source](https://groups.google.com/forum/#!searchin/rna-star/alternative$20splicing%7Csort:date/rna-star/1G01jkjlLPI/IUZam_-ZAAAJ)

10. STAR manual recommends gencode annotations for human and mouse

11. You can also give a custom annotated junctions list to STAR in the format Chr\tab Start\tab End\tab Strand=+/-/.

12. You can also insert some custom junctions on the fly that is additional to your custom junctions. 

13. ENCODE options and TCGA options used for STAR are kinda similar.

14. This is an important file [SAM Tags](https://samtools.github.io/hts-specs/SAMtags.pdf) gives details on all the SAM tags and also their format. Predefined standard tags are listed in the following table and described in greater detail in later subsections.Optional fields are usually displayed as **TAG:TYPE:VALUE** ; the type may be one of A (character), B (general array), f (real number), H (hexadecimal array), i (integer), or Z (string).

15. [TFCheckpoint](http://www.tfcheckpoint.org/) is a good resource for TF related searches. They have compiled data from multiple sources and can be used for filtering purposes

16. How to access grchr37 ensemble in biomart `grch37 = useMart(biomart="ENSEMBL_MART_ENSEMBL", host="grch37.ensembl.org", path="/biomart/martservice", dataset="hsapiens_gene_ensembl")`

17. Ok this one is on U12DB. You would think that one would do a simple thing while making a DB for U12 predictions that take the splice junctions and do denovo prediction on them and move on. But for U12DB the methodology used is very different. They took all the human U12 predictions and then for each predicted intron they took 100 bases of flanking sequence and then looked for that flanking sequence in the gene sequences of all its orthologs. If they found a gapped match with the gap coming at around 100 bases then they took it as an intron and put into the U2/U12 pipeline.

18. For quick scripting - gnu parallel > bash > perl > python. Other options are sed, awk, csv specific tools.

19. To unmount a dir mounted by sshfs use fusermount -u <dirpath> [Source](https://stackoverflow.com/a/22921004)

20. How to create multiple subdirs in bash `mkdir -p /results/test/{dir1,dir2,dir3}`

21. [intervene](https://intervene.readthedocs.io/en/latest/introduction.html) seems like an interesting project for quick verification of venn diagrams.

22. [FastaReferenceMaker](https://software.broadinstitute.org/gatk/documentation/tooldocs/3.8-0/org_broadinstitute_gatk_tools_walkers_fasta_FastaAlternateReferenceMaker.php) seems like a cool tool that will substitute the snps in a vcf file into your reference and give you and alternate reference

23. Don't run off to tools and frameworks. A lot of problems can be solved on the command line with things like sed, awk, perl one liners, csv toolkits, grep, cut. Cross of these tools first and only then go on to bigger tool sets and frameworks. Also in bioinformatics remember samtools is very powerful it has a bam viewer and a lot of things in general you can do with bam files.

24. Ensemble genome browser is also very very powerful man. It also links the regions to UCSC browser if required. We should keep it at the back of our head about it.

25. [Tarbase](http://carolina.imis.athena-innovation.gr/diana_tools/web/index.php?r=tarbasev8%2Findex) is a database of miRNA targets. You can put a gene name in there and get the list of mirna's that would target this gene. It is also available as a track on ensemble to see it visually.

26. [miRBase](http://www.mirbase.org/) is a good database of microRNA's.

27. When you download the genome from UCSC you may see some of the nucleotides as upper case while some as lower case. The lower case ones are repeats as per repeatmasker while the upper case ones are non repeats. [Source](https://biology.stackexchange.com/a/45304)

    
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