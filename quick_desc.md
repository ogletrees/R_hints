This function can be used to get a quick idea of NA's and 0's
```r
quickDesc <- function(df) {
  l1 <- lapply(df, function(x) sum(x == 0, na.rm = T))
  l2 <- lapply(df, function(x) sum(is.na(x)))
  l3 <- lapply(df, function(x) class(x))

  quickD <- cbind(l2, l1, l3)
  quickD <- as.data.frame(quickD)
  names(quickD) <- c("AreNA", "AreZero", "ColType")
  quickD <- lapply(quickD, function(x) unlist(x))
  quickD <- as.data.frame(quickD)
  return(quickD)
}
```
