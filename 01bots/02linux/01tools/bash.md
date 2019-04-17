# BASH

Notes on general bash shell things

## Expansion using {}

Lets say you want to create three files `A.bed B.bed C.bed` one way to do this is

```bash
touch A.bed B.bed C.bed
```

However this a lot of typing. We can use bash curly brace expansion to save time here. This expansion can be used in the following way

```bash
# Still longer way
touch {A,B,C}.bed

# Even more awesome is using the inbuilt expansion for numbers and alphabets
touch {A..C}.bed
# Now imagine if you wanted to create 26 .bed files from A to Z. This would come is handy isnt it
```

You can find more information on such expansions [here](https://www.linuxjournal.com/content/bash-brace-expansion)
