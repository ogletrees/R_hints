Sometimes I like to get data from a server. Here's how to do that.

```r
library(httr)
library(jsonlite)
library(dplyr)

# This will fetch the file (i.e geojson) and write it to disk. This is nice as then you have it locally.
x <- GET("url", write_disk("file.ext"))

# you can also parse this in R, like with a json file
y <- GET("url")
y2 <- content(y)
y3 <- fromJSON(y2)
# and then poke around y3 to get the data frame (like y3$features)
```
