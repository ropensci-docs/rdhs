# DHS Website Authentication

Authenticate Users for DHS website

## Usage

``` r
authenticate_dhs(config)
```

## Arguments

- config:

  Object of class \`rdhs_config\` as produced by \`read_rdhs_config\`
  that must contain a valid \`email\`, \`project\` and \`password\`.

## Value

Returns list of length 3:

- user_name: your email usually

- user_pass: your password you provided

- proj_id: your project number

## Details

If the user has more than one project that contains the first 30
characters of the provided project they will be prompted to choose which
project they want. This choice will be saved so they do not have to
enter it again in this R session.

## Note

Credit for some of the function to
<https://github.com/ajdamico/lodown/blob/master/R/dhs.R>
