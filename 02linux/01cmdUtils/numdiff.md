### Numdiff

Numdiff is an open source tool that can be used to do a diff between files while ignoring small numerical differences. More details at [Numdiff](https://github.com/tjhei/numdiff). Numdiff has a very informative manual which can be accessed on the command line as `info numdiff`

#### Compring two files while ignoring differences smaller than e.g 0.0001
```bash
numdiff --absolute-tolerance 0.0001 file1.txt file2.txt
```
