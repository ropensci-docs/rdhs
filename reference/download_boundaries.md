# DHS Spatial Boundaries

Download Spatial Boundaries

## Usage

``` r
download_boundaries(
  surveyNum = NULL,
  surveyId = NULL,
  countryId = NULL,
  method = "sf",
  quiet_download = FALSE,
  quiet_parse = TRUE,
  server_sleep = 5,
  client = NULL
)
```

## Arguments

- surveyNum:

  Numeric for the survey number to be downloaded. Values for surveyNum
  can be found in the datasets or surveys endpoints in the DHS API that
  can be accessed using
  [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md)
  and
  [`dhs_surveys`](https://docs.ropensci.org/rdhs/reference/dhs_surveys.md).
  Default is NULL, which will cause the SurveyId to be used to find the
  survey.

- surveyId:

  Numeric for the survey ID to be downloaded. Values for surveyId can be
  found in the datasets or surveys endpoints in the DHS API that can be
  accessed using
  [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md)
  and
  [`dhs_surveys`](https://docs.ropensci.org/rdhs/reference/dhs_surveys.md).
  Default is NULL, which will cause the SurveyNum to be used to find the
  survey.

- countryId:

  2-letter DHS country code for the country of the survey being
  downloaded. Default = NULL, which will cause the countrycode to be
  looked up from the API.

- method:

  Character for how the downloaded shape file is read in. Default =
  "sf", which uses
  [`sf::st_read`](https://r-spatial.github.io/sf/reference/st_read.html).
  Currently, this is the only option available(\`rgdal\` used to be
  available) but for development reasons this will be left as a
  parameter option for possible future alternatives to read in spatial
  files. To just return the file paths for the files use method = "zip".

- quiet_download:

  Whether to download file quietly. Passed to \[\`download_file()\`\].
  Default is \`FALSE\`.

- quiet_parse:

  Whether to read boundaries dataset quietly. Applies to \`method =
  "sf"\`. Default is \`TRUE\`.

- server_sleep:

  Numeric for length of sleep prior to downloading file from their
  survey. Default 5 seconds.

- client:

  If the request should be cached, then provide a client object created
  by
  [`client_dhs`](https://docs.ropensci.org/rdhs/reference/client_dhs.md).
  Default = \`NULL\`, which will search for a client to use

## Value

Returns either the spatial file as a \`sf\` (see \[sf::sf\]) object, or
a vector of the file paths of where the boundary was downloaded to.

## Details

Downloads the spatial boundaries from the DHS spatial repository, which
can be found at <https://spatialdata.dhsprogram.com/home/>.

## Examples

``` r
if (FALSE) { # \dontrun{
 # using the surveyNum
 res <- download_boundaries(surveyNum = 471, countryId = "AF")

 # using the surveyId and no countryID
 res <- download_boundaries(surveyId = "AF2010OTH")

 } # }
```
