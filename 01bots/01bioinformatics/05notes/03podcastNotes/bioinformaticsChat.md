# [Bioinformatics Chat](https://bioinformatics.chat)

## #2 Single-cell RNA sequencing with Aleksandra Kolodziejczyk

- So single cell RNA sequencing is motivated by studies which want to look into differences between individual cells. Like the embryo from single stage and its progression to more differentiated cells. Same is the case with blood and its lineage.
- So you using multiple possible techniques isolate the different cell types and and then sequence them. Due to presence of adapters you can then assign each read to its original sample.
- Also one thing to remember is since you are sequencing a lot of samples you will not get each at that high quality as individual RNA seq data. You will mostly get data for highly expressed genes and not so much for the low ones.
- You don't remove DNA as there are only two copies of it in the cell and it is not going to so much interfere with the analysis. Though you do remove the ribosomal RNA and do enrichment for the poly-A tail.
- The main application post that is clustering. You will take the most highly expressed genes and then do a PCA based on it. 
- There are multiple application like [Monocle](http://cole-trapnell-lab.github.io/monocle-release/)\(one of the first ones\) which can construct a trajectory and this can be helpful in determining how and which genes change over time.
- Publications to read
  - 