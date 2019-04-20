# cut

## Reverse the selection

Sometimes you want to use cut to remove some column and keep all the rest. This can be done using the `--complement` option. This is like `-v` is grep

```bash
# Select everything except column 1,2 and 3
cut -f 1,2,3 --complement
```

