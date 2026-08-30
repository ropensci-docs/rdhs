# read in dhs standard file types

read in dhs standard file types

## Usage

``` r
read_dhs_dataset(file, dataset, reformat = FALSE, all_lower = TRUE, ...)
```

## Arguments

- file:

  path to zip file to be read

- dataset:

  row from
  [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md)
  that corresponds to the file

- reformat:

  boolean detailing if datasets should be nicely reformatted. Default =
  \`FALSE\`

- all_lower:

  Logical indicating whether all value labels should be lower case.
  Default to \`TRUE\`.

- ...:

  Extra arguments to be passed to either
  [`read_dhs_dta`](https://docs.ropensci.org/rdhs/reference/read_dhs_dta.md)
  or
  [`read_dhs_flat`](https://docs.ropensci.org/rdhs/reference/read_dhs_flat.md)
