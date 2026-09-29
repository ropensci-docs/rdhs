# Make a dhs client

Make a DHS API client

## Usage

``` r
client_dhs(config = NULL, root = rappdirs_rdhs(), api_key = NULL)
```

## Arguments

- config:

  config object, as created using `read_rdhs_config`

- root:

  Character for root directory to where client, caches, surveys etc.
  will be stored. Default = `rappdirs_rdhs()`

- api_key:

  Character for DHS API KEY. Default = NULL

## Methods

- `dhs_api_request`:

  Makes a call to the DHS websites API. You can make requests to any of
  their declared api endpoints (see `vignette(rdhs)` for more on these).
  API queries can be filtered by providing query terms, and you can
  control how many search results you want returned. The default
  parameters will return all of the results, and will format it nicely
  into a data.frame for you. N.B. This is easier to now do by using the
  bespoke functions that are included within the package. These take the
  form dhs\_\<endpoint\>, e.g.
  [`dhs_data`](https://docs.ropensci.org/rdhs/reference/dhs_data.md).
  These functions can also take your client as an argument that will
  cache the response for you

  *Usage:*
  `dhs_api_request(api_endpoint, query = list(), api_key = private$api_key, num_results = 100, just_results = TRUE)`

  *Arguments:*

  - `api_endpoint`: API endpoint. Must be one of the 12 possible
    endpoints.

  - `query`: List of query filters. To see possible query filter terms
    for each endpoint then head to the DHS api website.

  - `api_key`: DHS API key. Default will grab the key provided when the
    client was created.

  - `num_results`: The Number of results to return. Default = "ALL"
    which will loop through all the api search results pages for you if
    there are more results than their API will allow you to fetch in one
    page. If you specify a number this many results will be returned
    (but probably best to just leave default).

  - `just_results`: Boolean whether to return just the results or all
    the http API response. Default = TRUE (probably best again to leave
    as this.)

  *Value*: Data.frame with search results if just_results=TRUE,
  otherwise a nested list with all the API responses for each page
  required.

- `available_datasets`:

  Searches the DHS website for all the datasets that you can download.
  The results of this function are cached in the client. If you have
  recently requested new datasets from the DHS website then you can
  specify to clear the cache first so that you get the new set of
  datasets available to you.

  *Usage:* `available_datasets(clear_cache_first = FALSE)`

  *Arguments:*

  - `clear_cache_first`: Boolean detailing if you would like to clear
    the cached available datasets first. The default is set to FALSE.
    This option is available so that you can make sure your client
    fetches any new datasets that you have recently been given access
    to.

  *Value*: Data.frame object with 14 variables that detail the surveys
  you can download, their url download links and the country, survey,
  year etc info for that link.

- `get_datasets`:

  Gets datasets from your cache or downloads from the DHS website. By
  providing the filenames, as specified in one of the returned fields
  from
  [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md),
  the client will log in for you and download all the files you have
  requested. If any of the requested files are unavailable for your log
  in, these will be flagged up first as a message so you can make a note
  and request them through the DHS website. You also have the option to
  control whether the downloaded zip file is then extracted and
  converted into a more convenient R `data.frame`. This converted object
  will then be subsequently saved as a ".rds" object within the client
  root directory datasets folder, which can then be more quickly loaded
  when needed with `readRDS`. You also have the option to reformat the
  dataset, which will ensure that a suitable parser is used to preserve
  the meta information in your dataset, such as what different survey
  response codes mean.

  *Usage:*
  `get_datasets(dataset_filenames, download_option = "rds", reformat = FALSE, all_lower = TRUE, output_dir_root = file.path(private$root, "datasets"), clear_cache = FALSE, ...)`

  *Arguments:*

  - `dataset_filenames`: The desired filenames to be downloaded. These
    can be found as one of the returned fields from
    [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md).
    Alternatively you can also pass the desired rows from
    [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md).

  - `download_option`: Character specifying whether the dataset should
    be just downloaded ("zip"), imported and saved as an .rds object
    ("rds"), or both extract and rds ("both"). Conveniently you can just
    specify any letter from these options.

  - `reformat`: Boolean concerning whether to reformat read in datasets
    by removing all factors and labels. Default = FALSE.

  - `all_lower`: Logical indicating whether all value labels should be
    lower case. Default to \`TRUE\`.

  - `output_dir_root`: Root directory where the datasets will be stored
    within. The default will download datasets to a subfolder of the
    client root called "datasets"

  - `clear_cache`: Should your available datasets cache be cleared
    first. This will allow newly accessed datasets to be available.
    Default = \`TRUE\`

  - `...`: Any other arguments to be passed to
    [`read_dhs_dataset`](https://docs.ropensci.org/rdhs/reference/read_dhs_dataset.md)

  *Value*: Depends on the download_option requested, but ultimately it
  is a file path to where the dataset was downloaded to, so that you can
  interact with it accordingly.

- `survey_questions`:

  Use this function after download_survey to query downloaded surveys
  for what questions they asked. This function will look for the
  downloaded and imported survey datasets from the cache, and will
  download them if not previously downloaded.

  *Usage:*
  `survey_questions(dataset_filenames, search_terms = NULL, essential_terms = NULL, regex = NULL, rm_na = TRUE, ...)`

  *Arguments:*

  - `dataset_filenames`: The desired filenames to be downloaded. These
    can be found as one of the returned fields from
    [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md).

  - `search_terms`: Character vector of search terms. If any of these
    terms are found within the surveys question descriptions, the
    corresponding code and description will be returned.

  - `essential_terms`: Character pattern that has to be in the
    description of survey questions. I.e. the function will first find
    all survey_questions that contain your search terms (or regex) OR
    essential_terms. It will then remove any questions that did not
    contain your essential_terms. Default = NULL.

  - `regex`: Regex character pattern for matching. If you want to
    specify your regex search pattern, then specify this argument. N.B.
    If both search_terms and regex are supplied as arguments then regex
    will be ignored.

  - `rm_na`: Should NAs be removed. Default is \`TRUE\`

  - `...`: Any other arguments to be passed to
    [`download_datasets`](https://docs.ropensci.org/rdhs/reference/download_datasets.md)

  *Value*: Data frame of the surveys where matches were found and then
  all the resultant codes and descriptions.

- `survey_variables`:

  Use this function after download_survey to look up all the surveys
  that have the provided codes.

  *Usage:*
  `survey_variables(dataset_filenames, variables, essential_variables = NULL, rm_na = TRUE, ...)`

  *Arguments:*

  - `dataset_filenames`: The desired filenames to be downloaded. These
    can be found as one of the returned fields from
    [`dhs_datasets`](https://docs.ropensci.org/rdhs/reference/dhs_datasets.md).

  - `variables`: Character vector of survey variables to be looked up

  - `essential_variables`: Character vector of variables that need to
    present. If any of the codes are not present in that survey, the
    survey will not be returned by this function. Default = NULL.

  - `rm_na`: Should NAs be removed. Default is \`TRUE\`

  - `...`: Any other arguments to be passed to
    [`download_datasets`](https://docs.ropensci.org/rdhs/reference/download_datasets.md)

  *Value*: Data frame of the surveys where matches were found and then
  all the resultant codes and descriptions.

- `extract`:

  Function to extract datasets using a set of survey questions as taken
  from the output from `survey_questions`

  *Usage:* `extract(questions, add_geo = FALSE)`

  *Arguments:*

  - `questions`: Questions to be queried, in the format from
    `survey_questions`

  - `add_geo`: Add geographic information to the extract. Default = TRUE

- `get_variable_labels`:

  Returns information about a dataset's survey variables and
  definitions.

  *Usage:*
  `get_variable_labels(dataset_filenames = NULL, dataset_paths = NULL, rm_na = FALSE)`

  *Arguments:*

  - `dataset_filenames`: Vector of dataset filenames to look up

  - `dataset_paths`: Vector of dataset file paths to where datasets have
    been saved to

  - `rm_na`: Should variables and labels with NAs be removed. Default =
    FALSE

  *Value*: Data frame of survey variable names and definitions

- `get_cache_date`:

  Returns the private member variable cache-date, which is the date the
  client was last created/validated against the DHS API.

  *Usage:* `get_cache_date()`

  *Value*: POSIXct and POSIXt time

- `get_root`:

  Returns the file path to the client's root directory

  *Usage:* `get_root()`

  *Value*: Character string file path

- `get_config`:

  Returns the client's configuration

  *Usage:* `get_config()`

  *Value*: Config data.frame

- `get_downloaded_datasets`:

  Returns a named list of all downloaded datasets and their file paths

  *Usage:*
  [`get_downloaded_datasets()`](https://docs.ropensci.org/rdhs/reference/get_downloaded_datasets.md)

  *Value*: List of dataset names and file paths.

- `set_cache_date`:

  Sets the private member variable cache-date, which is the date the
  client was last created/validated against the DHS API. This should
  never really be needed but is included to demonstrate the cache
  clearing properties of the client in the vignette.

  *Usage:* `set_cache_date(date)`

  *Arguments:*

  - `date`: POSIXct and POSIXt time to update cache time to.

- `save_client`:

  Internally save the client object as an .rds file within the root
  directory for the client.

  *Usage:* `save_client()`

- `clear_namespace`:

  Clear the keys and values associated within a cache context. The dhs
  client caches a number of different tasks, and places these within
  specific contexts using the package
  [`storr::storr_rds`](https://richfitz.github.io/storr/reference/storr_rds.html).

  *Usage:* `clear_namespace(namespace)`

  *Arguments:*

  - `namespace`: Character string for the namespace to be cleared.

## Examples

``` r
if (FALSE) { # \dontrun{
# create an rdhs config file at "rdhs.json"
conf <- set_rdhs_config(
config_path = "rdhs.json",global = FALSE, prompt = FALSE
)
td <- tempdir()
cli <- rdhs::client_dhs(api_key = "DEMO_1234", config = conf, root = td)
} # }
```
