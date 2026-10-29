# API request of DHS Surveys

API request of DHS Surveys

## Usage

``` r
dhs_surveys(
  countryIds = NULL,
  indicatorIds = NULL,
  selectSurveys = NULL,
  surveyIds = NULL,
  surveyYear = NULL,
  surveyYearStart = NULL,
  surveyYearEnd = NULL,
  surveyType = NULL,
  surveyStatus = NULL,
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

  Specify a range of Survey Years to filter Surveys on. surveyYearStart
  is an inclusive value. Can be used alone or in conjunction with
  surveyYearEnd.

- surveyYearEnd:

  Specify a range of Survey Years to filter Surveys on. surveyYearEnd is
  an inclusive value. Can be used alone or in conjunction with
  surveyYearStart.

- surveyType:

  Specify a survey type to filter by.

- surveyStatus:

  Every survey is assigned a surveys status and can be queried based on
  the surveyStatus parameter. \`surveyStatus="available"\` (default)
  provides a list of all surveys for which the DHS API contains
  Indicator Data. \`surveyStatus="Completed"\` provides a list of all
  completed surveys. NOTE: Data may not be available for every completed
  survey. \`surveyStatus="Ongoing"\` provides a list of all ongoing
  surveys. \`surveyStatus="all"\` provides a list of all surveys.

- surveyCharacteristicIds:

  Specify a survey characteristic id to filter surveys with the
  specified survey characteristic. For a list of survey characteristics
  use
  `dhs_surveys(returnFields=c("SurveyId", "SurveyYearLabel","SurveyType","CountryName"))`

- tagIds:

  Specify a tag id to filter surveys containing indicators with the
  specified tag. For a list of tags use
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

Returns a `data.table` of 28 (or less if `returnFields` is provided)
surveys with detailed information for each survey. A detailed
description of all the attributes returned is provided at
<https://api.dhsprogram.com/rest/dhs/surveys/fields>

## Examples

``` r

if (FALSE) { # \dontrun{
# A common use for the surveys API endpoint is to query which countries
# have conducted surveys since a given year, e.g. since 2010

dat <- dhs_surveys(surveyYearStart="2010")

# Additionally, some countries conduct non DHS surveys, but the data for
# thse is also available within the DHS website/API. To query these:

dat <- dhs_surveys(surveyType="MIS")

# Lastly, you may be interested to know about anything peculiar about a
# particular survey's implementation. This can be found by looking within
# the footnotes variable within the data frame returned. For example, the
# Madagascar 2013 MIS:

dat$Footnotes[dat$SurveyId == "MD2013MIS"]

# A complete list of examples for how each argument to the surveys API
# endpoint can be provided is given below, which is a copy of each of
# the examples listed in the API at:

# https://api.dhsprogram.com/#/api-surveys.cfm


dat <- dhs_surveys(countryIds="EG",all_results=FALSE)
dat <- dhs_surveys(indicatorIds="FE_FRTR_W_TFR",all_results=FALSE)
dat <- dhs_surveys(selectSurveys="latest",all_results=FALSE)
dat <- dhs_surveys(surveyIds="SN2010DHS",all_results=FALSE)
dat <- dhs_surveys(surveyYear="2010",all_results=FALSE)
dat <- dhs_surveys(surveyYearStart="2006",all_results=FALSE)
dat <- dhs_surveys(surveyYearStart="1991", surveyYearEnd="2006",
all_results=FALSE)
dat <- dhs_surveys(surveyType="DHS",all_results=FALSE)
dat <- dhs_surveys(surveyStatus="Surveys",all_results=FALSE)
dat <- dhs_surveys(surveyStatus="Completed",all_results=FALSE)
dat <- dhs_surveys(surveyStatus="Ongoing",all_results=FALSE)
dat <- dhs_surveys(surveyStatus="All",all_results=FALSE)
dat <- dhs_surveys(surveyCharacteristicIds="32",all_results=FALSE)
dat <- dhs_surveys(tagIds="1",all_results=FALSE)
dat <- dhs_surveys(f="html",all_results=FALSE)
} # }
```
