# Integrative Analysis

## Chip - RNA Seq

1. A tool which can integrate Chip and RNA seq with individual rankings from both is required. The question is how do you rank the genes for chip analysis. There seem to be two metrics which can come up. A distance based metric which gives weights to genes based on their distance from peaks or a score based one which weigh's peaks by their score or fold change. But we have fold change is macs2 too, why no use that for ranking the peaks and every gene maybe gets a value based on its log2fc and distance from closest peak to it. Maybe something like this

