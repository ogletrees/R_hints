If you get date and time coming in as character, it might be difficult to coerse it into the desired format. For example, 8/29/2016 11:44:19
```r
df$Date <- as.Date(df$Date, "%m/%d/%Y %H:%M:%S")
```
or

>The easiest way is to use lubridate:
```r
library(lubridate)
prods.all$Date2 <- mdy(prods.all$Date2)
```
>This function automatically returns objects of class POSIXct and will work with either factors or characters. [link](http://stackoverflow.com/questions/4310326/convert-character-to-date-in-r)

