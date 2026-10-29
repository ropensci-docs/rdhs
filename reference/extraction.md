# DHS survey questions extracted from datasets

Create a list of survey responses extracted using output of
`R6_client_dhs$public_methods$survey_questions`

## Usage

``` r
extraction(questions, available_datasets, geo_surveys, add_geo = FALSE)
```

## Arguments

- questions:

  Output of `R6_client_dhs$public_methods$survey_questions`

- available_datasets:

  Datasets that could be available. Output of
  `R6_client_dhs$public_methods$available_datasets`

- geo_surveys:

  Geographic Data Survey file paths.

- add_geo:

  Boolean detailing if geographic datasets should be added.

## Value

Returns \`data.frame\` with variables corresponding to the requested
variables in the questions object. Will also have geographic data
related columns if \`add_geo=TRUE\` is set. Lastly a SurveyId variable
will also be appended corresponding to
[`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md)\$SurveyId
