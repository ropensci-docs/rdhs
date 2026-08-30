# Archived dataset capable as_factor

Changes in \`haven\` have meant that \`labelled\` class are now referred
to as \`haven_labelled\` classes. If \`haven::as_factor\` is used on old
datasets they will fail to find the suitable method.
rdhs::as_factor.labelled will work on old archived datasets that have a
\`labelled\` class.

## Usage

``` r
as_factor.labelled(
  x,
  levels = c("default", "labels", "values", "both"),
  ordered = FALSE,
  ...
)
```

## Arguments

- x:

  Object to coerce to a factor.

- levels:

  How to create the levels of the generated factor:

  - "default": uses labels where available, otherwise the values. Labels
    are sorted by value.

  - "both": like "default", but pastes together the level and value

  - "label": use only the labels; unlabelled values become `NA`

  - "values: use only the values

- ordered:

  If `TRUE` create an ordered (ordinal) factor, if `FALSE` (the default)
  create a regular (nominal) factor.

- ...:

  Other arguments passed down to method.

## Details

For more details see
[`haven::as_factor`](https://forcats.tidyverse.org/reference/as_factor.html)

## Examples

``` r
if (FALSE) { # \dontrun{
# create a data.frame using the new haven_labelled class
df1 <- data.frame(
area = haven::labelled(c(1L, 2L, 3L), c("reg 1"=1,"reg 2"=2,"reg 3"=3)),
climate = haven::labelled(c(0L, 1L, 1L), c("cold"=0,"hot"=1))
)

# manually change it to the old style
class(df1$area) <- "labelled"
class(df1$climate) <- "labelled"

# with rdhs attached, i.e. library(rdhs), we can now do the following
haven::as_factor(df1$area)

# we can also use this on the data.frame by using the only_labelled argument
haven::as_factor(df1, only_labelled = TRUE)
} # }
```
