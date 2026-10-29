# Combine data frames with columns of class \`labelled\`

Combine data frames with columns of class \`labelled\`

## Usage

``` r
rbind_labelled(..., labels = NULL, warn = TRUE)
```

## Arguments

- ...:

  data frames to bind together, potentially with columns of class
  "labelled". The first argument can be a list of data frames, similar
  to \`plyr::rbind.fill\`.

- labels:

  A named list providing vectors of value labels or describing how to
  handle columns of class \`labelled\`. See details for usage.

- warn:

  Logical indicating to warn if combining variables with different value
  labels. Defaults to TRUE.

## Value

A data frame.

## Details

The argument \`labels\` provides options for how to handle binding of
columns of class \`labelled\`. Typical use is to provide a named list
with elements for each labelled column. Elements of the list are either
a vector of labels that should be applied to the column or the character
string "concatenated", which indicates that labels should be
concatenated such that all unique labels are distinct values in the
combined vector. This is accomplished by converting to character
strings, binding, and then casting back to labelled. For labelled
columns for which labels are not provided in the \`label\` argument, the
default behaviour is that the labels from the first data frame with
labels for that column are inherited by the combined data.

See examples.

## Examples

``` r
df1 <- data.frame(
area = haven::labelled(c(1L, 2L, 3L), c("reg 1"=1,"reg 2"=2,"reg 3"=3)),
climate = haven::labelled(c(0L, 1L, 1L), c("cold"=0,"hot"=1))
)
df2 <- data.frame(
area    = haven::labelled(c(1L, 2L), c("reg A"=1, "reg B"=2)),
climate = haven::labelled(c(1L, 0L), c("cold"=0, "warm"=1))
)

# Default: all data frames inherit labels from first df. Incorrect if
# "reg 1" and "reg A" are from different countries, for example.
dfA <- rbind_labelled(df1, df2)
#> Warning: Some variables have non-matching value labels: area, climate.
#> Inheriting labels from first data frame with labels.
haven::as_factor(dfA)
#>    area climate
#> 1 reg 1    cold
#> 2 reg 2     hot
#> 3 reg 3     hot
#> 4 reg 1     hot
#> 5 reg 2    cold

# Concatenate value labels for "area". Regions are coded separately,
# and original integer values are lost (by necessity of more levels now).
# For "climate", codes "1 = hot" and "1 = warm", are coded as the same
# outcome, inheriting "1 = hot" from df1 by default.
dfB <- rbind_labelled(df1, df2, labels=list(area = "concatenate"))
#> Warning: Some variables have non-matching value labels: climate.
#> Inheriting labels from first data frame with labels.
dfB
#>   area climate
#> 1    1       0
#> 2    2       1
#> 3    3       1
#> 4    4       1
#> 5    5       0
haven::as_factor(dfB)
#>    area climate
#> 1 reg 1    cold
#> 2 reg 2     hot
#> 3 reg 3     hot
#> 4 reg A     hot
#> 5 reg B    cold

# We can specify to code as "1=warm/hot" rather than inheriting "hot".
dfC <- rbind_labelled(df1, df2,
labels=list(area = "concatenate", climate = c("cold"=0, "warm/hot"=1)))

dfC$climate
#> <labelled<integer>[5]>
#> [1] 0 1 1 1 0
#> 
#> Labels:
#>  value    label
#>      0     cold
#>      1 warm/hot
haven::as_factor(dfC)
#>    area  climate
#> 1 reg 1     cold
#> 2 reg 2 warm/hot
#> 3 reg 3 warm/hot
#> 4 reg A warm/hot
#> 5 reg B     cold

# Or use `climate="concatenate"` to code "warm" and "hot" as different.
dfD <- rbind_labelled(df1, df2,
labels=list(area = "concatenate", climate="concatenate"))

dfD
#>   area climate
#> 1    1       1
#> 2    2       2
#> 3    3       2
#> 4    4       3
#> 5    5       1
haven::as_factor(dfD)
#>    area climate
#> 1 reg 1    cold
#> 2 reg 2     hot
#> 3 reg 3     hot
#> 4 reg A    warm
#> 5 reg B    cold
```
