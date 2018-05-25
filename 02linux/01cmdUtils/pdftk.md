### PDFTK

A tool for manipulating pdf files from the command line. Man page at [Source](http://manpages.ubuntu.com/manpages/xenial/en/man1/pdftk.1.html)

#### Rotating pdf files

Rotate and save a copy of the roatated pdf file

```bash
pdftk input.pdf cat 1-endsouth output output.pdf
#        \_______/     \___/\___/        \________/
#        input file    range  |          output file
#                           direction
```
Where direction can be any of these:

north
south
east
west
left
right
down

[Source](https://askubuntu.com/a/821617)
