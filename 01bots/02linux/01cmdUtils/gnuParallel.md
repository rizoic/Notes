# GNU Parallel

GNU parallel is a command line utility to run shell commands in parallel. I also find it handly to generate shell commands on a variety of inputs. [More info](https://www.gnu.org/software/parallel/)

These notes are primarily from the [GNU parallel book](https://zenodo.org/record/1146014/files/GNU_Parallel_2018.pdf)

## Quick Start

### Input sources
GNU parallel can take input from STDIN(through pipes or manual entry) or then you can specify it manually

Manual Entry
```bash
parallel echo ::: 1 2 3 4 5
```

Piped through STDIN
```bash
# You can skip the {} in some cases but it is better to be explicit with your input
find example.* -print | parallel echo File {}
```

Multiple inputs can be given using :::
```bash
# It will generate all the possible combinations
parallel echo ::: S M L ::: Green Red
```

### Build the command line
So anything before the ::: is taken as the command. You can even have multiple commands just remember to seperate them by ; in quotes like ';'

```bash
parallel echo counting lines';' wc -l ::: example.*
```

The value will be normally appended to end of the command but you can put it wherever you want using {} as stated earlier

```bash
parallel echo counting {}';' wc -l {} ::: example.*
```

If you have multiple inputs then you can address them as {1}, {2}, {3} and so on
```bash
parallel echo count {1} in {2}';' wc {1} {2} ::: -l -c ::: example.*
```

You can use --dry-run to see the actual commands that will be run. This comes very handy also as a shell script generator.

### Control the output
By default parallel will launch all commands in parallel and print their output as soon as any of the commands complete
This means that you might not see the output in the same order as the input. However this can be controlled using the `--keep-order/-k` parameter which will ensure that the output is printed in the same order as the input even though the commands may run and complete in a different order.

### Dynamic replacement variables
When working with files you often want to do processing like remove extensions, get dirname etc. These can be done with replacement strings using `--rpl`. The cool thing is you can do this multiple times and create multiple vars

Lets see this with an example
```bash
# This will find all the .fq.gz files
# The variable b will remove the parent dirname
# The variable c will remove the .fq.gz extension
# This can also be done with parallel inbuild vars but this is just an example
find -name "*fq.gz"|parallel --dry-run --rpl '{b} s/.*?fastq\///' --rpl '{c} s/\.fq\.gz//' "STAR {b} {c}"
```
