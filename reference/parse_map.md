# Create dictionary from DHS .MAP codebook

Create dictionary from DHS .MAP codebook

## Usage

``` r
parse_map(map, all_lower = TRUE)
```

## Arguments

- map:

  A character vector containing .MAP file, e.g. from \`readLines()\`.

- all_lower:

  Logical indicating whether all value labels should be converted to
  lower case

## Value

A data frame containing metadata, principally variable labels and a
vector of value labels.

## Details

Currently hardcoded for 111 char width .MAP files, which covers the vast
majority of DHS Phase V, VI, and VIII. To be extended in the future and
perhaps add other useful options.

## Examples

``` r
mrdt_zip <- tempfile()
download.file("https://dhsprogram.com/data/model_data/dhs/zzmr61fl.zip",
              mrdt_zip, mode="wb")

map <- rdhs::read_zipdata(mrdt_zip, "\\.MAP", readLines)
dct <- rdhs:::parse_map(map)
```
