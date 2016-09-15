If you need to replace a value in a column, based on the values in another data frame, leaving the not matches alone.
[link] (http://stackoverflow.com/questions/6112260/conditional-merge-replacement-in-r)
```r
df1$x2[match(df2$x1,df1$x1)] <- df2$x2
```
