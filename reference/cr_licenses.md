# Search CrossRef licenses

Search CrossRef licenses

## Usage

``` r
cr_licenses(
  query = NULL,
  offset = NULL,
  limit = NULL,
  sort = NULL,
  order = NULL,
  .progress = "none",
  ...
)

cr_licenses_(
  query = NULL,
  offset = NULL,
  limit = NULL,
  sort = NULL,
  order = NULL,
  .progress = "none",
  parse = FALSE,
  ...
)
```

## Arguments

- query:

  Query terms

- offset:

  Number of record to start at, from 1 to infinity.

- limit:

  Number of results to return in the query. Not relavant when searching
  with specific dois. Default: 20. Max: 1000

- sort:

  Field to sort on. Acceptable set of fields to sort on:

  - `score` OR `relevance` - Sort by relevance score

  - `updated` - Sort by date of most recent change to metadata.
    Currently the same as deposited.

  - `deposited` - Sort by time of most recent deposit

  - `indexed` - Sort by time of most recent index

  - `published` - Sort by publication date

  - `published-print` - Sort by print publication date

  - `published-online` - Sort by online publication date

  - `issued` - Sort by issued date (earliest known publication date)

  - `is-referenced-by-count` - Sort by number of times this DOI is
    referenced by other Crossref DOIs

  - `references-count` - Sort by number of references included in the
    references section of the document identified by this DOI

- order:

  (character) Sort order, one of 'asc' or 'desc'

- .progress:

  Show a `plyr`-style progress bar? Options are "none", "text", "tk",
  "win, and "time". See
  [`plyr::create_progress_bar()`](https://rdrr.io/pkg/plyr/man/create_progress_bar.html)
  for details of each.

- ...:

  Named parameters passed on to
  [`crul::HttpClient()`](https://docs.ropensci.org/crul/reference/HttpClient.html)

- parse:

  (logical) Whether to output json `FALSE` or parse to list `TRUE`.
  Default: `FALSE`

## Details

BEWARE: The API will only work for CrossRef DOIs.

NOTE: The API route behind this function does not support filters any
more, so the `filter` parameter has been removed.

## References

https://github.com/CrossRef/rest-api-doc

## See also

Other crossref:
[`cr_funders()`](https://docs.ropensci.org/rcrossref/reference/cr_funders.md),
[`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md),
[`cr_members()`](https://docs.ropensci.org/rcrossref/reference/cr_members.md),
[`cr_prefixes()`](https://docs.ropensci.org/rcrossref/reference/cr_prefixes.md),
[`cr_types()`](https://docs.ropensci.org/rcrossref/reference/cr_types.md),
[`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)

## Examples

``` r
if (FALSE) { # \dontrun{
cr_licenses()
# query for something, e.g. a publisher
cr_licenses(query = 'elsevier')

# Low level function - does no parsing to data.frame, get json or a list
cr_licenses_()
cr_licenses_(query = "elsevier")
cr_licenses_(query = "elsevier", parse=TRUE)
} # }
```
