### Check character lengths
Let's say you have a column of character values and they all need to be the same length but you don't know if they were all entered that way.  
Check the range of lengths
```r
# this uses the stringi package
range(stringi::stri_length(df$col), na.rm = TRUE)
```
### Add leading 0's
```r
# this uses the stringr package
df$col_a <- stringr::str_pad(df$col_a, no of digits, pad = "0")
```

### Formatting
If you need a specific formatting, like adding dashes at certain places in a string
```r
# format with dashes. In this case we get a 12 digit char -> xxx-xxx-xxx-xxx
df$col_a <- gsub("(\\d\\d\\d)(\\d\\d\\d)(\\d\\d\\d)(\\d\\d\\d)", "\\1-\\2-\\3-\\4", df$col_a)
```
