So, we have data in a data frame and it's in long format
```r
   Ind yr value val2 val3
1 Ind1 97     1   21   41
2 Ind2 97     2   22   42
3 Ind3 97     3   23   43
4 Ind1 98     4   24   44
5 Ind2 98     5   25   45
6 Ind3 98     6   26   46
...
```
and we want it to be wide. Sometimes this is what ArcGIS works with because it can't do time well.  
Here's how we transform the data:  
`tidyr` is really set to take from wide to long, or "tidy". Going the other way is not pretty.  
`reshape` is what we want here
```r
reshape(results, idvar="Ind", timevar="yr", direction="wide")
```
`idvar` is the identifier, like the participant id who will be assessed many times.  
`timevar` is the indicator of which treatment or which number of the repeated assessments.

So sometimes this doesn't work and I get a column with all of the column names smashed together and no values. This is when using `reshape` like the above code. The data I have is like this:
```r
# Parcel | Year | Land | Impr | Total
```
and I need it as:
```r
# Parcel | Land.1 | Impr.1 | Total.1 | Land.2 | Impr.2 | Total.2 | ...
```
The issue is tibbles, `reshape` does not like them, so do this
```r
df_wide <- reshape(as.data.frame(df), idvar = "id", timevar = "time", direction = "wide")
```
