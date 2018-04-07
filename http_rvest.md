```r
library(rvest)
url <- "https://www.example.com"
dp <- read_html(url)
dnodes <- html_nodes(dp, "td")


```
If you specify at html tag, you will likely get the text of the tag. So if you really want the url of the `a href` then you have to use `html_attr`

Look here too http://blog.rstudio.com/2014/11/24/rvest-easy-web-scraping-with-r/

This heled get urls https://stackoverflow.com/questions/43343658/rvest-extract-tables-with-urls-instead-of-text?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa
