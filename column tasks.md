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

# you can use colnames too. I think you have to name them all or R will start reusing the names you give
colnames(df) <- c("A", "B", "C", "D", "E", "F", "G")
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
To add to the column name
```r
colnames(df) <- paste("pre", colnames(df), sep = "_")  # prefix
colnames(df) <- paste(colnames(df), "suf", sep = "_")  % suffix
```
### Reorder columns
```r
# order names alphabetically
df <- df[ , order(names(df))]
# reorder according to col index
df <- df[, c(5, 21, 6:20, 1:4)]
```
## Look up values and change  
If you need to change the values in a column based on their match in another data frame
```r
# this with match the values from myframe$x and ref$x and return the values from ref$y
myframe$y <-  ref$y[match(myframe$x,ref$x)]
# if you want to overwrite the source value
myframe$x <-  ref$y[match(myframe$x,ref$x)]
```
## Change multiple column classes
```r
cols.num <- c("a","b")
DF[cols.num] <- sapply(DF[cols.num],as.numeric)
```
## Investigating duplicates in a column
You can get the rows that show up more than once with
```r
# requires dplyr
df %>% count(col) %>% filter(n > 1)
```
If this is saved to a df then that df can be used to filter the main df to see the whole row
```r
df_check <-  df1[which(df1$colx %in% df2$colx),] %>% arrange(colx)
```
