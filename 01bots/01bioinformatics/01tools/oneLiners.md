# Bioinformatics Oneliners

1. Move multiple .fq.gz files in a directory to their individual directories

```bash
find . -name "*.fq.gz"|parallel --dry-run --rpl "{sampName} s/.*?\/(.*).fq.gz/\1/" "mkdir -p {sampName} && mv {} ./{sampName}/"
```

