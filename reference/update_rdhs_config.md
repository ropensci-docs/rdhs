# Update your current rdhs config

`update_rdhs_config` allows you to update elements of your rdhs config,
without having to set it completely via `set_rdhs_config`. For each
config element, provide the new changes required. To update your
password, set `password = TRUE` and you will be asked securely for your
new password.

## Usage

``` r
update_rdhs_config(
  password = FALSE,
  email = NULL,
  project = NULL,
  cache_path = NULL,
  config_path = NULL,
  global = NULL,
  verbose_download = NULL,
  verbose_setup = NULL,
  timeout = NULL,
  data_frame = NULL,
  project_choice = NULL
)
```

## Arguments

- password:

  Logical for updating your password securely. Default = FALSE

- email:

  Character for email used to login to the DHS website.

- project:

  Character for the name of the DHS project from which datasets should
  be downloaded.

- cache_path:

  Character for directory path where datasets and API calls will be
  cached. If left bank, a suitable directory will be created within your
  user cache directory for your operating system (permission granting).

- config_path:

  Character for where the config file should be saved. For a global
  configuration, \`config_path\` must be '~/.rdhs.json'. For a local
  configuration, \`config_path\` must be 'rdhs.json'. If left bank, the
  config file will be stored within your user cache directory for your
  operating system (permission granting).

- global:

  Logical for the config_path to be interpreted as a global config path
  or a local one. Default = TRUE.

- verbose_download:

  Logical for dataset download progress bars to be shown. Default =
  FALSE.

- verbose_setup:

  Logical for rdhs setup and messages to be printed. Default = TRUE.

- timeout:

  Numeric for how long in seconds to wait for the DHS API to respond.
  Default = 30.

- data_frame:

  Function with which to convert API calls into. If left blank
  `data_frame` objects are returned. Must be passed as a character.
  Examples could be:
  [`data.table::as.data.table`](https://rdrr.io/pkg/data.table/man/as.data.table.html)
  [`tibble::as.tibble`](https://tibble.tidyverse.org/reference/deprecated.html)

- project_choice:

  Numeric for project choice. See `authenticate_dhs` for more info.
