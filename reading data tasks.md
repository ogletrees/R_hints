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
```r
Warning message:
In scan(file = file, what = what, sep = sep, quote = quote, dec = dec,  :
  EOF within quoted string
  ```
  when a data point has only one quotation mark. Adding `quote = ""` can get the data in but now all of the quotation marks come too. At this point you probably have to just replace them with `df$col <- gsub('"', '', df$col)`. Alternatively, try a `for` loop
  ```r
  for(i in names(df)){
  df[[i]] <- gsub("\"", "", df[[i]])
}
```
## reading data in as a list of dataframes
If you have a folder of .csv for example, you can bring them is an a list of data frames. Here is how
```r
#If the path is different than your working directory
# you'll need to set full.names = TRUE to get the full
# paths.
my_files <- list.files("./folder") # ./ for relative path. 
my_files <-  paste("./folder/", my_files, sep = "")
my_files


#Further arguments to read.csv can be passed in ...
all_csv <- lapply(my_files,read.csv) # read.csv, colClasses=...  for eaxample

#Set the name of each list element to its
# respective file name. Note full.names = FALSE to
# get only the file names, not the full path.
names(all_csv) <- gsub(".csv","",
                       list.files("./folder",full.names = FALSE),
                       fixed = TRUE)
```

You can read in data from the clipboard, eith from Excel or other text files. Varys depnding on OS.
```r
# for Windows:

x <- read.delim("clipboard")
# for Mac OS:

x <- read.delim(pipe(“pbpaste”))

read.table(file = "clipboard", sep = "\t", header=TRUE) # Alternative
```
With ```psych``` package
```r
x <- read.clipboard()
```
