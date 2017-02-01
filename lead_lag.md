Suppose you want to lead or lag a column into another column

```r
library(dplyr)
df <- mutate(df, new_col = lead(col)) # can add ', n = _' to move more than one

```
```lead``` will pull it up one. ```lag``` will push it down one.
