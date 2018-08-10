From r cookbook, where bp is your ggplot:

Remove legend for a particular aesthetic (fill):
```r
bp + guides(fill=FALSE)
```
It can also be done when specifying the scale:
```r
bp + scale_fill_discrete(guide=FALSE)
```
This removes all legends:
```r
bp + theme(legend.position="none")
```
https://stackoverflow.com/questions/35618260/remove-legend-ggplot-2-2
