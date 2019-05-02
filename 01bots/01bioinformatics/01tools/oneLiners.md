# Bioinformatics Oneliners

1. Move multiple .fq.gz files in a directory to their individual directories

```bash
find . -name "*.fq.gz"|parallel --dry-run --rpl "{sampName} s/.*?\/(.*).fq.gz/\1/" "mkdir -p {sampName} && mv {} ./{sampName}/"
```

2. Find the count of peaks in a narrowpeak file and output them in a sorted way to an xls file

```bash
cat <(printf "Count\tSample\n") <(find -name "*.narrowPeak"|parallel "wc -l {}"|sort -n -r|sed "s/ \+/\t/g") > peak_count.xls
```

