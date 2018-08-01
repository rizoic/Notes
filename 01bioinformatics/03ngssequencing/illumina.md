### Illumina Sequencing

Illunmina sequencing technology is one of the most used sequencng technology today.


#### Adapters
In order to be able to seqeuence any given DNA fragment illumina technology ataches adapters to your DNA fragments. The adapters for TruSeq consist primarily of two parts an Universal or P5 adapter and an Index or P7 adapter. The index adapter will have a 8 base unique fragment which is the barcode for your library. This enables sequencing of multilple samples in a single sequencing run.
The arrangement of these adapters can be seen in many images but the best representation I could find of this is
```
(flow cell)
||
||
||                                             (Index Adapter)                                               (Universal Adapter)
||    3'                                                                5'                          3'                                                        5'  
||    GTTCGTCTTCTGCCGTATGCTCTA-NNNNNN-CACTGACCTCAAGTCTGCACACGAGAAGGCTAGA                           TCTAGCCTTCTCGCAGCACATCCCTTTCTCACATCTAGAGCCACCAGCGGCATAGTAA
||                                                         ||||||||||||||                           ||||||||||||||                                                              <----- Must get denatured!
||        5'   AATGATCGGCGACCACCGAGATCTACACTCTTTCCCTACACGACGCTCTTCCGATCT--(5' MY DNA FRAGMENT 3')--AGATCGGAAGAGCACACGTCTGAACTCCAGTCAC‐NNNNNN‐ATCTCGTATGCCGTCTTCTGCTTG
||-------------TTACTAGCCGCTGGTGGCT                                     3'                           5'                                                                3'  
||    
||             ^(Flow cell oligo)              ^(Universal Adapter)                                            ^(Index Adapter)
||  
||                                     TGTGAGAAAGGGATGTGCTGCGAGAAGGCTAGA                           TCTAGCCTTCTCGTGTGCAGACTTGAGGTCAGTGTG
||    
||                                             ^(Read 1 Primer)                                                ^(Read 2 Primer)
||
||    
||                                                                                                                                           TAGAGCATACGGCAGAAGACGAAC----------||
||    
||                                                                                                                                               ^(Flow cell oligo)
||
[Copied from](https://biology.stackexchange.com/q/39853)
```
The left side represents the P5 end and the right side represents the P7 end

The short description is first A is added to the 3' end of the sequence then the index adapter with its phospohate group on the indexed adapter will attach to this A group and then the Universal adapter will also attach to the 5' end of the fragment

Then the dna is put on the flowcell and the start is with hthe p7 attached and having the complimentary sequence to the original sequence. So when sequecing will happen we will get the original sequence and the p7 origial sequence in read 1

For read 2 the p5 is attached and seqeuncing will start from p7. The seqeunce of the tempate is the orignal sequence. We will thus get the reverse complimentary of the original sequence and the sequence of the p5 adapter in read2.

So the key is you will see the index adapter till the barcode in the read1 and the reverse complementary of the universal adapter in read2. You can keep the read 2 adapter sequence of the entire length of the universal adapter or of the same length as the read1 adapter.

The actual seqeunce can be found as
```bash
cutadapt \
            -a AGATCGGAAGAGCACACGTCTGAACTCCAGTCAC \
            -A AGATCGGAAGAGCGTCGTGTAGGGAAAGAGTGTAGATCTCGGTGGTCGCCGTATCATT \
            -o trimmed.1.fastq.gz -p trimmed.2.fastq.gz \
            reads.1.fastq.gz reads.2.fastq.gz
```

[Source](http://cutadapt.readthedocs.io/en/stable/guide.html#illumina-truseq)

So read1 is always AGATCGGAAGAGCACACGTCTGAACTCCAGTCAC and read 2 can be AGATCGGAAGAGCGTCGTGTAGGGAAAGAGTGTA or can be longer at AGATCGGAAGAGCGTCGTGTAGGGAAAGAGTGTAGATCTCGGTGGTCGCCGTATCATT
