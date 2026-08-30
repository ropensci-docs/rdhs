# convert labelled data frame to data frame of just characters

convert labelled data frame to data frame of just characters

## Usage

``` r
delabel_df(df)
```

## Arguments

- df:

  data frame to convert labelled elements of. Likely this will be the
  output of
  [`extract_dhs`](https://docs.ropensci.org/rdhs/reference/extract_dhs.md).

## Value

A data frame of de-labelled elements

## Examples

``` r
df1 <- data.frame(
area = haven::labelled(c(1L, 2L, 3L), c("reg 1"=1,"reg 2"=2,"reg 3"=3)),
climate = haven::labelled(c(0L, 1L, 1L), c("cold"=0,"hot"=1))
)

df_char <- delabel_df(df = df1)
```
