If the order of the factors is good in the data frame, but they get reordered into alphebetical in ggplot, then this is the answer
```r
 %>% mutate(col = factor(col, col)) # 'col' is the column you want to set the order to
```
