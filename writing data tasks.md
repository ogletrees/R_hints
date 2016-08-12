## writing to .csv  

```r
# this makes sure that NAs are blank and doesn't make row numbers that would show up on import later
write.csv(pdata, "C:/Users/file.csv", na = "", row.names = FALSE )
```
