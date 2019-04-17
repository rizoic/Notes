# SEQKIT

Seqkit is a very handy tool to do operations on FASTQ files. You can find more info [here](https://github.com/shenwei356/seqkit)

## Get basic stats on fastq files

You can use the `stats` tool in seqkit to ge some quick stats on fastq file. Of coutse there is always FASTQC but stats has a utility in doing a quick check. You can run it as follows

```bash
> seqkit stats input.fastq

# You should get output like this
file                                        format  type  num_seqs  sum_len  min_len  avg_len  max_len
input.fastq                                 FASTQ   DNA      1,251  125,100      100      100      100
```

You can find more information of options for stats [here](https://bioinf.shenwei.me/seqkit/usage/#stats)
