# API request of DHS Info

API request of DHS Info

## Usage

``` r
dhs_info(
  infoType = NULL,
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

- infoType:

  Specify a type of info to obtain the information requested. Default is
  version. \`infoType="version"“ (default) Provides the version of the
  API. Example:
  https://api.dhsprogram.com/rest/dhs/info?infoType=version
  \`infoType="citation"\` Provides the citation for the API to include
  with your application or data. Example:
  https://api.dhsprogram.com/rest/dhs/info?infoType=citation

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

Returns a `data.table` of 2 (or less if `returnFields` is provided)
fields describing the type of information that was requested and a value
corresponding to the information requested.
<https://api.dhsprogram.com/rest/dhs/info/fields>

## Examples

``` r

if (FALSE) { # \dontrun{
# The main use for the info API  will be to confirm the version of the API
# being used to providing the most current citation for the data.

dat <- dhs_info(infoType="version")

# A complete list of examples for how each argument to the info API
# endpoint can be provided is given below, which is a copy of each of
# the examples listed in the API at:

# https://api.dhsprogram.com/#/api-info.cfm


dat <- dhs_info(infoType="version",all_results=FALSE)
dat <- dhs_info(infoType="citation",all_results=FALSE)
dat <- dhs_info(f="html",all_results=FALSE)
} # }
```
