One thing I need to do sometimes is make sure that some data are in a particular CRS. 

There are 2 functions, one sets the CRS and one transforms. These are `st_crs` and `st_transform`.
```r
st_crs(sdf) # this will retrieve the CRS and print it to the console
tpl_sub <- st_transform(sdf, 5070) # with the assignment this will change the CRS to the EPSG given, 5070 in this case, this is reprojecting

st_crs(sdf) <- 4326
# Warning message:
# st_crs<- : replacing crs does not reproject data; use st_transform for that 
```
`st_transform` will reproject the data to a new CRS, so if a process requires that the 2 data frames be in the same CRS this is what you want to do.

Just changing the CRS will not do this.
