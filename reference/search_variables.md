# Search Survey Variables

Searches across datasets specified for requested survey variables. This
function (or
[`search_variable_labels`](https://docs.ropensci.org/rdhs/reference/search_variable_labels.md))
should be used to provide the \`questions\` argument for
[`extract_dhs`](https://docs.ropensci.org/rdhs/reference/extract_dhs.md).

## Usage

``` r
search_variables(dataset_filenames, variables, essential_variables = NULL, ...)
```

## Arguments

- dataset_filenames:

  The desired filenames to be downloaded. These can be found as one of
  the returned fields from
  [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md).

- variables:

  Character vector of survey variables to be looked up

- essential_variables:

  Character vector of variables that need to present. If any of the
  codes are not present in that survey, the survey will not be returned
  by this function. Default = \`NULL\`.

- ...:

  Any other arguments to be passed to
  [`download_datasets`](https://docs.ropensci.org/rdhs/reference/download_datasets.md)

## Value

A `data.frame` of the surveys where matches were found and then all the
resultant codes and descriptions.

## Details

Use this function after
[`get_datasets`](https://docs.ropensci.org/rdhs/reference/get_datasets.md)
to look up all the survey variables that have the required variable.

## Examples

``` r
if (FALSE) { # \dontrun{
# get the model datasets included with the package
model_datasets <- model_datasets

# download two of them
g <- get_datasets(dataset_filenames = model_datasets$FileName[1:2])

# and now seearch within these for survey variables
search_variables(
dataset_filenames = names(g), variables = c("v002","v102","ml13"),
)

# if we specify an essential variable then that dataset has to have that
# variable or else no variables will be returned for that datasets
search_variables(
dataset_filenames = names(g),
variables = c("v002","v102","ml13"),
essential_variables = "ml13"
)
} # }
```
