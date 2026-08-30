# Search the CrossRef Fundref API

Search the CrossRef Fundref API

## Usage

``` r
cr_funders(
  dois = NULL,
  query = NULL,
  filter = NULL,
  offset = NULL,
  limit = NULL,
  sample = NULL,
  sort = NULL,
  order = NULL,
  facet = FALSE,
  works = FALSE,
  cursor = NULL,
  cursor_max = 5000,
  .progress = "none",
  flq = NULL,
  select = NULL,
  ...
)

cr_funders_(
  dois = NULL,
  query = NULL,
  filter = NULL,
  offset = NULL,
  limit = NULL,
  sample = NULL,
  sort = NULL,
  order = NULL,
  facet = FALSE,
  works = FALSE,
  cursor = NULL,
  cursor_max = 5000,
  .progress = "none",
  parse = FALSE,
  flq = NULL,
  select = NULL,
  ...
)
```

## Arguments

- dois:

  Search by a single DOI or many DOIs.

- query:

  Query terms

- filter:

  Filter options. See examples for usage examples and
  [`filters`](https://docs.ropensci.org/rcrossref/reference/filters.md)
  for what filters are available. `filter` is available for use with
  `cr_works` and other `crossref` family functions with `works=TRUE`

- offset:

  Number of record to start at. Minimum: 1. For
  [`cr_works`](https://docs.ropensci.org/rcrossref/reference/cr_works.md),
  and any function setting `works = TRUE`, the maximum offset value
  is 10000. For larger requests use `cursor`.

- limit:

  Number of results to return in the query. Not relavant when searching
  with specific dois. Default: 20. Max: 1000

- sample:

  (integer) Number of random results to return. when you use the sample
  parameter, the rows and offset parameters are ignored. Ignored unless
  `works=TRUE`. Max: 100

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

- facet:

  (logical) Include facet results. Boolean or string with field to facet
  on. Valid fields are \*, affiliation, funder-name, funder-doi, orcid,
  container-title, assertion, archive, update-type, issn, published,
  source, type-name, publisher-name, license, category-name,
  assertion-group. Default: `FALSE`

- works:

  (logical) If `TRUE`, works returned as well, if not then not.

- cursor:

  (character) Cursor character string to do deep paging. Default is
  None. Pass in '\*' to start deep paging. Any combination of query,
  filters and facets may be used with deep paging cursors. While the
  `limit` parameter may be specified along with cursor, offset and
  sample cannot be used with the cursor. See
  https://github.com/CrossRef/rest-api-doc#deep-paging-with-cursors

- cursor_max:

  (integer) Max records to retrieve. Only used when cursor param used.
  Because deep paging can result in continuous requests until all are
  retrieved, use this parameter to set a maximum number of records. Of
  course, if there are less records found than this value, you will get
  only those found. When cursor pagination is being used the `limit`
  parameter sets the chunk size per request.

- .progress:

  Show a `plyr`-style progress bar? Options are "none", "text", "tk",
  "win", and "time". See
  [`create_progress_bar`](https://rdrr.io/pkg/plyr/man/create_progress_bar.html)
  for details of each. Only used when passing in multiple ids (e.g.,
  multiple DOIs, DOI prefixes, etc.), or when using the `cursor` param.
  When using the `cursor` param, this argument only accept a boolean,
  either `TRUE` or `FALSE`; any non-boolean is coerced to `FALSE`.

- flq:

  field queries. One or more field queries. Acceptable set of field
  query parameters are:

  - `query.container-title` - Query container-title aka. publication
    name

  - `query.author` - Query author first and given names

  - `query.editor` - Query editor first and given names

  - `query.chair` - Query chair first and given names

  - `query.translator` - Query translator first and given names

  - `query.contributor` - Query author, editor, chair and translator
    first and given names

  - `query.bibliographic` - Query bibliographic information, useful for
    citation lookup. Includes titles, authors, ISSNs and publication
    years

  - `query.affiliation` - Query contributor affiliations

  Note: `query.title` has been removed - use `query.bibliographic` as a
  replacement

- select:

  (character) One or more field to return (only those fields are
  returned)

- ...:

  Named parameters passed on to
  [`verb-GET`](https://docs.ropensci.org/crul/reference/verb-GET.html)

- parse:

  (logical) Whether to output json `FALSE` or parse to list `TRUE`.
  Default: `FALSE`

## Details

BEWARE: The API will only work for CrossRef DOIs.

This function name changing to `cr_funders` in the next version - both
work for now

## Note

See the "Rate limiting" seciton in
[rcrossref](https://docs.ropensci.org/rcrossref/reference/rcrossref-package.md)
to get into the "fast lane"

## Deep paging (using the cursor)

When using the cursor, a character string called `next-cursor` is
returned from Crossref that we use to do the next request, and so on. We
use a while loop to get number of results up to the value of
`cursor_max`. Since we are doing each request for you, you may not need
the `next-cursor` string, but if you do want it, you can get to it by
indexing into the result like `x$meta$next_cursor`

Note that you can pass in curl options when using cursor, via `"..."`

## NOTE

Funders without IDs don't show up on the /funders route, and in this
function. Some funders don't have assigned IDs in Crossref's system, so
won't show up in searches.

## References

https://github.com/CrossRef/rest-api-doc

## See also

Other crossref:
[`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md),
[`cr_licenses()`](https://docs.ropensci.org/rcrossref/reference/cr_licenses.md),
[`cr_members()`](https://docs.ropensci.org/rcrossref/reference/cr_members.md),
[`cr_prefixes()`](https://docs.ropensci.org/rcrossref/reference/cr_prefixes.md),
[`cr_types()`](https://docs.ropensci.org/rcrossref/reference/cr_types.md),
[`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)

## Examples

``` r
if (FALSE) { # \dontrun{
cr_funders(query="NSF", limit=1)
cr_funders(query="NSF")
cr_funders(dois='10.13039/100000001')
out <- cr_funders(dois=c('10.13039/100000001','10.13039/100000015'))
out['10.13039/100000001']
out[['10.13039/100000001']]

cr_funders(dois='10.13039/100000001')
cr_funders(dois='10.13039/100000001', works=TRUE, limit=5)

cr_funders(dois=c('10.13039/100000001','10.13039/100000015'))
cr_funders(dois=c('10.13039/100000001','10.13039/100000015'), works=TRUE)

## get facets back
cr_funders("10.13039/100000001", works=TRUE, facet=TRUE, limit = 0)
cr_funders("10.13039/100000001", works=TRUE, facet="license:*", limit = 0)
cr_funders('100000001', works = TRUE, cursor = "*", cursor_max = 500,
   limit = 100, facet=TRUE)

# Curl options
cr_funders(dois='10.13039/100000001', verbose = TRUE)

# If not found, and > 1 DOI given, those not found dropped
cr_funders(dois=c("adfadfaf","asfasf"))
cr_funders(dois=c("adfadfaf","asfasf"), works=TRUE)
cr_funders(dois=c("10.13039/100000001","asfasf"))
cr_funders(dois=c("10.13039/100000001","asfasf"), works=TRUE)

# Use the cursor for deep paging
cr_funders('100000001', works = TRUE, cursor = "*", cursor_max = 500,
   limit = 100)
cr_funders(c('100000001', '100000002'), works = TRUE, cursor = "*",
   cursor_max = 300, limit = 100)
## with optional progress bar
cr_funders('100000001', works = TRUE, cursor = "*", cursor_max = 500,
   limit = 100, .progress = TRUE)

# Low level function - does no parsing to data.frame, get json or a list
cr_funders_(query = 'nsf')
cr_funders_('10.13039/100000001')
cr_funders_(query = 'science', parse=TRUE)
cr_funders_('10.13039/100000001', works = TRUE, cursor = "*",
   cursor_max = 300, limit = 100)
cr_funders_('10.13039/100000001', works = TRUE, cursor = "*",
   cursor_max = 300, limit = 100, parse = TRUE)

# field queries
## query.container-title
cr_funders('10.13039/100000001', works = TRUE,
  flq = c(`query.container-title` = 'Ecology'))

# select only certain fields to return
res <- cr_funders('10.13039/100000001', works = TRUE, 
  select = c('DOI', 'title'))
names(res$data)
} # }
```
