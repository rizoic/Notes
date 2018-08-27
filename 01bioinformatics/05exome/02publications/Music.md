# MuSiC: identifying mutational significance in cancer genomes

## Notes

1. Key goal of music is to separate the driver mutations from the passenger ones.

2. It has six individual modules and a seventh module with runs all the other six.

3. Lets see each of these individual modules
    - **SMG**:  Significantly mutated genes. These are genes which show a significantly higher mutations rate when compared to background mutation rate(BMR). BMR in music can be calculated across all samples, a group of samples or per sample. Then comparisons are done across all the BMR's and a single p-value summarizing all considerations is generated for each gene. The p-values are summarized using 3 methods
        - Convolution Test(CT)
        - Fisher's Combined p-value test(FCPT)
        - Likelihood ratio test(LRT)
    The description as per the tool is

    ```text
    This script runs R-based statistical tools to identify Significantly Mutated Genes (SMGs), when
    given per-gene mutation rates categorized by mutation type, and the overall background mutation
    rates (BMRs) for each of those categories (gene_mr_file, created using "music bmr calc-bmr").

    P-values and false discovery rates (FDRs) for each gene in gene_mr_file is calculated using
    three tests: Fisher's Combined P-value test (FCPT), Likelihood Ratio test (LRT), and the
    Convolution test (CT). For a gene, if its FDR for at least 2 of these tests is <= max_fdr, it
    will be output as an SMG. Another output file with prefix "_detailed" will have p-values and
    FDRs for all genes.
    ```

    - **PathScan** - Pathscan is important for two factors which other methods neglect
        - Variations in gene lengths and the consequent differences of their mutational likelihoods under the null hypothesis
        - Distribution of mutations among samples and their proper combination into an overall p-value
    