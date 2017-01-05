Bring the text in a pdf into R line by line
``` r
## PDF TO TEXT LINES ####
doc <- "file.pdf"
Rpdf <- readPDF(control = list(text = "-layout"))
system.time(corp <- VCorpus(URISource(doc), readerControl = list(reader = Rpdf)))
system.time(pdf.array <- content(content(corp)[[1]]))
# I only know how to work with data frame, so make one
pdf_df <- data.frame(pdf.array)
```
