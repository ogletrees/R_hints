Joining with dplyr - join df.a to df.b with column names that are different
```r
left_join(df.a, df.b, by = c("col.x" = "col.y")) 
df.a %>% left_join(df.b, by = c("col.x" = "col.y"))
```
this will result in having all of df.a and then matched rows from df.b. No match with be ```NA```
