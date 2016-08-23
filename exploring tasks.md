To take a look at things, here are some things to remember.

Find out how many of something is in a column, like 0's or NA
```r
# for NAs
sum(is.na(df$col))

# for 0's
sum(df$col==0, na.rm = TRUE)

# using dplyr
df %>% count(col==0) # you get FALSEs, TRUEs, and NAs
```


