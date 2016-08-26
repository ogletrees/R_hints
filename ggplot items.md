To get the bars in a bar plot to be in order based on the y value
```r
ggplot(df, aes(reorder(col1, col2), col2)  # likely ordered low to high
ggplot(df, aes(reorder(col1, -col2), col2) # reverse order
```
### x axis labels
To rotate the labels
```r
+ theme(axis.text.x = element_text(angle = 45, hjust = 1, vjust = 1))
```
