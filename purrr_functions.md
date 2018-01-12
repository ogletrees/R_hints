To read is a bunch of files that are in a folder
```r
library(purrr)
data <- list.files("../folder/", full.names = T) %>% map_df(read.csv, stringsAsFactors =F)
# 'map' will read them is as a list of data frames.
# 'map_df' will go ahead and bind them up. Unique cols to one df will be NA in others.

```
