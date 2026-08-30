# Extract Data

Extracts data from your downloaded datasets according to a data.frame of
requested survey variables or survey definitions

## Usage

``` r
extract_dhs(questions, add_geo = FALSE)
```

## Arguments

- questions:

  Questions to be queried, in the format from
  [`search_variables`](https://docs.ropensci.org/rdhs/reference/search_variables.md)
  or
  [`search_variable_labels`](https://docs.ropensci.org/rdhs/reference/search_variable_labels.md)

- add_geo:

  Add geographic information to the extract. Defaut = \`TRUE\`

## Value

A `list` of \`data.frames\` for each survey data extracted.

## Details

Function to extract datasets using a set of survey questions as taken
from the output from
[`search_variables`](https://docs.ropensci.org/rdhs/reference/search_variables.md)
or
[`search_variable_labels`](https://docs.ropensci.org/rdhs/reference/search_variable_labels.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# get the model datasets included with the package
model_datasets <- model_datasets

# download one of them
g <- get_datasets(dataset_filenames = model_datasets$FileName[1])

# create some terms of data me may want to extrac
st <- search_variable_labels(names(g), "bed net")

# and now extract it
ex <- extract_dhs(st)
} # }
```
