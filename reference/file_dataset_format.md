# Returns what the dataset file ending should be for a given filename

Returns what the dataset file ending should be for a given filename

## Usage

``` r
file_dataset_format(file_format)
```

## Arguments

- file_format:

  FileFormat for a file as taken from the API, e.g.
  `dhs_datasets(returnFields = "FileFormat")`

## Value

One of "dat","dat","sas7bdat","sav" or "dta"

## Examples

``` r
file_format <- "Stata dataset (.dta)"
identical(rdhs:::file_dataset_format(file_format),"dta")
#> [1] TRUE
```
