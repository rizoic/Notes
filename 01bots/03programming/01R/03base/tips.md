# TIPS

General notes for R

1. When using the internals of any object/package which are not exported be extremely careful. They may not be meant for raw use and may be formatted/structured in a different way than you think.
2. How do you take z-scores for a matrix

```R
# For column wise Z scores
mat.z.scores <- scale(mat)

# For row wise Z scores
mat.z.scores <- t(scale(t(mat)))
```



