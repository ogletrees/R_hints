## Column manipulations

### Rename columns  
```r
d
#>   alpha two gamma
#> 1     1   4     7
#> 2     2   5     8
#> 3     3   6     9

# You can also rename by position, but this is a bit dangerous if your data
# can change in the future. If there is a change in the number or positions of
# columns, then this can result in wrong data.

# Rename by index in names vector: change third item, "gamma", to "three"
names(d)[3] <- "three"
d
#>   alpha two three
#> 1     1   4     7
#> 2     2   5     8
#> 3     3   6     9
```
With ```data.table```  
```r
library(data.table)
d <- data.frame(a=1:2,b=2:3,d=4:5)
setnames(d, old = c('a','d'), new = c('anew','dnew'))
d
```
To change part of a column name
```r
names(df) = sub("replace this","with this",names(df)) 
```
### Reorder columns
```r
# order names alphabetically
df <- df[ , order(names(df))]
# reorder according to col index
df <- df[, c(5, 21, 6:20, 1:4)]
```
