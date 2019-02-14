# NOTES ABOUT SETTING UP A REF GENOME


1. The parts besides the chr1-23/XYM(Human) as called scaffolds.
2. It seems the last patch for the hg19 human genome was released on June 28,2013[Source](https://www.ncbi.nlm.nih.gov/grc/human)
3. Its better to stick with Ensemble as with their biomart you an quickly do cross referencing for a wide variety of things.
4. What are the sequences in a reference genome
This file contains the following sequence information:

    chromosomes 1-22, X, Y
    sequences that can be asigned to one chromosome, but not to an exact position or orientation (unlocalized sequences)
    sequences that cannot be assigned to any chromosome (unplaced sequences)

These make up the primary assembly
Besides this there are
the mitochondrial genome
sequences that provides an alternate representation of a locus (alernate locus)[Source](https://www.biostars.org/p/342482/)

5.It is strongly recommended to include major chromosomes (e.g., for human chr1-22,chrX,chrY,chrM,)
as well as un-placed and un-localized scaffolds. Typically, un-placed/un-localized scaffolds add just a
few MegaBases to the genome length, however, a substantial number of reads may map to ribosomal
RNA (rRNA) repeats on these scaffolds. These reads would be reported as unmapped if the scaffolds
are not included in the genome, or, even worse, may be aligned to wrong loci on the chromosomes.
Generally, patches and alternative haplotypes should not be included in the genome.
Examples of acceptable genome sequence files:
• ENSEMBL: files marked with .dna.primary.assembly, such as: ftp://ftp.ensembl.
org/pub/release-77/fasta/homo_sapiens/dna/Homo_sapiens.GRCh38.dna.primary_
assembly.fa.gz
• NCBI: ”no alternative - analysis set”:
ftp://ftp.ncbi.nlm.nih.gov/genbank/
genomes/Eukaryotes/vertebrates_mammals/Homo_sapiens/GRCh38/seqs_for_alignment_
pipelines/GCA_000001405.15_GRCh38_no_alt_analysis_set.fna.gz [Source](https://github.com/alexdobin/STAR/blob/master/doc/STARmanual.pdf)