# Search CrossRef prefixes

Search CrossRef prefixes

## Usage

``` r
cr_prefixes(
  prefixes,
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

cr_prefixes_(
  prefixes,
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

- prefixes:

  (character) Publisher prefixes, one or more in a vector or list.
  Required.

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

Note that any one publisher can have more than one DOI. If you want to
search on all DOIs for a publisher, pass in all DOIs, or see
[`cr_members()`](https://docs.ropensci.org/rcrossref/reference/cr_members.md),
and pass in the `member_ids` parameter.

Notes from CrossRef (quoting them):

The prefix of a CrossRef DOI does NOT indicate who currently owns the
DOI. It only reflects who originally registered the DOI. CrossRef
metadata has an `owner_prefix` element that records the current owner of
the CrossRef DOI in question.

CrossRef also has member IDs for depositing organisations. A single
member may control multiple owner prefixes, which in turn may control a
number of DOIs. When looking at works published by a certain
organisation, member IDs and the member routes should be used.

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

## References

https://github.com/CrossRef/rest-api-doc

## See also

Other crossref:
[`cr_funders()`](https://docs.ropensci.org/rcrossref/reference/cr_funders.md),
[`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md),
[`cr_licenses()`](https://docs.ropensci.org/rcrossref/reference/cr_licenses.md),
[`cr_members()`](https://docs.ropensci.org/rcrossref/reference/cr_members.md),
[`cr_types()`](https://docs.ropensci.org/rcrossref/reference/cr_types.md),
[`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)

## Examples

``` r
if (FALSE) { # \dontrun{
cr_prefixes(prefixes="10.1016")
cr_prefixes(prefixes="10.1016", works=TRUE)
cr_prefixes(prefixes=c('10.1016','10.1371','10.1023','10.4176','10.1093'))
cr_prefixes(prefixes=c('10.1016','10.1371'), works=TRUE)
cr_prefixes(prefixes="10.1016", works=TRUE, filter=c(has_full_text=TRUE), 
  limit=5)
cr_prefixes(prefixes="10.1016", works=TRUE, query='ecology', limit=4)
cr_prefixes(prefixes="10.1016", works=TRUE, query='ecology', limit=4)

# facets - only avail. when works=TRUE
cr_prefixes(prefixes="10.1016", works=TRUE, facet=TRUE)
cr_prefixes(prefixes="10.1016", works=TRUE, facet="license:*", limit=0)
cr_prefixes(prefixes=c('10.1016','10.1371'), works=TRUE, facet=TRUE,
  limit=0)

# Use the cursor for deep paging
cr_prefixes("10.1016", works = TRUE, cursor = "*", cursor_max = 500,
   limit = 100)
cr_prefixes(c('10.1016', '10.1371'), works = TRUE, cursor = "*",
   cursor_max = 300, limit = 100)
## with optional progress bar
cr_prefixes("10.1016", works = TRUE, cursor = "*", cursor_max = 500,
   limit = 100, .progress = TRUE)

# Low level function - does no parsing to data.frame, get json or a list
cr_prefixes_("10.1016")
cr_prefixes_(c('10.1016', '10.1371'))
cr_prefixes_("10.1016", works = TRUE, query = 'ecology', limit = 10)
cr_prefixes_("10.1016", works = TRUE, query = 'ecology', parse=TRUE,
   limit = 10)
cr_prefixes_("10.1016", works = TRUE, cursor = "*",
   cursor_max = 300, limit = 100)
cr_prefixes_("10.1016", works = TRUE, cursor = "*",
   cursor_max = 300, limit = 100, parse = TRUE)

# field queries
## query.container-title
cr_prefixes("10.1016", works = TRUE,
  flq = c(`query.container-title` = 'Ecology'))

# select only certain fields to return
res <- cr_prefixes("10.1016", works = TRUE, select = c('DOI', 'title'))
names(res$data)
} # }
```
