You can put a number of data frame sin a list for both orderly environments and to do the same things to multiple data frames easily.

If you have a list of data frames you can access things inside.
```r
df.list[[1]] # access the first data frame
names(df.list[[1]]) # would give the col names of the first data frame
df.list[[1]][[3]] # would access the 3rd col of the 1st data frame
```

Subset columns
```r
df_list <- lapply(df_list, "[", c(2,5))
# or
df_list <- lapply(df_list, subset, colname != "0")
```
To get data frames in a list combined into one big data frame
```
df.dplyr <- as.data.frame(bind_rows(listOfDataFrames))
df.dplyr <- bind_rows(listOfDataFrames)
```
Of course, how to get a number of csv's into a data frame list? You likely would also like the data frames to have the name of the file they came from too.
```r
# bring all of the csv files in as data frame in a list
list_of_files <- list.files('../folder/', pattern = "*.csv", full.names = TRUE)

#Further arguments to read.csv can be passed in ...
all_in_list <- lapply(list_of_files,read.csv, stringsAsFactors = FALSE)

#Set the name of each list element to its respective file name. Note full.names = FALSE to get only the file names, not the full path.
names(all_in_list) <- gsub(".csv","", list.files('../folder/', pattern = ".csv", full.names = FALSE), fixed = TRUE)

```
if you want he individual data frame names added in a col
```r
library(data.table)
df.all <- rbindlist(df_list, idcol = "index")
```
