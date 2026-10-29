# API request of DHS Data Updates

API request of DHS Data Updates

## Usage

``` r
dhs_data_updates(
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
  data that have been updated on or after the specified date will be
  returned.

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

Returns a `data.table` of 9 (or less if `returnFields` is provided)
indicators or surveys that have been added/updated or removed. A
detailed description of all the attributes returned is provided at
<https://api.dhsprogram.com/rest/dhs/dataupdates/fields>

## Examples

``` r

if (FALSE) { # \dontrun{
# The API endpoint for the data updates available within the DHS
# is a very useful endpoint, which is used a lot within `rdhs`. For example,
# we use it to keep the end user's cache up to date. For example to find all
# updates that have occurred in 2018:

dat <- dhs_data_updates(lastUpdate="20180101")

# A complete list of examples for how each argument to the data updates
# API endpoint can be provided is given below, which is a
# copy of each of the examples listed in the API at:

# https://api.dhsprogram.com/#/api-dataupdates.cfm


dat <- dhs_data_updates(lastUpdate="20150901",all_results=FALSE)
dat <- dhs_data_updates(f="html",all_results=FALSE)
} # }
```
