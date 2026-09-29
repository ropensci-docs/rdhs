# API request of DHS Countries

API request of DHS Countries

## Usage

``` r
dhs_countries(
  countryIds = NULL,
  indicatorIds = NULL,
  surveyIds = NULL,
  surveyYear = NULL,
  surveyYearStart = NULL,
  surveyYearEnd = NULL,
  surveyType = NULL,
  surveyCharacteristicIds = NULL,
  tagIds = NULL,
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
  `dhs_surveys(returnFields=c("SurveyId", "SurveyYearLabel","SurveyType","CountryName"))`

- surveyYear:

  Specify a comma separated list of survey years to filter by.

- surveyYearStart:

  Specify a range of Survey Years to filter Countries on.
  surveyYearStart is an inclusive value. Can be used alone or in
  conjunction with surveyYearEnd.

- surveyYearEnd:

  Specify a range of Survey Years to filter Countries on. surveyYearEnd
  is an inclusive value. Can be used alone or in conjunction with
  surveyYearStart.

- surveyType:

  Specify a survey type to filter by.

- surveyCharacteristicIds:

  Specify a survey characteristic id to filter countries in surveys with
  the specified survey characteristic. For a list of survey
  characteristics use
  `dhs_surveys(returnFields=c("SurveyId","SurveyYearLabel", "SurveyType","CountryName"))`

- tagIds:

  Specify a tag id to filter countries with surveys containing
  indicators with the specified tag. For a list of tags use
  [`dhs_tags()`](https://docs.ropensci.org/rdhs/reference/dhs_tags.md)

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

Returns a `data.table` of 12 (or less if `returnFields` is provided)
countries with their corresponding details. A detailed description of
all the attributes returned is provided at
<https://api.dhsprogram.com/rest/dhs/countries/fields>

## Examples

``` r

if (FALSE) { # \dontrun{
# A common use for the countries API endpoint is to query which countries
# ask questions about a given topic. For example to find all countries that
# record data on malaria prevalence by RDT:

dat <- dhs_countries(indicatorIds = "ML_PMAL_C_RDT")

# Additionally you may want to know all the countries that have conducted
# MIS (malaria indicator surveys):

dat <- dhs_countries(surveyType="MIS")

# A complete list of examples for how each argument to the countries API
# endpoint can be provided is given below, which is a copy of each of
# the examples listed in the API at:

# https://api.dhsprogram.com/#/api-countries.cfm


dat <- dhs_countries(countryIds="EG",all_results=FALSE)
dat <- dhs_countries(indicatorIds="FE_FRTR_W_TFR",all_results=FALSE)
dat <- dhs_countries(surveyIds="SN2010DHS",all_results=FALSE)
dat <- dhs_countries(surveyYear="2010",all_results=FALSE)
dat <- dhs_countries(surveyYearStart="2006",all_results=FALSE)
dat <- dhs_countries(surveyYearStart="1991", surveyYearEnd="2006",
all_results=FALSE)
dat <- dhs_countries(surveyType="DHS",all_results=FALSE)
dat <- dhs_countries(surveyCharacteristicIds="32",all_results=FALSE)
dat <- dhs_countries(tagIds="1",all_results=FALSE)
dat <- dhs_countries(f="html",all_results=FALSE)
} # }
```
