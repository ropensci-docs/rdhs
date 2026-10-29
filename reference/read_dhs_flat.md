# Read DHS flat file data set

This function reads a DHS recode dataset from the zipped flat file
dataset.

## Usage

``` r
read_dhs_flat(zfile, all_lower = TRUE, meta_source = NULL)
```

## Arguments

- zfile:

  Path to \`.zip\` file containing flat file dataset, usually ending in
  filename \`XXXXXXFL.zip\`

- all_lower:

  Logical indicating whether all value labels should be lower case.
  Default to \`TRUE\`.

- meta_source:

  character string indicating metadata source file for data dictionary.
  Default `NULL` first tried to use `.DCF` and then `.SPS` if not found.

## Value

A data frame. Value labels for each variable are stored as the
\`labelled\` class from \`haven\`.

## See also

[`labelled`](https://haven.tidyverse.org/reference/labelled.html),
[`read_dhs_dta`](https://docs.ropensci.org/rdhs/reference/read_dhs_dta.md).

For more information on the DHS filetypes and contents of distributed
dataset .ZIP files, see
<https://dhsprogram.com/data/File-Types-and-Names.cfm#CP_JUMP_10334>.

## Examples

``` r
mrfl_zip <- tempfile()
download.file("https://dhsprogram.com/data/model_data/dhs/zzmr61fl.zip",
              mrfl_zip,mode="wb")

mr <- rdhs:::read_dhs_flat(mrfl_zip)
attr(mr$mv213, "label")
#> [1] "Partner currently pregnant"
class(mr$mv213)
#> [1] "haven_labelled" "vctrs_vctr"     "integer"       
head(mr$mv213)
#> <labelled<integer>[6]>: Partner currently pregnant
#> [1] NA  0  0 NA  0 NA
#> 
#> Labels:
#>  value   label
#>      0      no
#>      1     yes
#>      8  unsure
#>      9 missing
table(mr$mv213)
#> 
#>    0    1    8    9 
#> 1766  239   57   13 
table(haven::as_factor(mr$mv213))
#> 
#>      no     yes  unsure missing 
#>    1766     239      57      13 
```
