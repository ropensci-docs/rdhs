# Package index

## Query DHS API

Functions for interacting with each of the DHS API endpoints. They all
start ‘dhs\_’ for simplicity.

- [`dhs_countries()`](https://docs.ropensci.org/rdhs/reference/dhs_countries.md)
  : API request of DHS Countries
- [`dhs_data()`](https://docs.ropensci.org/rdhs/reference/dhs_data.md) :
  API request of DHS Indicator Data
- [`dhs_data_updates()`](https://docs.ropensci.org/rdhs/reference/dhs_data_updates.md)
  : API request of DHS Data Updates
- [`dhs_datasets()`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md)
  : API request of DHS Datasets
- [`dhs_geometry()`](https://docs.ropensci.org/rdhs/reference/dhs_geometry.md)
  : API request of DHS Geometry
- [`dhs_indicators()`](https://docs.ropensci.org/rdhs/reference/dhs_indicators.md)
  : API request of DHS Indicators
- [`dhs_info()`](https://docs.ropensci.org/rdhs/reference/dhs_info.md) :
  API request of DHS Info
- [`dhs_publications()`](https://docs.ropensci.org/rdhs/reference/dhs_publications.md)
  : API request of DHS Publications
- [`dhs_survey_characteristics()`](https://docs.ropensci.org/rdhs/reference/dhs_survey_characteristics.md)
  : API request of DHS Survey Characteristics
- [`dhs_surveys()`](https://docs.ropensci.org/rdhs/reference/dhs_surveys.md)
  : API request of DHS Surveys
- [`dhs_tags()`](https://docs.ropensci.org/rdhs/reference/dhs_tags.md) :
  API request of DHS Tags
- [`dhs_ui_updates()`](https://docs.ropensci.org/rdhs/reference/dhs_ui_updates.md)
  : API request of DHS UI Updates

## Set up DHS login credentials

“Set our credentials for logging into the DHS website. This creates in
the backend a rdhs client for downloading datasets, querying survey
variables and extracting data.”

- [`set_rdhs_config()`](https://docs.ropensci.org/rdhs/reference/set_rdhs_config.md)
  : Set rdhs config
- [`get_rdhs_config()`](https://docs.ropensci.org/rdhs/reference/get_rdhs_config.md)
  : Get rdhs config
- [`update_rdhs_config()`](https://docs.ropensci.org/rdhs/reference/update_rdhs_config.md)
  : Update your current rdhs config
- [`client_dhs()`](https://docs.ropensci.org/rdhs/reference/client_dhs.md)
  : Make a dhs client

## User Interface

Functions to download, search and interact with downloaded datasets

- [`extract_dhs()`](https://docs.ropensci.org/rdhs/reference/extract_dhs.md)
  : Extract Data
- [`get_available_datasets()`](https://docs.ropensci.org/rdhs/reference/get_available_datasets.md)
  : Get Available Datasets
- [`get_datasets()`](https://docs.ropensci.org/rdhs/reference/get_datasets.md)
  : Get Datasets
- [`get_downloaded_datasets()`](https://docs.ropensci.org/rdhs/reference/get_downloaded_datasets.md)
  : Get Downloaded Datasets
- [`search_variables()`](https://docs.ropensci.org/rdhs/reference/search_variables.md)
  : Search Survey Variables
- [`search_variable_labels()`](https://docs.ropensci.org/rdhs/reference/search_variable_labels.md)
  : Search Survey Variable Definitions
- [`download_boundaries()`](https://docs.ropensci.org/rdhs/reference/download_boundaries.md)
  : DHS Spatial Boundaries

## Downstream Dataset Helper Functions

Tools to help combine extracted datasets, as well as extract and apend
dataset variable names and definitions

- [`rbind_labelled()`](https://docs.ropensci.org/rdhs/reference/rbind_labelled.md)
  : Combine data frames with columns of class \`labelled\`
- [`get_variable_labels()`](https://docs.ropensci.org/rdhs/reference/get_variable_labels.md)
  : Get Survey Variable Labels
- [`data_and_labels()`](https://docs.ropensci.org/rdhs/reference/data_and_labels.md)
  : Create list of dataset and its variable names
- [`delabel_df()`](https://docs.ropensci.org/rdhs/reference/delabel_df.md)
  : convert labelled data frame to data frame of just characters

## DHS Dataset Parsers

Custom built parsers for handling flat ASCII and stata DHS datasets

- [`read_dhs_flat()`](https://docs.ropensci.org/rdhs/reference/read_dhs_flat.md)
  : Read DHS flat file data set
- [`parse_dcf()`](https://docs.ropensci.org/rdhs/reference/parse_meta.md)
  [`parse_sps()`](https://docs.ropensci.org/rdhs/reference/parse_meta.md)
  [`parse_do()`](https://docs.ropensci.org/rdhs/reference/parse_meta.md)
  : Parse fixed-width file metadata
- [`read_dhs_dta()`](https://docs.ropensci.org/rdhs/reference/read_dhs_dta.md)
  : Read DHS Stata data set
