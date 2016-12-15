If you need to replace a value in a column, based on the values in another data frame, leaving the not matches alone.
[link] (http://stackoverflow.com/questions/6112260/conditional-merge-replacement-in-r)
```r
df1$x2[match(df2$x1,df1$x1)] <- df2$x2
```
The example given looks like
```r
df1
x1  x2
1   a
2   b
3   c
4   d
df2
x1  x2
2   zz
3   qq
# resulting df
df1
x1  x2
1   a
2   zz
3   qq
4   d
```
The above did not work one time, so I found this
```r
x <- data.frame("puba" = c("1", "3", "0", "2", "1"), "pubb" = c("1", "3", "0", "2", "1"), stringsAsFactors = F)
y <- data.frame("code" = c("0", "1", "2", "3"), "acc" = c("No", "yes", "maybe", "question"), stringsAsFactors = F)
x$puba[match(y$code,x$pubb)] <- y$acc

for(id in 1:nrow(y)){
  x$pubb[x$puba %in% y$code[id]] <- y$acc[id]
}
```
