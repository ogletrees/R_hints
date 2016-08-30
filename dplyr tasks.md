If you want to collect duplicates in a col and summarise the other cols
```r
df %>% group_by(grp) %>% summarise_each(funs(mean(., na.rm = TRUE)))  # also 'sum' for instance. (., na.rm = TRUE) if there are NAs
```
