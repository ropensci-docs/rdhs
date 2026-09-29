# unzip special that catches for 4GB+

unzip special that catches for 4GB+

## Usage

``` r
unzip_special(
  zipfile,
  files = NULL,
  overwrite = TRUE,
  junkpaths = FALSE,
  exdir = ".",
  unzip = "internal",
  setTimes = FALSE
)
```

## Arguments

- zipfile:

  The pathname of the zip file: tilde expansion (see
  [`path.expand`](https://rdrr.io/r/base/path.expand.html) will be
  performed.)

- files:

  A character vector of recorded filepaths to be extracted: the default
  is to extract all files.

- overwrite:

  If `TRUE`, overwrite existing files (the equivalent of `unzip -o`),
  otherwise ignore such files (the equivalent of `unzip -n`).

- junkpaths:

  If `TRUE`, use only the basename of the stored filepath when
  extracting. The equivalent of `unzip -j`.

- exdir:

  The directory to extract files to (the equivalent of `unzip -d`). It
  will be created if necessary.

- unzip:

  The method to be used. An alternative is to use `getOption("unzip")`,
  which on a Unix-alike may be set to the path to a `unzip` program.

- setTimes:

  logical. For the internal method only, should the file times be set
  based on the times in the zip file? (NB: this applies to included
  files, not to directories.)
