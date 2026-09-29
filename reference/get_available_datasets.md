# Get Available Datasets

Details the datasets that your login credentials have access to

## Usage

``` r
get_available_datasets(clear_cache = FALSE)
```

## Arguments

- clear_cache:

  Boolean detailing if you would like to clear the cached available
  datasets first. The default is set to FALSE. This option is available
  so that you can make sure your client fetches any new datasets that
  you have recently been given access to.

## Value

A `data.frame` with 14 variables that detail the surveys you can
download, their url download links and the country, survey, year etc
info for that link.

## Details

Searches the DHS website for all the datasets that you can download. The
results of this function are cached in the client. If you have recently
requested new datasets from the DHS website then you can specify to
clear the cache first so that you get the new set of datasets available
to you. This function is used by
[`get_datasets`](https://docs.ropensci.org/rdhs/reference/get_datasets.md)
and should thus be used with \`clear_cache_first = TRUE\` before using
\`get_datasets\` if you have recently requested new datasets.

## Examples

``` r

if (FALSE) { # \dontrun{
# grab the datasets
datasets <- get_available_datasets()

# and if we look at the last one it will be the model datasets from DHS
tail(datasets, 1)
} # }
```
