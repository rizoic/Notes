# GREP

**grep** is a commnadline utility for searching plain text files for lines that match a regular expression.[More Info](https://www.gnu.org/savannah-checkouts/gnu/grep/manual/grep.html)

## Grep one file based on lines in another files

You can use grep to filter one files based on another

```bash
grep -Fwf file_with_filters.txt file_to_filter.txt
```

You can obviously add a `-v` to reverse the filter.

Lets look into what the other agrs mean

```
-f Tells grep to obtain the patters frol a file which is file_with_filters.txt in our case
-w Select only those lines containing matches that form whole words. In you need the words to occour anywhere you can exclude this
-F Tell that the pattern in the file file_with_filters.txt are fixed and contain no regular expressions in them
```
