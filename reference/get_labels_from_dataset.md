# Return variable labels from a dataset

Returns variable labels stored as `"label"` attribute.

## Usage

``` r
get_labels_from_dataset(data, return_all = TRUE)
```

## Arguments

- data:

  A `data.frame` from which to extract variable labels.

- return_all:

  Logical whether to return all variables (`TRUE`) or only those with
  labels.

## Value

A `data.frame` consisting of the variable name and labels.
