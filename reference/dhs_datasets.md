# API request of DHS Datasets

API request of DHS Datasets

## Usage

``` r
dhs_datasets(
  countryIds = NULL,
  selectSurveys = NULL,
  surveyIds = NULL,
  surveyYear = NULL,
  surveyYearStart = NULL,
  surveyYearEnd = NULL,
  surveyType = NULL,
  fileFormat = NULL,
  fileType = NULL,
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

- countryIds:

  Specify a comma separated list of country ids to filter by. For a list
  of countries use
  `dhs_countries(returnFields=c("CountryName","DHS_CountryCode"))`

- selectSurveys:

  Specify to filter data from the latest survey by including
  \`selectSurveys=TRUE\` in your request. Note: Please use this
  parameter in conjunction with countryCode, surveyType, or indicatorIds
  for best results.

- surveyIds:

  Specify a comma separated list of survey ids to filter by. For a list
  of surveys use
  `dhs_surveys(returnFields=c("SurveyId","SurveyYearLabel", "SurveyType","CountryName"))`

- surveyYear:

  Specify a comma separated list of survey years to filter by.

- surveyYearStart:

  Specify a range of Survey Years to filter Datasets on. surveyYearStart
  is an inclusive value. Can be used alone or in conjunction with
  surveyYearEnd.

- surveyYearEnd:

  Specify a range of Survey Years to filter Datasets on. surveyYearEnd
  is an inclusive value. Can be used alone or in conjunction with
  surveyYearStart.

- surveyType:

  Specify a survey type to filter by.

- fileFormat:

  Specify the file format for the survey. Can use file format type name
  (SAS, Stata, SPSS, Flat, Hierarchical) or file format code. View list
  of file format codes -
  <https://dhsprogram.com/data/File-Types-and-Names.cfm>

- fileType:

  Specify the type of dataset generated for the survey (e.g. household,
  women, men, children, couples, etc.). View list of file type codes -
  <https://dhsprogram.com/data/File-Types-and-Names.cfm>

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

Returns a `data.table` of 13 (or less if `returnFields` is provided)
datasets with their corresponding details. A detailed description of all
the attributes returned is provided at
<https://api.dhsprogram.com/rest/dhs/datasets/fields>

## Examples

``` r

if (FALSE) { # \dontrun{
# The API endpoint for the datasets available within the DHS website
# is a very useful endpoint, which is used a lot within `rdhs`. For example,
# it is used to find the file names and size of the dataset files, as well
# as when they were last modified. This enables us to see which datasets
# have been updated and may thus be out of date. For example to find all
# datasets that have been modified in 2018:

dat <- dhs_datasets()
dates <- rdhs:::mdy_hms(dat$FileDateLastModified)
years <- as.POSIXlt(dates, tz = tz(dates))$year + 1900
modified_in_2018 <- which(years == 2018)

# A complete list of examples for how each argument to the datasets
# API endpoint can be provided is given below, which is a
# copy of each of the examples listed in the API at:

# https://api.dhsprogram.com/#/api-datasets.cfm


dat <- dhs_datasets(countryIds="EG",all_results=FALSE)
dat <- dhs_datasets(selectSurveys="latest",all_results=FALSE)
dat <- dhs_datasets(surveyIds="SN2010DHS",all_results=FALSE)
dat <- dhs_datasets(surveyYear="2010",all_results=FALSE)
dat <- dhs_datasets(surveyYearStart="2006",all_results=FALSE)
dat <- dhs_datasets(surveyYearStart="1991", surveyYearEnd="2006",
all_results=FALSE)
dat <- dhs_datasets(surveyType="DHS",all_results=FALSE)
dat <- dhs_datasets(fileFormat="stata",all_results=FALSE)
dat <- dhs_datasets(fileFormat="DT",all_results=FALSE)
dat <- dhs_datasets(fileType="KR",all_results=FALSE)
dat <- dhs_datasets(f="geojson",all_results=FALSE)
} # }
```
