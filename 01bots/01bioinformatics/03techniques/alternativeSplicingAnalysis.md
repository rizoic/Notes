# Alternative Splicing Analysis

## General

### Resources

1. [**awesome-alternative-splicing**](https://github.com/HussainAther/awesome-alternative-splicing) - A repo with links to some of the tools and databases useful for alternative splicing analysis

## Intron Retention

### Publications

#### [iREAD](https://www.biorxiv.org/content/biorxiv/early/2017/10/04/135624.full.pdf)

#### [IRFinder](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-017-1184-4)

#### [Whippet](https%3A%2F%2Flinkinghub.elsevier.com%2Fretrieve%2Fpii%2FS1097276518306786%3Fshowall%3Dtrue)

### Tools

#### [GeneStructure](https://bioconductor.org/packages/release/bioc/vignettes/GeneStructureTools/inst/doc/Vignette.html)

#### [Leafcutter](<https://davidaknowles.github.io/leafcutter/index.html>)

#### Other Resources

#### [InTEREST Thesis](https://helda.helsinki.fi/bitstream/handle/10138/256031/bioinfor.pdf?sequence=1&isAllowed=y)

### Biostars

#### [Getting list of Introns](https://www.biostars.org/p/325994/)

### STAR aligner params

Below is a list of all the params besides the default that may need to be customized for the STAR aligner to do efficient alignment for intron retention ananlysis

- IRFinder

  ```
  --outFilterMultimapNmax 1
  --outSAMstrandField intronMotif
  --outSAMmode NoQS
  --outSAMunmapped None
  ```

[Source](https://github.com/williamritchie/IRFinder/blob/6f8717cfe6f1a1e433e4114343856456a61900e5/bin/IRFinder)

- [idiffir](http://combi.cs.colostate.edu/idiffir/tutorial.html)

  iDiffIR accepts any sorted, indexed BAM file for single- or paired-end reads. It may be helpful to use an aligner that provides an “NH” tag (such as STAR or TopHat) to identify unique alignments

- –outSAMstrandField intronMotif, –outFilterIntronMotifs RemoveNoncanonicalUnannotated, –outReadsUnmapped None, –alignMatesGapMax 200000, and alignIntronMax 5000000[Source](<https://advances.sciencemag.org/content/3/6/e1700731.full>)

- rMATS

  ```bash
  STAR --chimSegmentMin 2 --outFilterMismatchNmax 3 --alignEndsType EndToEnd --runThreadN 4 --outSAMstrandField intronMotif --outSAMtype BAM SortedByCoordinate
  --alignSJDBoverhangMin 6 --alignIntronMax 299999
  ```

- Mine

  ```bash
  --outSAMstrandField intronMotif
  --outFilterMultimapNmax 4
  --alignIntronMax 299999
  --scoreGapATAC -4
  --alignSJDBoverhangMin 6 # Leafcutter makes a case for this
  ```

  

### Handy methods section

1. [Targeted Intron Retention and Excision for Rapid Gene Regulation in Response to Neuronal Activity](https://www.sciencedirect.com/science/article/pii/S089662731630900X)
2. [Differential intron retention in *Jumonji* chromatin modifier genes is implicated in reptile temperature-dependent sex determination](<https://advances.sciencemag.org/content/3/6/e1700731.full>)
3. [Intron retention is regulated by altered MeCP2-mediated splicing factor recruitment](<https://www,nature.com/articles/ncomms15134>)