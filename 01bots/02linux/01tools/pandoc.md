# Pandoc

## Convert one format to another

### Converting a .docx to text file

Converting a .docx to a text file is fairly straightforward. Its even quicker that opening the docx and copy pasting

```bash
pandoc -s input.docx -o output.text
```

### Convert from any format to another

You can also generically convert from any format to another by specifying them explicitly

```bash
pandoc -s input.docx -o output.text -f docx -t markdown
```

