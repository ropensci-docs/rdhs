# API request of DHS Survey Characteristics

API request of DHS Survey Characteristics

## Usage

``` r
dhs_survey_characteristics(
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

  Specify a range of Survey Years to filter Survey Characteristics on.
  surveyYearStart is an inclusive value. Can be used alone or in
  conjunction with surveyYearEnd.

- surveyYearEnd:

  Specify a range of Survey Years to filter Survey Characteristics on.
  surveyYearEnd is an inclusive value. Can be used alone or in
  conjunction with surveyYearStart.

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

Returns a `data.table` of 2 (or less if `returnFields` is provided)
survey characteristics. A survey can be labelled with one or more of
these survey characteristics. A description of all the attributes
returned is provided at
<https://api.dhsprogram.com/rest/dhs/surveycharacteristics/fields>

## Examples

``` r

if (FALSE) { # \dontrun{
# A good use for the survey characteristics API endpoint is to query what the
# IDs are for each survey characteristic. These are useful for passing as
# arguments to other API endpoints.For example to show all the ids:

dat <- dhs_survey_characteristics()

# Or if your analysis is foucssed on a particular country, and you want to
# see all the characteristics surveyed for e.g. Senegal

dat <- dhs_countries(countryIds="SN")

# A complete list of examples for how each argument to the survey
# characteristics API endpoint can be provided is given below, which is a
# copy of each of the examples listed in the API at:

# https://api.dhsprogram.com/#/api-surveycharacteristics.cfm


dat <- dhs_survey_characteristics(countryIds="EG",all_results=FALSE)
dat <- dhs_survey_characteristics(indicatorIds="FE_FRTR_W_TFR",
all_results=FALSE)
dat <- dhs_survey_characteristics(surveyIds="SN2010DHS,all_results=FALSE")
dat <- dhs_survey_characteristics(surveyYear="2010,all_results=FALSE")
dat <- dhs_survey_characteristics(surveyYearStart="2006",all_results=FALSE)
dat <- dhs_survey_characteristics(surveyYearStart="1991",
surveyYearEnd="2006",all_results=FALSE)
dat <- dhs_survey_characteristics(surveyType="DHS",all_results=FALSE)
dat <- dhs_survey_characteristics(f="html",all_results=FALSE)
} # }
```
