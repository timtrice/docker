# RStudio 3.4.4

This Dockerfile builds R 3.4.4 ("Someone to Lean On") with RStudio 1.1.447. 

## CRAN packages

* blogdown
* corrplot
* crul
* ggrepel
* Hmisc
* miniUI
* pander
* PKI
* RCurl
* rgdal
* rgeos
* RJSONIO
* rnaturalearthdata
* rsconnect
* servr
* skimr
* sweep
* tibbletime
* tidyquant
* timetk

## GitHub packages

* DavisVaughan/furrr 
* eddelbuettel/drat
* r-dbi/DBI
* r-dbi/odbc
* r-dbi/RMariaDB
* r-dbi/RPostgres
* r-lib/fs
* r-lib/pkgdown
* ropensci/rrricanes
* rstudio/rstudioapi 
* timtrice/HURDAT
* timtrice/NCDCStormEvents
* yihui/xfun

## Getting Started

### `flyingfox`

By and large, `flyingfox` is set up to run right out of the box. All required on the user side is to set a [Quandl API Key](https://docs.quandl.com/docs#section-authentication) and run

```r
flyingfox::fly_ingest()
```

The ingestion of data will take some time. Zipline data bundles are not automatically maintained and are not appended. Cleaning periodically is required, depending on usage. See [Zipine bundles](http://www.zipline.io/bundles.html).

## Notable Exceptions

### `flyingfox`

`reticulate` 1.6 was the latest CRAN Release as of BUILD_DATE 2018-04-23. `flyingfox` 0.1.0 requires `reticulate` 1.7. `reticulate` has not done a GitHub release since [v0.7](https://github.com/rstudio/reticulate/releases/tag/v0.7). Thankfully, there is a branch `cran/v1.7`. In order to use `flyingfox`, `reticulate` must be installed via `devtools::install_github()` which, as of this writing (Jun. 24, 2018) is version 1.7. 

```r
devtools::install_github("rstudio/reticulate@cran/v1.7")
```

Then, `flyingfox` can be installed.

```r
devtools::install_github("DavisVaughan/flyingfox")
```

### rstudioapi

`rstudioapi` must be installed via `devtools::install_github()` due to error (see Issue #1). Installing via CRAN, at least as of Jun. 24, 2018, will not allow `bookdown::serve_book()` to execute without error.
