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
