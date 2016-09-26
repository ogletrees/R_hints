## writing to .csv  

```r
# this makes sure that NAs are blank and doesn't make row numbers that would show up on import later
write.csv(pdata, "C:/Users/file.csv", na = "", row.names = FALSE )
```
Write the stuff that would go to console to a text file
```r
sink("TheFile.txt")
# code goes here
sink()
```
[link] (http://www.cookbook-r.com/Data_input_and_output/Writing_text_and_output_from_analyses_to_a_file/)
