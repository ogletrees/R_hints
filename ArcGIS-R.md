To set up the bridge between ArcGIS and R
``` r
library(arcgisbinding) # load the package, this is set up with the toolbox in ArcGIS
arc.check_product() # this will check to see if you have a license. If using 64bit R you need ArcGIS Pro installed on the machine
```
Now to connect to a GIS file. In this case I will access a feature class in a geodatabase
```r
# build the arc-R bridge
df <- arc.open("../DataTest/test.gdb/featureclass")

# select the fields, all of them in this case
df_select <- arc.select(df, fields = "*") # this is a data frame with spatial information

# to keep the spatial data, convert to an sp object, SpatialPloygonsDataFrame
spdf <- arc.data2sp(df_select) # sp object can be plotted
```
This will give you a 'data.frame' in R. It is a 'data.frame' but also an `arc.data`. This is an `attribute$class` that contains spatial information, so when calling `str` you get the data and the spatial info.

We can get the data, or attributes, into a data frame
```r
str(df_select)
# Classes ‘arc.data’ and 'data.frame'...
class(spdf)
# [1] "SpatialPolygonsDataFrame"
# attr(,"package")
# [1] "sp
d <- spdf@data # this is where the attribute data lives in the "SpatialPolygonsDataFrame"
str(d)
# Classes ‘arc.data’ and 'data.frame'...
# ...
# - attr(*, "shape")=Formal class 'arc.shape' [package "arcgisbinding"] with 2 slots
# ...
# .. ..@ shapeinfo:List of 5
# .. .. ..$ type: chr "Polygon"
# .. .. ..$ hasZ: logi FALSE
# .. .. ..$ hasM: logi FALSE
# .. .. ..$ WKT : chr "GEOGCS[\"WGS 84\",DATUM[\"World Geodetic System 1984 (EPSG ID 6326)\",SPHEROID[\"WGS 84 (EPSG ID 7030)\",6378137.0,298.25722356"| __truncated__
# .. .. ..$ WKID: int 0
# .. .. ..- attr(*, "class")= chr  "list" "arc.shapeinfo"
```
You can roll with that, but I wonder if having just the data frame with no extra info might be needed sometime. To do that you need to remove the attribute (of the data frame) data.
```r
attributes(d)$shape <- NULL
class(d) <- "data.frame"
```
Now you have the data without the arc.data
