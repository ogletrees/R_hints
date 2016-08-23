## .csv  
Using ```read.csv```  
```r
# you can make read.csv get the column types right for you, but you have to tell it
df <- read.csv("C:/Users/file.csv", colClasses = c("character", "character", "numeric", "numeric"), na.strings = "")
```

Sometimes you get a .txt or .csv file where all of the data has quotes around it. Like:  
```
"item1","item2","item3",...
```
When you use `read.csv` all of your data is character with quotes, not good. This seems to be the result of some weirdness, as `read.csv` typically can figure it all out. If you get quoted data then one solution is to replace the quotes. Another is to go to the source file and save it as some other format.

---

You can also see this
```
Warning message:
In scan(file = file, what = what, sep = sep, quote = quote, dec = dec,  :
  EOF within quoted string
  ```
  when a data point has only one quotation mark.

