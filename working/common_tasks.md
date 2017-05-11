When some value is associated with many others, and you want them into a comma delimited cell
```r
df %>% filter(col.1 %in% df2$col.1) %>% group_by(col.1) %>% summarise(codes = str_c(col.2, collapse = ";")) 
```
