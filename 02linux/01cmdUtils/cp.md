### cp notes

cp is a command line program to copy files/directories.[Online man page](http://man7.org/linux/man-pages/man1/cp.1.html)

#### Copy entire folder structure with files(but all files of 0 KB)

If a directory has a multi level structure having important large outfiles of an analysis and you want to test something on this. It comes very handy to just replicate the entire structure else where with the same file names. But copying so many files is time consuming and not required. So cp can be used to copy an entire folder structure and create all the files in it just that they will be 0 KB

```bash
cp -r --attributes-only /path/to/dir1 /path/to/dir2
```
[Source](https://stackoverflow.com/a/11946544)
