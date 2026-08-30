# Create a data frame of datasets that your log in can download

Download datasets specified using output of `available_datasets`.

## Usage

``` r
download_datasets(
  config,
  desired_dataset,
  download_option = "both",
  reformat = TRUE,
  all_lower = TRUE,
  output_dir_root = NULL,
  ...
)
```

## Arguments

- config:

  Object of class \`rdhs_config\` as produced by \`read_rdhs_config\`
  that must contain a valid \`email\`, \`project\` and \`password\`.

- desired_dataset:

  Row from `available_datasets`

- download_option:

  Character dictating how the survey is stored when downloaded. Must be
  one of:

  - "zip" - Just the zip. "z", "i", "p" or "zip" will match

  - "rds" - Just the read in and saved rds. "r", "d", "s" or "rdhs" will
    match

  - "both" - Both the rds and extract. "b", "o", "t", "h" or "both" will
    match

- reformat:

  Boolean detailing whether dataset rds should be reformatted for ease
  of use later. Default = TRUE

- all_lower:

  Logical indicating whether all value labels should be lower case.
  Default to \`TRUE\`.

- output_dir_root:

  Directory where files are to be downloaded to

- ...:

  Any other arguments to be passed to
  [`read_dhs_dataset`](https://docs.ropensci.org/rdhs/reference/read_dhs_dataset.md)
