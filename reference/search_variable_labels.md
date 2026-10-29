# Search Survey Variable Definitions

Searches across datasets specified for requested survey variable
definitions. This function (or `search_variable_labels`) should be used
to provide the \`questions\` argument for
[`extract_dhs`](https://docs.ropensci.org/rdhs/reference/extract_dhs.md).

## Usage

``` r
search_variable_labels(
  dataset_filenames,
  search_terms = NULL,
  essential_terms = NULL,
  regex = NULL,
  ...
)
```

## Arguments

- dataset_filenames:

  The desired filenames to be downloaded. These can be found as one of
  the returned fields from
  [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md).

- search_terms:

  Character vector of search terms. If any of these terms are found
  within the survey question definitions, the corresponding survey
  variable and definitions will be returned.

- essential_terms:

  Character pattern that has to be in the definitions of survey question
  definitions. I.e. the function will first find all survey variable
  definitions that contain your \`search_terms\` (or regex) OR
  \`essential_terms\`. It will then remove any questions that did not
  contain your \`essential_terms\`. Default = \`NULL\`.

- regex:

  Regex character pattern for matching. If you want to specify your
  regex search pattern, then specify this argument. N.B. If both
  \`search_terms\` and \`regex“ are supplied as arguments then regex
  will be ignored.

- ...:

  Any other arguments to be passed to
  [`download_datasets`](https://docs.ropensci.org/rdhs/reference/download_datasets.md)

## Value

A `data.frame` of the surveys where matches were found and then all the
resultant codes and descriptions.

## Details

Use this function after
[`get_datasets`](https://docs.ropensci.org/rdhs/reference/get_datasets.md)
to query downloaded datasets for what survey questions they asked. This
function will look for your downloaded and imported survey datasets from
your cached files, and will download them if not downloaded.

## Examples

``` r
if (FALSE) { # \dontrun{
# get the model datasets included with the package
model_datasets <- model_datasets

# download two of them
g <- get_datasets(dataset_filenames = model_datasets$FileName[1:2])

# and now seearch within these for survey variable labels of interest
vars <- search_variable_labels(
dataset_filenames = names(g), search_terms = "fever"
)

head(vars)

# if we specify an essential term then no results will be returned from
# a dataset if it does not have any results from the search with this term
search_variable_labels(
dataset_filenames = names(g),
search_terms = "fever",
essential_terms = "primaquine",
)

# we can also use regex queries if we prefer, by passing `regex = TRUE`
vars <- search_variable_labels(
dataset_filenames = names(g), search_terms = "fever|net", regex = TRUE
)
} # }
```
