# Search CrossRef works (articles)

Search CrossRef works (articles)

## Usage

``` r
cr_works(
  dois = NULL,
  query = NULL,
  filter = NULL,
  offset = NULL,
  limit = NULL,
  sample = NULL,
  sort = NULL,
  order = NULL,
  facet = FALSE,
  cursor = NULL,
  cursor_max = 5000,
  .progress = "none",
  flq = NULL,
  select = NULL,
  async = FALSE,
  ...
)

cr_works_(
  dois = NULL,
  query = NULL,
  filter = NULL,
  offset = NULL,
  limit = NULL,
  sample = NULL,
  sort = NULL,
  order = NULL,
  facet = FALSE,
  cursor = NULL,
  cursor_max = 5000,
  .progress = "none",
  parse = FALSE,
  flq = NULL,
  select = NULL,
  async = FALSE,
  ...
)
```

## Arguments

- dois:

  Search by a single DOI or many DOIs. Note that using this parameter at
  the same time as the `query`, `limit`, `select` or `flq` parameter
  will result in an error.

- query:

  Query terms

- filter:

  Filter options. See examples for usage examples and
  [`filters`](https://docs.ropensci.org/rcrossref/reference/filters.md)
  for what filters are available. `filter` is available for use with
  `cr_works` and other `crossref` family functions with `works=TRUE`

- offset:

  Number of record to start at. Minimum: 1. For `cr_works`, and any
  function setting `works = TRUE`, the maximum offset value is 10000.
  For larger requests use `cursor`.

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

- async:

  (logical) use async HTTP requests. Default: `FALSE`

- ...:

  Named parameters passed on to
  [`verb-GET`](https://docs.ropensci.org/crul/reference/verb-GET.html)

- parse:

  (logical) Whether to output json `FALSE` or parse to list `TRUE`.
  Default: `FALSE`

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

## Beware

The API will only work for CrossRef DOIs.

## Functions

- `cr_works()` - Does data request and parses to data.frame for easy
  downstream consumption

- `cr_works_()` - Does data request, and gives back json (default) or
  lists, with no attempt to parse to data.frame's

## Explanation of some data fields

- score: a term frequency, inverse document frequency score that comes
  from the Crossref Solr backend, based on bibliographic metadata fields
  title, publication title, authors, ISSN, publisher, and date of
  publication.

## References

https://github.com/CrossRef/rest-api-doc

## See also

Other crossref:
[`cr_funders()`](https://docs.ropensci.org/rcrossref/reference/cr_funders.md),
[`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md),
[`cr_licenses()`](https://docs.ropensci.org/rcrossref/reference/cr_licenses.md),
[`cr_members()`](https://docs.ropensci.org/rcrossref/reference/cr_members.md),
[`cr_prefixes()`](https://docs.ropensci.org/rcrossref/reference/cr_prefixes.md),
[`cr_types()`](https://docs.ropensci.org/rcrossref/reference/cr_types.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Works funded by the NSF
cr_works(query="NSF")

# Works that include renear but not ontologies
cr_works(query="renear+-ontologies")

# Filter
cr_works(query="global state", filter=c(has_orcid=TRUE), limit=3)
# Filter by multiple fields
cr_works(filter=c(has_orcid=TRUE, from_pub_date='2004-04-04'))
# Only full text articles
cr_works(filter=c(has_full_text = TRUE))
# has affilitation data
cr_works(filter=c(has_affiliation = TRUE))
# has abstract
cr_works(filter=c(has_abstract = TRUE))
# has clinical trial number
cr_works(filter=c(has_clinical_trial_number = TRUE))

# Querying dois
cr_works(dois='10.1063/1.3593378')
cr_works('10.1371/journal.pone.0033693')
cr_works(dois='10.1007/12080.1874-1746')
cr_works(dois=c('10.1007/12080.1874-1746','10.1007/10452.1573-5125',
   '10.1111/(issn)1442-9993'))

# progress bar
cr_works(dois=c('10.1007/12080.1874-1746','10.1007/10452.1573-5125'),
   .progress="text")

# Include facetting in results
cr_works(query="NSF", facet=TRUE)
## Get facets only, by setting limit=0
cr_works(query="NSF", facet=TRUE, limit=0)
## you can also set facet to a query
cr_works(facet = "license:*", limit=0)

# Sort results
cr_works(query="ecology", sort='relevance', order="asc")
res <- cr_works(query="ecology", sort='score', order="asc")
res$data$score
cr_works(query="ecology", sort='published')
x=cr_works(query="ecology", sort='published-print')
x=cr_works(query="ecology", sort='published-online')

# Get a random number of results
cr_works(sample=1)
cr_works(sample=10)

# You can pass in dot separated fields to filter on specific fields
cr_works(filter=c(award.number='CBET-0756451',
   award.funder='10.13039/100000001'))

# Use the cursor for deep paging
cr_works(query="NSF", cursor = "*", cursor_max = 300, limit = 100)
cr_works(query="NSF", cursor = "*", cursor_max = 300, limit = 100,
   facet = TRUE)
## with optional progress bar
x <- cr_works(query="NSF", cursor = "*", cursor_max = 1200, limit = 200, 
  .progress = TRUE)

# Low level function - does no parsing to data.frame, get json or a list
cr_works_(query = "NSF")
cr_works_(query = "NSF", parse=TRUE)
cr_works_(query="NSF", cursor = "*", cursor_max = 300, limit = 100)
cr_works_(query="NSF", cursor = "*", cursor_max = 300, limit = 100,
   parse=TRUE)

# field queries
## query.author
res <- cr_works(query = "ecology", flq = c(query.author = 'Boettiger'))

## query.container-title
res <- cr_works(query = "ecology",
  flq = c(`query.container-title` = 'Ecology'))

## query.author and query.bibliographic
res <- cr_works(query = "ecology",
  flq = c(query.author = 'Smith', query.bibliographic = 'cell'))

# select only certain fields to return
res <- cr_works(query = "NSF", select = c('DOI', 'title'))
names(res$data)

# asyc
queries <- c("ecology", "science", "cellular", "birds", "European",
  "bears", "beets", "laughter", "hapiness", "funding")
res <- cr_works(query = queries, async = TRUE)
res_json <- cr_works_(query = queries, async = TRUE)
unname(vapply(res_json, class, ""))
jsonlite::fromJSON(res_json[[1]])

queries <- c("ecology", "science", "cellular")
res <- cr_works(query = queries, async = TRUE, verbose = TRUE)
res

# time
queries <- c("ecology", "science", "cellular", "birds", "European",
  "bears", "beets", "laughter", "hapiness", "funding")
system.time(cr_works(query = queries, async = TRUE))
system.time(lapply(queries, function(z) cr_works(query = z)))
} # }
```
