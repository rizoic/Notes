# Gencode

## Questions

1. What is this basic set of transcripts from gencode?

   The transcripts tagged as "basic" form part of a subset of representative transcripts for each gene. This subset **prioritises full-length protein coding transcripts over partial or non-protein coding transcripts** within the same gene, and intends to highlight those transcripts that will be useful to the majority of users.
   
   More help on this from the [ENSEMBLE website](https://asia.ensembl.org/info/genome/genebuild/transcript_quality_tags.html#basic)GENCODE Basic
   
   The GENCODE gene set is the gene set Ensembl displays for human and  mouse. GENCODE Basic is a subset of the GENCODE gene set, and is  intended to provide a simplified, high-quality subset of the GENCODE  transcript annotations that will be useful to the majority. This subset  prioritises full-length protein coding transcripts over partial or  non-protein coding transcripts within the same gene.
   
   GENCODE Basic includes all genes in the GENCODE gene set, with a  representative subset of the transcripts (splice variants). The GENCODE  Basic set is available for the human and mouse gene sets from Ensembl  release 75.
   
   ### Rules for GENCODE Basic
   
   We worked with GENCODE to decide how to tag transcripts as 'Basic'.  These are the rules that we use to tag which transcripts are included in  the GENCODE Basic set, for each gene:
   
   1. Loop through all protein-coding (and similar biotype) transcripts  and tag all the complete (CDS start- and end found) transcripts. If none  of the transcripts are complete, tag only the transcript(s) with the  longest CDS.
   2. Loop through all the small noncoding and antisense transcripts and  tag all the complete (mRNA start- and end found) transcripts. If none  are complete, loop through the long-noncoding transcripts too and then  tag only the transcript(s) with the longest combined exon length.
   3. Combine the results from steps (1) and (2) and this is what is displayed as ‘GENCODE Basic’.
   4. If, after step (3), we've got an empty basket and no transcripts in  the gene are tagged as 'Basic', we look for pseudogene transcripts and  tag all the pseudogene transcripts that we find.
   5. Finally, we've still got no transcripts tagged from steps (1) or (2)  or (4), then we tag transcripts with 'problematic' biotypes ie.  retained*intron, TEC, ambiguous*ORF and disrupted_domain.



2. Gencode gets its non coding RNA annotations from - [Rfam](http://rfam.xfam.org/) and specially miRNA sequences from [mirBase](http://www.mirbase.org/). Then there are some non coding RNA pseudogenes which are predicted by the Ensemble pipeline.
3. In a gencode GTF file you will find besides gene/transcript/exon you will also see UTR, CDS, start,stop and selenocystine. The below given figure very clearly represents these elements

![img](assets/dna-rna-protein.jpg)

So UTR are present on both the sides. These are things which are part of the first and last exon and are present in the mRNA which has the poly A tail and thus also present in the RNA seq data that we get. These are for allowing ribosomal complexe to bind. Withing the exon1 you will find somewhere a start codons from there the CDS starts and it will continue till the last exon within which you will find a stop codon somewhere as you can see in the figure above. Then post the 3’UTR you have the poly A tail. `Selenocysine` is just an annotation for places where there is the 21st amino acid in case ever required.p