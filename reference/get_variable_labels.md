# Get Survey Variable Labels

Return variable labels from a dataset

## Usage

``` r
get_variable_labels(dataset, return_all = TRUE)
```

## Arguments

- dataset:

  Can be either the file path to a dataset, the dataset as a
  \`data.frame\` or the filenames of datasets. See details for more
  information

- return_all:

  Logical whether to return all variables (`TRUE`) or only those with
  labels.

## Value

A `data.frame` consisting of the variable name and labels.

## Details

Returns variable names and their labels from a dataset. You can pass for
the \`data\` argument any of the following:

- The file path to a saved dataset. This would be the direct output of
  [`get_datasets`](https://docs.ropensci.org/rdhs/reference/get_datasets.md)

- A read in dataset, i.e. produced by using
  [`readRDS`](https://rdrr.io/r/base/readRDS.html) to load a dataset
  from a file path produced by
  [`get_datasets`](https://docs.ropensci.org/rdhs/reference/get_datasets.md)

- Dataset filenames. These can be found as one of the returned fields
  from
  [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md).
  If these datasets have not been downloaded before this will download
  them for you.

## Examples

``` r
if (FALSE) { # \dontrun{
# get the model datasets included with the package
model_datasets <- model_datasets

# download one of them
g <- get_datasets(dataset_filenames = model_datasets$FileName[1])

# we can pass the list of filepaths to the function
head(get_variable_labels(g))

# or we can pass the full dataset
r <- readRDS(g[[1]])
head(get_variable_labels(r))
} # }
```
