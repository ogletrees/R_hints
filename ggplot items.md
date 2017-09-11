To get the bars in a bar plot to be in order based on the y value
```r
ggplot(df, aes(reorder(x, y), y)  # likely ordered low to high
ggplot(df, aes(reorder(x, -y), y) # reverse order
```
### x axis labels
To rotate the labels
```r
+ theme(axis.text.x = element_text(angle = 45, hjust = 1, vjust = 1))
```
Labels
```r
+ labs(x = "label", y = "label", title = "title", caption = "caption", subtitle = "subtitle")
```
