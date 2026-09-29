# API request of DHS Tags

API request of DHS Tags

## Usage

``` r
dhs_tags(
  countryIds = NULL,
  indicatorIds = NULL,
  surveyIds = NULL,
  surveyYear = NULL,
  surveyYearStart = NULL,
  surveyYearEnd = NULL,
  surveyType = NULL,
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

- indicatorIds:

  Specify a comma separated list of indicators ids to filter by. For a
  list of indicators use
  `dhs_indicators(returnFields=c("IndicatorId","Label","Definition"))`

- surveyIds:

  Specify a comma separated list of survey ids to filter by. For a list
  of surveys use
  `dhs_surveys(returnFields=c("SurveyId","SurveyYearLabel", "SurveyType","CountryName"))`

- surveyYear:

  Specify a comma separated list of survey years to filter by.

- surveyYearStart:

  Specify a range of Survey Years to filter Tags on. surveyYearStart is
  an inclusive value. Can be used alone or in conjunction with
  surveyYearEnd.

- surveyYearEnd:

  Specify a range of Survey Years to filter Tags on. surveyYearEnd is an
  inclusive value. Can be used alone or in conjunction with
  surveyYearStart.

- surveyType:

  Specify a survey type to filter by.

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

Returns a `data.table` of 4 (or less if `returnFields` is provided) tags
with detailed information. An indicators can be tagged with one or more
tags to help identify certain topics an indicator can be identified by.
A description of the attributes returned is provided at
<https://api.dhsprogram.com/rest/dhs/tags/fields>

## Examples

``` r

if (FALSE) { # \dontrun{
# A good use for the tags API endpoint is to query what the
# IDs are for each tag. These are useful for passing as
# arguments to other API endpoints.For example to show all the ids:

dat <- dhs_tags()

# Or if your analysis is foucssed on a particular country, and you want to
# see all the characteristics surveyed for e.g. Senegal

dat <- dhs_tags(countryIds="SN")

# A complete list of examples for how each argument to the survey
# tags API endpoint can be provided is given below, which is a
# copy of each of the examples listed in the API at:

# https://api.dhsprogram.com/#/api-tags.cfm


dat <- dhs_tags(countryIds="EG",all_results=FALSE)
dat <- dhs_tags(indicatorIds="FE_FRTR_W_TFR",all_results=FALSE)
dat <- dhs_tags(surveyIds="SN2010DHS",all_results=FALSE)
dat <- dhs_tags(surveyYear="2010",all_results=FALSE)
dat <- dhs_tags(surveyYearStart="2006",all_results=FALSE)
dat <- dhs_tags(surveyYearStart="1991", surveyYearEnd="2006",
all_results=FALSE)
dat <- dhs_tags(surveyType="DHS",all_results=FALSE)
dat <- dhs_tags(f="html",all_results=FALSE)
} # }
```
