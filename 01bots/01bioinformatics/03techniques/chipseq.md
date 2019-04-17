# ChIP-Seq

## databases

Ok so if you want to find if chip data exists for a partuclar cell type/cell line these are some of the resources you can use to look for it:-

1. **GEO Search**

You can substitute the name of the cell line/cell type in [this](https://www.ncbi.nlm.nih.gov/gds?term=sjsa1%5BAll%20Fields%5D%20AND%20%22Genome%20binding/occupancy%20profiling%20by%20high%20throughput%20sequen%22%5BFilter%5D&cmd=DetailsSearch) URL format and then search. This will filter the results for chip seq results only if any.

2. [**Cistrome Data Browser**](http://cistrome.org/db/#/)

This includes a data browser where you can filter by Species, Biological Sources and Factors. It applies a uniform analysis pipeline called ChiLin on all the samples.

3. You can also use the [ENA search](https://www.ebi.ac.uk/ena/data/warehouse/search) to search for a dataset.

4. Some of the other data bases which could be of interest are [Chip-Atlas](https://chip-atlas.org), [ChipBase](http://rna.sysu.edu.cn/chipbase) and [Remap](http://pedagogix-tagc.univ-mrs.fr/remap/)


## wetlab

1. What is input and what is igg and when which are used:- When doing chip seq you add formaldehyde to cross like the protien with dna. Then you sonicate the dna and pull down this cross linked protien with an antodby attached to a bead. This bead is pulled down magnetically. This pulldown by antibodies is called immunoprecipication. Now the problem with just using this IP sample is that there can be some background DNA also pulled down or you may have your antibody cross linking with some other protien(maybe even non nuclear and thus not binding to DNA). How do you control and not say that the protien binds against some background portion or some 

## tools

1. [ChromHMM](http://compbio.mit.edu/ChromHMM/) - ChromHMM is software for learning and characterizing chromatin states. ChromHMM can integrate multiple chromatin datasets such as ChIP-seq data of various histone modifications to discover de-novo the major re-occurring combinatorial and spatial patterns of marks. ChromHMM is based on a multivariate Hidden Markov Model that explicitly models the presence or absence of each chromatin mark. The resulting model can then be used to systematically annotate a genome in one or more cell types. By automatically computing state enrichments for large-scale functional and annotation datasets ChromHMM facilitates the biological characterization of each state. ChromHMM also produces files with genome-wide maps of chromatin state annotations that can be directly visualized in a genome browser. It is actively maintained.
2. [Segway](https://segway.hoffmanlab.org/) - Another alternative to ChromHMM is Segway - The free Segway software package contains a novel method for analyzing multiple tracks of functional genomics data. Our method uses a dynamic Bayesian network (DBN) model, which enables it to analyze the entire genome at 1-bp resolution even in the face of heterogeneous patterns of missing data. This method is the first application of DBN techniques to genome-scale data and the first genomic segmentation method designed for use with the maximum resolution data available from ChIP-seq experiments without downsampling. Segway uses the Graphical Models Toolkit (GMTK) for efficient DBN inference. Our software has extensive documentation and was designed from the outset with external users in mind. It is python based and also actively maintained.
3. Here are some more tools to make chromatin state maps - TreeHMM, hiHMM, diHMM.

## observations

1. Profile plots from chip seq are also possibly known as metagene plots. There exists an [R package](https://bioconductor.org/packages/devel/bioc/vignettes/metagene/inst/doc/metagene.html) which can draw these for you