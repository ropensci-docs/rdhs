# Get Downloaded Datasets

Detail the datasets that you have already downloaded

## Usage

``` r
get_downloaded_datasets()
```

## Value

A `data.frame` of downloaded datasets

## Details

Returns a `data.frame` of the datasets that have been downloaded within
this client. This could be useful if you are without an internet
connection and wish to know which saved dataset files in your root
directory correspond to which dataset

## Examples

``` r
if (FALSE) { # \dontrun{
# get the model datasets included with the package
model_datasets <- model_datasets

# download one of them
g <- get_datasets(dataset_filenames = model_datasets$FileName[1])

# these will then be stored so that we know what datasets we have downloaded
d <- get_downloaded_datasets()

# which returns a names list of file paths to the datasets
d[1]
} # }
```
