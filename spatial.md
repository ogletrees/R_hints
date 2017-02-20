The ArcGIS page gives some help on spatial. Another way to deal with some of this would be to convert to simple features with `sf` package.

```r
spdf # a SpatialPolygonsDataFrame, has data and spatial info
library(sf)

sf_df <- st_as_sf(spdf) # converts from sp object to sf object
df <- as.data.frame9sf_df) # now just a plain ol' data frame
```

You can also read shapefiles, KMZ, and KML with `sf` package.
```r
biketrails_shp <- st_read("biketrails.shp")
if(Sys.info()[1] == "Linux") # may not work if not Linux
  biketrails_kmz <- st_read("BikePaths.kmz")
u_kml = "http://www.northeastraces.com/oxonraces.com/nearme/safe/6.kml"
download.file(u_kml, "bikeraces.kml")
bikraces <- st_read("bikeraces.kml")
```
