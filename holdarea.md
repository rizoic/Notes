# HOLDAREA

1. A tool which can integrate Chip and RNA seq with individual rankings from both is required. The question is how do you rank the genes for chip analysis. There seem to be two metrics which can come up. A distance based metric which gives weights to genes based on their distance from peaks or a score based one which weigh's peaks by their score or fold change. But we have fold change is macs2 too, why no use that for ranking the peaks and every gene maybe gets a value based on its log2fc and distance from closest peak to it. Maybe something like this

2. There is a need for an histone cheatsheet. Some of them exist but more are required

3. How is single cell analysis different from the cell line or tissue analysis we do normally?

4. A good set of [resource](http://www.csun.edu/~cmalone/pdf562/) for understanding epigenetic parts

5. [ChromHMM](http://compbio.mit.edu/ChromHMM/) - ChromHMM is software for learning and characterizing chromatin states. ChromHMM can integrate multiple chromatin datasets such as ChIP-seq data of various histone modifications to discover de-novo the major re-occurring combinatorial and spatial patterns of marks. ChromHMM is based on a multivariate Hidden Markov Model that explicitly models the presence or absence of each chromatin mark. The resulting model can then be used to systematically annotate a genome in one or more cell types. By automatically computing state enrichments for large-scale functional and annotation datasets ChromHMM facilitates the biological characterization of each state. ChromHMM also produces files with genome-wide maps of chromatin state annotations that can be directly visualized in a genome browser. It is actively maintained.

6. [Segway](https://segway.hoffmanlab.org/) - Another alternative to ChromHMM is Segway - The free Segway software package contains a novel method for analyzing multiple tracks of functional genomics data. Our method uses a dynamic Bayesian network (DBN) model, which enables it to analyze the entire genome at 1-bp resolution even in the face of heterogeneous patterns of missing data. This method is the first application of DBN techniques to genome-scale data and the first genomic segmentation method designed for use with the maximum resolution data available from ChIP-seq experiments without downsampling. Segway uses the Graphical Models Toolkit (GMTK) for efficient DBN inference. Our software has extensive documentation and was designed from the outset with external users in mind. It is python based and also actively maintained.

7. CTCF binding seems to be another important dataset that can be very helpful and needs to be looked into

8. There are another tools to make chromatin state maps - TreeHMM, hiHMM, diHMM.

9. t-SNE, MDS and SOM(Self organising maps) need to be seen in.

10. What is done as a part of footprinting analysis for ATAC Seq?

11. Profile plots from chip seq are also possibly known as metagene plots. There exists an [R package](https://bioconductor.org/packages/devel/bioc/vignettes/metagene/inst/doc/metagene.html) which can draw these for you

12. [DREAMSeq](http://tanglab.hebtu.edu.cn/tanglab/Home/DREAMSeq) - A differential relative expression analysis method for RNA-seq data mining. A new method for RNA seq DEG analysis seems interesting

13. BETA a tool to do integrative analysis of chip and RNA seq has a forum which can be accessed at [here](https://groups.google.com/forum/#!topic/cistromebeta/ZVPt2tUgYpg)

14. Single ends usually have lower mapping rates because we don't have the other pair to help in the alignment

15. Teaser is a really handy tool and should be used more frequently

16. BWA aln for smaller reads and BWA mem for longer ones seem fine. Many pipelines are using that now. I think we will need a teaser face off for this

17. [Vroom](https://github.com/jimhester/vroom) seems like a very promising delimited reader for R. It will lazily read in indexed files.

18. A good introduction to [probability](https://seeing-theory.brown.edu/index.html#secondPage)

19. [PEPATAC](https://github.com/databio/pepatac) - A modular, containerized pipeline for ATAC-seq data processing. Used in the TCGA paper for ATAC seq

20. [iGenomes](https://support.illumina.com/sequencing/sequencing_software/igenome.html) - Standard ref genomes from illumina

21. [refgenie](https://github.com/databio/refgenie) - Refgenie creates a standardized folder structure for reference genome files and indexes. You can download pre-built genomes or use the script to build your own for any genome you like. 

22. [elmer](http://bioconductor.org/packages/release/bioc/html/ELMER.html) - ELMER is designed to use DNA methylation and gene expression from a large number of samples to infer regulatory element landscape and transcription factor network in primary tissue.

23. Overhang in star is the number of based after a denovo or annotated junction. The higher the overhang the more is your accuracy however you may also sacrifice a bit on sensitivity.

24. Using [GeneID](https://cdn.technologynetworks.com/TN/Resources/PDF/0367.pdf) for U12 prediction

25. SpliceRack is a good resource to download PSSM's for U12 prediction

26. [FLUXSimulator](http://confluence.sammeth.net/display/SIM/Home) is used in a lot of experiments for simulating RNA Seq data. Seems faily feature rich.

27. We need a python/C based tool to detect U12/U2 from GTF and fa file.

28. SGSeq also seems to be good tool to for alternative splicing quantification

29. rMATS requirement for end to end does not make so much sense to me so i am going to skip it[Source](https://groups.google.com/forum/#!searchin/rna-star/alternative$20splicing%7Csort:date/rna-star/1G01jkjlLPI/IUZam_-ZAAAJ)

30. STAR manual recommends gencode annotations for human and mouse

31. You can also give a custom annotated junctions list to STAR in the format Chr\tab Start\tab End\tab Strand=+/-/.

32. You can also insert some custom junctions on the fly that is additional to your custom junctions. 

33. ENCODE options and TCGA options used for STAR are kinda similar.

34. STAR output logs

Log.out: main log file with a lot of detailed information about the run. This file is most useful
for troubleshooting and debugging.
Log.progress.out: reports job progress statistics, such as the number of processed reads, %
of mapped reads etc. It is updated in 1 minute intervals.
Log.final.out: summary mapping statistics after mapping job is complete, very useful for
quality control. The statistics are calculated for each read (single- or paired-end) and then
summed or averaged over all reads. Note that STAR counts a paired-end read as one read,
(unlike the samtools flagstat/idxstats, which count each mate separately). Most of the information 
is collected about the UNIQUE mappers (unlike samtools flagstat/idxstats which does not
separate unique or multi-mappers). Each splicing is counted in the numbers of splices, which
would correspond to summing the counts in SJ.out.tab. The mismatch/indel error rates are
calculated on a per base basis, i.e. as total number of mismatches/indels in all unique mappers
divided by the total number of mapped bases.

35. STAR can by itself detect chimeric(fusion) alignments. And gives you a lot of parameters to control this

36. [STAR-Fusion](https://github.com/STAR-Fusion/STAR-Fusion/wiki) can be used to detect fusion in RNA seq reads.

37. This is an important file [SAM Tags](https://samtools.github.io/hts-specs/SAMtags.pdf) gives details on all the SAM tags and also their format. Predefined standard tags are listed in the following table and described in greater detail in later subsections.Optional fields are usually displayed as **TAG:TYPE:VALUE** ; the type may be one of A (character), B (general array), f (real number), H (hexadecimal array), i (integer), or Z (string).

38. [TFCheckpoint](http://www.tfcheckpoint.org/) is a good resource for TF related searches. They have compiled data from multiple sources and can be used for filtering purposes

39. How to access grchr37 ensemble in biomart `grch37 = useMart(biomart="ENSEMBL_MART_ENSEMBL", host="grch37.ensembl.org", path="/biomart/martservice", dataset="hsapiens_gene_ensembl")`

40. Ok this one is on U12DB. You would think that one would do a simple thing while making a DB for U12 predictions that take the splice junctions and do denovo prediction on them and move on. But for U12DB the methodology used is very different. They took all the human U12 predictions and then for each predicted intron they took 100 bases of flanking sequence and then looked for that flanking sequence in the gene sequences of all its orthologs. If they found a gapped match with the gap coming at around 100 bases then they took it as an intron and put into the U2/U12 pipeline.

41. For quick scripting - gnu parallel > bash > perl > python. Other options are sed, awk, csv specific tools.

42. To unmount a dir mounted by sshfs use fusermount -u <dirpath> [Source](https://stackoverflow.com/a/22921004)

43. How to create multiple subdirs in bash `mkdir -p /results/test/{dir1,dir2,dir3}`

44. [intervene](https://intervene.readthedocs.io/en/latest/introduction.html) seems like an interesting project for quick verification of venn diagrams.

45. [FastaReferenceMaker](https://software.broadinstitute.org/gatk/documentation/tooldocs/3.8-0/org_broadinstitute_gatk_tools_walkers_fasta_FastaAlternateReferenceMaker.php) seems like a cool tool that will substitute the snps in a vcf file into your reference and give you and alternate reference

46. Don't run off to tools and frameworks. A lot of problems can be solved on the command line with things like sed, awk, perl one liners, csv toolkits, grep, cut. Cross of these tools first and only then go on to bigger tool sets and frameworks. Also in bioinformatics remember samtools is very powerful it has a bam viewer and a lot of things in general you can do with bam files.

47. Ensemble genome browser is also very very powerful man. It also links the regions to UCSC browser if required. We should keep it at the back of our head about it.

48. [Tarbase](http://carolina.imis.athena-innovation.gr/diana_tools/web/index.php?r=tarbasev8%2Findex) is a database of miRNA targets. You can put a gene name in there and get the list of mirna's that would target this gene. It is also available as a track on ensemble to see it visually.

49. [miRBase](http://www.mirbase.org/) is a good database of microRNA's.

50. When you download the genome from UCSC you may see some of the nucleotides as upper case while some as lower case. The lower case ones are repeats as per repeatmasker while the upper case ones are non repeats. [Source](https://biology.stackexchange.com/a/45304)


