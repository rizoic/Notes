# STRING FUNCTIONS

Notes on functions that provide utility in dealing with strings in R. These notes are for the base string functions and not the ones that come with stringR

## match
`match` is a function which will give you the indices for a vector where things match in another one

```R
vec1 <- c('a','b','c')
vec2 <- c('s','a','t','y','b')
match(vec1, vec2) # Gives c(2,5)
```

In most of the scenarios `%in%` does the job for you but in some cases where you want to do things like select certain rows based on matches then `match` comes in handy.