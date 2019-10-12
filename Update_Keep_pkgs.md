You can do this in the R app

1.	Before you upgrade, build a temp file with all of your old packages.
```r
tmp <- installed.packages()
installedpkgs <- as.vector(tmp[is.na(tmp[,"Priority"]), 1])
save(installedpkgs, file="installed_old.rda")
```
2. Install the new version of R and let it do it’s thing.

3. Once you’ve got the new version up and running, reload the saved packages and re-install them from CRAN.
```r
load("installed_old.rda")
tmp <- installed.packages()
installedpkgs.new <- as.vector(tmp[is.na(tmp[,"Priority"]), 1])
missing <- setdiff(installedpkgs, installedpkgs.new)
install.packages(missing)
update.packages()
```
From https://www.datascienceriot.com/how-to-upgrade-r-without-losing-your-packages/kris/

non-CRAN packages:

devtools::install_github("rmcelreath/rethinking")  
devtools::install_github("thomasp85/patchwork")  

