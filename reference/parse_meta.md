# Parse fixed-width file metadata

Parse dataset metadata

## Usage

``` r
parse_dcf(dcf, all_lower = TRUE)

parse_sps(sps, all_lower = TRUE)

parse_do(do, dct, all_lower = TRUE)
```

## Arguments

- dcf:

  .DCF file path to parse

- all_lower:

  logical indicating whether to convert variable labels to lower case.
  Defaults to \`TRUE\`.

- sps:

  .SPS file as character vector (e.g. from readLines / brio::read_lines)

- do:

  .DO file as character vector (e.g. from readLines / brio::read_lines)

- dct:

  .DCT file as character vector (e.g. from readLines / brio::read_lines)

## Value

data.frame with metadata for parsing fixed-width flat file

## Examples

``` r
mrfl_zip <- tempfile()
download.file("https://dhsprogram.com/data/model_data/dhs/zzmr61fl.zip",
              mrfl_zip, mode = "wb")

dcf <- rdhs::read_zipdata(mrfl_zip, "\\.DCF", readLines)
dct <- rdhs:::parse_dcf(dcf)

sps <- rdhs::read_zipdata(mrfl_zip, "\\.SPS", readLines)
dct <- rdhs:::parse_sps(sps)

do <- rdhs::read_zipdata(mrfl_zip, "\\.DO", readLines)
dctin <- rdhs::read_zipdata(mrfl_zip, "\\.DCT", readLines)
dct <- rdhs:::parse_do(do, dctin)
```
