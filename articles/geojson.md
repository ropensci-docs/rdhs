# Interacting with geojson API returns

## Overview

The API can return geojson objects, which can be very useful for quickly
creating maps of the DHS indicator data. These are large objects though,
and can cause the API to return slowly if too much data is returned.

In this demonstration we will be using 2 other packages, `leaflet` and
`geojson`.

------------------------------------------------------------------------

``` r

# load our package
library(rdhs)

# install other packages
# install.packages("geojson")
# install.packages("leaflet")
```

``` r

# make request
d <- dhs_data(countryIds = "SN",
              indicatorIds = "FE_FRTR_W_A15",
              surveyYearStart = 2014,
              breakdown = "subnational",
              returnGeometry = TRUE,
              f = "geojson")

# convert to sp
m <- geojsonio::as.json(d)
nc <- geojsonio::geojson_sp(m) 

# plot using leaflet
pal <- leaflet::colorNumeric("viridis", NULL)

leaflet::leaflet(nc[nc$IndicatorId=="FE_FRTR_W_A15",]) %>%
  leaflet::addTiles() %>%
  leaflet::addPolygons(stroke = FALSE, smoothFactor = 0.3, fillOpacity = 1,
              fillColor = ~pal(log10(Value)),
              label = ~paste0(CharacteristicLabel, ": ", formatC(Value, big.mark = ","))) %>%
  leaflet::addLegend(pal = pal, values = ~log10(Value), opacity = 1.0,
            labFormat = leaflet::labelFormat(transform = function(x) round(10^x)),title = ~Indicator[1])
```
