# gffread

gffread in a handy utility which is a part of the cufflinks package. 

## Using GFFread to extract transcript seqeunces

Given a fasta file and a GTF file gffread can extract trancript sequences from the fasta file. This can come in handy when transcript sequenes are required for programs like kallisto/salmon amongst others. It also creates the transcript sequences taking the strand of the transcript into consideration. This then comes in handy for creating references in case of stranded RNA-seq experiments. An example common for this is:-

```bash
gffread -w output_transcripts.fa \
-g ref.fa \
annotation_file.gtf
```



