---
title: "Import the Data"
output: html_document
---

## read datasets
What do our datasets look like?

```r
# library
library(tidyverse)
```

```
## -- Attaching packages --------------------------------------- tidyverse 1.3.0 --
```

```
## v ggplot2 3.3.2     v purrr   0.3.4
## v tibble  3.0.3     v dplyr   1.0.2
## v tidyr   1.1.2     v stringr 1.4.0
## v readr   1.3.1     v forcats 0.5.0
```

```
## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
library(readxl)
library(tidytext)
library(broom)
library(stopwords)
library(dplyr)
library(skimr)

# full_d for the full dialog, not annotated
full_d_raw = read_csv('data/FullData/full_dialog.csv',
         col_names = TRUE)
```

```
## Error: 'data/FullData/full_dialog.csv' does not exist in current working directory ('C:/Users/Public/User Documents/Documents/RStudio-NCSU/data').
```

```r
full_i_raw = read_csv('data/FullData/full_info.csv',
         col_names = TRUE) %>% 
  rename_with(~str_remove(.,"\\.x$"))
```

```
## Error: 'data/FullData/full_info.csv' does not exist in current working directory ('C:/Users/Public/User Documents/Documents/RStudio-NCSU/data').
```

```r
# anonymous fn ? regular expression (python/perl/real programming)

fullset = full_d_raw %>% 
  left_join(full_i_raw) %>% 
  select(
    ConvoId = B2,
    Turn = Turn,
    Role = B4, # (0 = persuader, 1 = persuadee)
    Dialogue = Unit,
    User = B3,
    NumTurn = B7,
    Donation = B6,
    everything()
    )
```

```
## Error in eval(lhs, parent, parent): object 'full_d_raw' not found
```

```r
full_d_raw = full_d_raw %>% 
  select(
    ConvoId = B2,
    Turn = Turn,
    Role = B4, # (0 = persuader, 1 = persuadee)
    Dialogue = Unit
  )
```

```
## Error in eval(lhs, parent, parent): object 'full_d_raw' not found
```

```r
# there were some really cool functions Julia used to clean up the data. One for smushing the two colums in the annotated set together, and one to get rid of the ".x" on the end of the identity variables. and a very cool funtion for looking at summary things


# ann_d for the full dialog, with annotations
ann_d_raw = read_xlsx('data/AnnotatedData/300_dialog.xlsx',
         col_names = TRUE)
```

```
## Error: `path` does not exist: 'data/AnnotatedData/300_dialog.xlsx'
```

```r
# ann_i for the corresponding index file
ann_i_raw = read_xlsx('data/AnnotatedData/300_info.xlsx',
         col_names = TRUE)
```

```
## Error: `path` does not exist: 'data/AnnotatedData/300_info.xlsx'
```

```r
annset = ann_d_raw %>% 
  left_join(ann_i_raw) %>%
  select(
    ConvoId = B2,
    Turn = Turn,
    Role = B4, # (0 means persuader, 1 means persuadee)
    Sentence = Unit,
    User = B3,
    Donation = B6,
    IntDonation = B5,
    NumTurn = B7,
    # Label1 = # concat(er_label_1,ee_label_1),
    # Label2 = # concat(er_label_2,ee_label_2),
    Neg = neg,
    Neu = neu,
    Pos = pos,
    everything()
  )
```

```
## Error in eval(lhs, parent, parent): object 'ann_d_raw' not found
```

```r
# annset = ann_d %>% select()
###
```

## tidyr

What can we do with tidyr? Here are some transformations from chapter 1 of Silge's Text Mining With R to make token per row data. 

```
## Error in eval(lhs, parent, parent): object 'fullset' not found
```

```
## Error in eval(lhs, parent, parent): object 'full_d_raw' not found
```
