## .csv  
Using ```read.csv```  
```r
# you can make read.csv get the column types right for you, but you have to tell it
df <- read.csv("C:/Users/file.csv", colClasses = c("character", "character", "numeric", "numeric"), na.strings = "")
```
