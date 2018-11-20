# RMARKDOWN

R-markdown is an awesome way to create do an analysis in R. You can write comments, workflows and all other details for your analysis in the markdown document iself.

## Header for R Markdown

You can create sligtly better looking documents by modifiyng the header for your markdown documents. An example header would be

``` yaml
title: "Test"
author: "rizoic"
date: "`r format(Sys.time(), '%d %B, %Y')`"
output: 
  html_document:
    toc: true
    toc_float: true
    theme: cosmo
    highlight: tango
```
