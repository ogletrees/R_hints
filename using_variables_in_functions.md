When it would be nice to select a column in a function or loop.

Like, there are numerous columns with names like 'use97', 'use98', 'use99'. If working in a for loop I might want to select those in each run. Maybe like this:
```r
yr <- 97
x <- paste("use", yr)
df %>% select(x)
```
but this will throw and error since ther is no column name == x

I think this is nonstandard evaluation.

If using janitor::tabyl

```r
yrs <- 1997:2009
luccol <- sym(paste0("use", substr(yrs[1], 3, 4)))
t97 <- df %>% tabyl(!!luccol)
```
The `!!` evaluate the `luccol` object before running `tabyl` I think.
