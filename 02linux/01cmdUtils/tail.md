### Tail Notes

Tail is a command line utility to display lines from the end of a files


#### Using tail to remove the first line of a file
```bash
tail -n +2 filename
```

Explanation
`-n d` tells tail to print the last d lines of a file.
But if you say `-n +d` then it tells tail to rather print starting from line number d. So if you would have said +1 so it would print from the start. 
Note: This seems to be available only if you use GNU tail. Also this cannot do inplace replacement i.e. you cannot say `tail -n +2 file1.txt > file1.txt` This will give you an empty file.For detailed explanation see - [Source](https://stackoverflow.com/a/339941). 