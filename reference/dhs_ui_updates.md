# API request of DHS UI Updates

API request of DHS UI Updates

## Usage

``` r
dhs_ui_updates(
  lastUpdate = NULL,
  f = NULL,
  returnFields = NULL,
  perPage = NULL,
  page = NULL,
  client = NULL,
  force = FALSE,
  all_results = TRUE
)
```

## Arguments

- lastUpdate:

  Specify a date or Unix time to filter the updates by. Only results for
  interfaces that has been updated on or after the specified date will
  be returned.

- f:

  You can specify the format of the data returned from the query as
  HTML, JSON, PJSON, geoJSON, JSONP, XML or CSV. The default data format
  is JSON.

- returnFields:

  Specify a list of attributes to be returned.

- perPage:

  Specify the number of results to be returned per page. By default the
  API will return 100 results.

- page:

  Allows specifying a page number to obtain for the API request. By
  default the API will return page 1.

- client:

  If the API request should be cached, then provide a client object
  created by
  [`client_dhs`](https://docs.ropensci.org/rdhs/reference/client_dhs.md)

- force:

  Should we force fetching the API results, and ignore any cached
  results we have. Default = FALSE

- all_results:

  Boolean for if all results should be returned. If FALSE then the
  specified page only will be returned. Default = TRUE.

## Value

Returns a `data.table` of 3 (or less if `returnFields` is provided)
interfaces that have been added/updated or removed. A detailed
description of all the attributes returned is provided at
<https://api.dhsprogram.com/rest/dhs/uiupdates/fields>

## Examples

``` r

if (FALSE) { # \dontrun{
# The main use for the ui updates API will be to search for the last time
# there was a change to the UI. For example to return all the
# changes since 2018:

dat <- dhs_ui_updates(lastUpdate="20180101")

# A complete list of examples for how each argument to the ui updates API
# endpoint can be provided is given below, which is a copy of each of
# the examples listed in the API at:

# https://api.dhsprogram.com/#/api-uiupdates.cfm


dat <- dhs_ui_updates(lastUpdate="20150901",all_results=FALSE)
dat <- dhs_ui_updates(f="html",all_results=FALSE)
} # }
```
