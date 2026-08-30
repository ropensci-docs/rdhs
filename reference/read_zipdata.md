# Read filetype from a zipped folder based on the file ending

Read filetype from a zipped folder based on the file ending

## Usage

``` r
read_zipdata(zfile, pattern = ".dta$", readfn = haven::read_dta, ...)
```

## Arguments

- zfile:

  Path to \`.zip\` file containing flat file dataset, usually ending in
  filename \`XXXXXXFL.zip\`

- pattern:

  String detailing which filetype is to be read from within the zip by
  means of a grep. Default = ".dta\$"

- readfn:

  Function object to be used for reading in the identified file within
  the zip. Default = \`haven::read_dta\`

- ...:

  additional arguments to readfn

## Examples

``` r
if (FALSE) { # \dontrun{
# get the model datasets included in the package
model_datasets <- model_datasets

# download just the zip
g <- get_datasets(
dataset_filenames = model_datasets$FileName[1],
download_option = "zip"
)

# and then read from the zip. This function is used internally by rdhs
# when using `get_datasets` with `download_option = .rds` (default)
r <- read_zipdata(
g[[1]], pattern = ".dta"
)

# and we can pass a function to read the file and any other args with ...
r <- read_zipdata(
g[[1]], pattern = ".dta", readfn = haven::read_dta, encoding = "UTF-8"
)
} # }
```
