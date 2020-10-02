---
title: "Import the Data"
output: html_document
---



## read datasets
What do our datasets look like?

```
## Warning: Missing column names filled in: 'X1' [1]
```

```
## Parsed with column specification:
## cols(
##   X1 = col_double(),
##   Unit = col_character(),
##   Turn = col_double(),
##   B4 = col_double(),
##   B2 = col_character()
## )
```

```
## Parsed with column specification:
## cols(
##   .default = col_double(),
##   B2 = col_character(),
##   B3 = col_character(),
##   sex.x = col_character(),
##   race.x = col_character(),
##   edu.x = col_character(),
##   marital.x = col_character(),
##   employment.x = col_character(),
##   religion.x = col_character(),
##   ideology.x = col_character()
## )
```

```
## See spec(...) for full column specifications.
```

```
## Joining, by = c("B4", "B2")
```

```
## New names:
## * `` -> ...1
```

```
## Joining, by = c("B2", "B4")
```

## tidyr

What can we do with tidyr? Here are some transformations from chapter 1 of Silge's Text Mining With R to make token per row data. 

```
## Error in check_input(x): Input must be a character vector of any length or a list of character
##   vectors, each of which has a length of 1.
```
