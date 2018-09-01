# SED

sed is a stream editor. It can perform text transformations on an input stream which can be piped or a file. [More Info](https://www.gnu.org/software/sed/manual/sed.html)

## Convert multiline input to single line with a delimiter

You can use sed to convert piped multi line input to a single line with custom delimiter as follows

```bash
# This will find all fastq.gz file and then convert it to a comma seperated file list
find -name "*.fastq.gz"|sort|sed -e ':a;N;$!ba;s/\n/,/g'
```

An explanation as to what these modifiers actually do can be found [here](https://stackoverflow.com/a/1252191)
