To read in a bunch of files that are in a folder
```r
library(purrr)
data <- list.files("../folder/", full.names = T) %>% map_df(read.csv, stringsAsFactors =F)
# 'map' will read them is as a list of data frames.
# 'map_df' will go ahead and bind them up. Unique cols to one df will be NA in others.

```
If you make a nested data frame you can apply a function over certain columns in those data frames that are in a list.
```r
# for example, creating a new col with the mean of a column in the nested data frames
# data frames are in 'data', the col is 'lifeExp'
by_country <- by_country %>% 
  mutate(mean_lifeExp = map(data, ~round(mean(.$lifeExp), 2)), sd_life = map(data, ~round(sd(.$lifeExp), 2)))
  ```
  This produces a list column, so use `unlist()` to get back to a vector. `purr` can do this with another function too I think.
