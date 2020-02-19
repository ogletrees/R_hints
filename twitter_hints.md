Deal with converting the date format

```r
formatTwDate <- function(datestring, format="datetime"){
    if (format=="datetime"){
        date <- as.POSIXct(datestring, format="%a %b %d %H:%M:%S %z %Y")
    }
    if (format=="date"){
        date <- as.Date(datestring, format="%a %b %d %H:%M:%S %z %Y")
    }   
    return(date)
}
```

from: SMAPPNYU/smappR


Converting the Twitter created_at format:
```r
df$tdate <- as.Date(df$created_at, format="%a %b %d %H:%M:%S %z %Y")
df %>% count(tdate) %>% ggplot(aes(tdate, n)) + geom_col()
```
