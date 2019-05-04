## Notes

1. Ribosome profiling, the recently developed high throughput sequencing technique, enabledthe mapping of translated regions genome-wide.
2. This technique takes advantage of the fact that ribosomes actively engaged in translation can protect their associated mRNA fragments against RNAse digestion. 
3. The basic idea of ribosome profiling is to perform deep-sequencing of the ribosome-protected mRNA fragment (~30 nts), termed ribosome footprints, to determine the occupancy of translating ribosomes on a given mRNA. 



## Workflow

- **Alignment**

  These reads are very very small but they may still be spliced so makes sense to use STAR for the alignment.

  Some changes required to the alignment params as per the author

  
```bash
--sjdbOverhang parameter should be set to the maximum (or 90% percentile) of the read length. 

To increase general mapping sensitivity for short reads, you can increase 
--winAnchorMultimapNmax from default 50 to 100 or 200, and reduce 
--seedSearchStartLmax from default 50 to 20 or 15
```
  [Source](https://github.com/alexdobin/STAR/issues/255)

The params as for alignment as per the [Ribocode](https://github.com/xryanglab/RiboCode) documentation

```bash
STAR --outFilterType BySJout --runThreadN 8 --outFilterMismatchNmax 2 --genomeDir <hg19_STARindex>
--readFilesIn <un_aligned.fastq>  --outFileNamePrefix <HEK293> --outSAMtype BAM
SortedByCoordinate --quantMode TranscriptomeSAM GeneCounts --outFilterMultimapNmax 1
--outFilterMatchNmin 16 --alignEndsType EndToEnd
```

Answer by the author in another [google forum post](https://groups.google.com/forum/#!topic/rna-star/1F86aCmPOYY)

```bash
25b reads will be much harder to map to the splice junctions, of course. Using annotations at the genome generation step would be very beneficial, with --sjdbOverhang chosen to be the longest read length -1.

At the mapping step, you can increase sensitivity with --seedSearchStartLmax 20, or even 15.

If you are using SJ.out.tab file, I would reduce --outSJfilterOverhangMin from 30 12 12 12 to, say, 30  8 8 8, to increase sensitivity for unannotated junctions.

You may want to be more restrictive for minimum allowed mapped length/score, by increasing:

--outFilterScoreMin               0
    int: alignment will be output only if its score is higher than this value
--outFilterScoreMinOverLread      0.66
        float: outFilterScoreMin normalized to read length (sum of mates lengths for paired-end reads)
--outFilterMatchNmin              0
    int: alignment will be output only if the number of matched bases is higher than this value
--outFilterMatchNminOverLread     0.66
    float: outFilterMatchNmin normalized to read length (sum of mates lengths for paired-end reads)

You can trim 3 adapters from within  STAR with

clip3pAdapterSeq            -
    string(s): adapter sequences to clip from 3p of each mate.  If one value is given, it will be assumed the same for both mates.
clip3pAdapterMMp            0.1
    double(s): max proportion of mismatches for 3p adpater clipping for each mate.  If one value is given, it will be assumed the same for both mates.
    
```

- Post alignment people will exclude reads aligning to ribosomal regions as per repeatmasker. [Source](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSM2837004). Some other ways of removing the reads could be aligning first to bowtie against rRNA regions and then proceeding with the unmapped reads. There also seem to be some special tools for this i.e [SortMeRNA](https://academic.oup.com/bioinformatics/article/28/24/3211/246053). [rRNAFilter](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5372776/) though these seem to be more so tailored towards metagenomic sequencing.

- Additional comments on the edited params

  ```bash
  --winAnchorMultimapNmax is used to select anchor seeds - only seeds (exactly mapping portions of the read) that map to <= number of loci are considered anchors. Anchors define the genomic windows where a read mapping is attempted. For example, if you want to map read that map equally well to 100 loci, you would need to set --winAnchorMultimapNmax at least 100, though I would recommend double that number.
  ```

  [Source](https://github.com/alexdobin/STAR/issues/243#issuecomment-393695283) [Source2](https://groups.google.com/d/msg/rna-star/cu4E0PIKnks/IoZF_9uvBgAJ)

  

## Tools

- [Ribocode](https://github.com/xryanglab/RiboCode)

  A tools to detect translated ORFs

- [MappingQC](https://github.com/Biobix/mQC)
  
  QC of the ribosome profiling mapping
  
- [RIboTISH](https://github.com/zhpn1024/ribotish)

  Find TIS sites in aligned data and compare them.

## Papers

- [Ribosome profiling reveals the what, when, where and how of protein synthesis](https://www.nature.com/articles/nrm4069)

  