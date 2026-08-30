# API request of DHS Indicators

API request of DHS Indicators

## Usage

``` r
dhs_indicators(
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
  `dhs_surveys(returnFields=c("SurveyId","SurveyYearLabel", "SurveyType","CountryName"))`

- surveyYear:

  Specify a survey year to filter by.

- surveyYearStart:

  Specify a range of Survey Years to filter Indicators on.
  surveyYearStart is an inclusive value. Can be used alone or in
  conjunction with surveyYearEnd.

- surveyYearEnd:

  Specify a range of Survey Years to filter Indicators on. surveyYearEnd
  is an inclusive value. Can be used alone or in conjunction with
  surveyYearStart.

- surveyType:

  Specify a comma separated list of survey years to filter by.

- surveyCharacteristicIds:

  Specify a survey characteristic id to filter indicators in surveys
  with the specified survey characteristic. For a list of survey
  characteristics use
  `dhs_surveys(returnFields=c("SurveyId","SurveyYearLabel", "SurveyType","CountryName"))`

- tagIds:

  Specify a tag id to filter indicators with the specified tag. For a
  list of tags use
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

Returns a `data.table` of 18 (or less if `returnFields` is provided)
indicators with attributes for each indicator. A detailed description of
all the attributes returned is provided at
<https://api.dhsprogram.com/rest/dhs/indicators/fields>

## Examples

``` r
if (FALSE) { # \dontrun{
# A common use for the indicators data API will be to search for a list of
# health indicators within a given characteristic category, such as anemia
# testing, HIV prevalence, micronutrients etc. For example to return all the
# indicators relating to malaria testing by RDTs:

dat <- dhs_indicators(surveyCharacteristicIds="90")

# A list of the different `surveyCharacteristicIds` can be found
# [here](https://api.dhsprogram.com/rest/dhs/surveycharacteristics?f=html)

# A complete list of examples for how each argument to the indicator API
# endpoint can be provided is given below, which is a copy of each of
# the examples listed in the API at:

# https://api.dhsprogram.com/#/api-indicators.cfm


dat <- dhs_indicators(countryIds="EG",all_results=FALSE)
dat <- dhs_indicators(indicatorIds="FE_FRTR_W_TFR",all_results=FALSE)
dat <- dhs_indicators(surveyIds="SN2010DHS",all_results=FALSE)
dat <- dhs_indicators(surveyYear="2010",all_results=FALSE)
dat <- dhs_indicators(surveyYearStart="2006",all_results=FALSE)
dat <- dhs_indicators(surveyYearStart="1991", surveyYearEnd="2006",
all_results=FALSE)
dat <- dhs_indicators(surveyType="DHS",all_results=FALSE)
dat <- dhs_indicators(surveyCharacteristicIds="32",all_results=FALSE)
dat <- dhs_indicators(tagIds="1",all_results=FALSE)
dat <- dhs_indicators(f="html",all_results=FALSE)
} # }
```
