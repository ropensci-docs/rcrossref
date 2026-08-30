# Changelog

## rcrossref 1.2.1

CRAN release: 2025-08-20

- fix bibtex::do_read_bib() deprecation warning
- add example to
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  using `doi` filter for querying multiple dois at once (thanks
  [@LukasWallrich](https://github.com/LukasWallrich))

## rcrossref 1.2.0

CRAN release: 2022-11-11

- implement Crossref’s REST API updates for the public and polite pool
- change of maintainer

## rcrossref 1.1.0

CRAN release: 2020-10-02

#### MINOR IMPROVEMENTS

- move `bibtex` package to Suggests as it has been orphaned, use it
  conditionally
  ([\#209](https://github.com/ropensci/rcrossref/issues/209))
- change all uses of
  [`tibble::tbl_df`](https://tibble.tidyverse.org/reference/tbl_df-class.html)
  to
  [`tibble::as_tibble`](https://tibble.tidyverse.org/reference/as_tibble.html)
  ([\#206](https://github.com/ropensci/rcrossref/issues/206))
- additional fields now parsed in the
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  output: short-container-title, references-count,
  is-referenced-by-count, language, content-domain, and update-to
  ([\#208](https://github.com/ropensci/rcrossref/issues/208))

## rcrossref 1.0.0

CRAN release: 2020-03-19

#### MINOR IMPROVEMENTS

- docs page vignette has names
  ([\#197](https://github.com/ropensci/rcrossref/issues/197))
- `query.title` field query is no longer supported by Crossref, removed
  from package
  ([\#198](https://github.com/ropensci/rcrossref/issues/198))
- fix some links in readme
  ([\#199](https://github.com/ropensci/rcrossref/issues/199))
- improve documentation for how to do deep paging (new section “Deep
  paging”), and how to use the cursor specifically
  ([\#190](https://github.com/ropensci/rcrossref/issues/190))

#### BUG FIXES

- fix error when progress used and when limit param not used
  ([\#190](https://github.com/ropensci/rcrossref/issues/190))
- encoding fix for the Crossref RStudio Addin
  ([\#194](https://github.com/ropensci/rcrossref/issues/194))
  ([\#201](https://github.com/ropensci/rcrossref/issues/201))

## rcrossref 0.9.2

CRAN release: 2019-05-04

### NEW FEATURES

- [`cr_funders()`](https://docs.ropensci.org/rcrossref/reference/cr_funders.md),
  [`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md),
  [`cr_licenses()`](https://docs.ropensci.org/rcrossref/reference/cr_licenses.md),
  [`cr_members()`](https://docs.ropensci.org/rcrossref/reference/cr_members.md),
  [`cr_prefixes()`](https://docs.ropensci.org/rcrossref/reference/cr_prefixes.md),
  [`cr_types()`](https://docs.ropensci.org/rcrossref/reference/cr_types.md),
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  gain ability to show a progress bar when using deep pagination when
  using `works=TRUE`
  ([\#186](https://github.com/ropensci/rcrossref/issues/186))
  ([\#188](https://github.com/ropensci/rcrossref/issues/188))

#### MINOR IMPROVEMENTS

- fix a test fixture that had non-ascii characters
  ([\#187](https://github.com/ropensci/rcrossref/issues/187))
- [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  returned a tibble in the `$data` slot in each case except for when a
  single DOI was passed to the `doi` parameter. now fixed
  ([\#184](https://github.com/ropensci/rcrossref/issues/184)) thanks
  [@martinjhnhadley](https://github.com/martinjhnhadley)

## rcrossref 0.9.0

CRAN release: 2019-01-14

#### NEW FEATURES

- big Crossref Addin update
  ([\#171](https://github.com/ropensci/rcrossref/issues/171)) all work
  by [@haozhu233](https://github.com/haozhu233)
- Async HTTP introduced for
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md),
  [`cr_works_()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md),
  and
  [`cr_citation_count()`](https://docs.ropensci.org/rcrossref/reference/cr_citation_count.md).
  See the new parameter `async` (logical) in those functions. For
  [`cr_citation_count()`](https://docs.ropensci.org/rcrossref/reference/cr_citation_count.md),
  it now accepts more than 1 DOI, and the output has changed from a
  numeric value to a data.frame (columns: `doi` and `count`). With
  `async=TRUE` for
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  you get a list of data.frame’s; while for
  [`cr_works_()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  you get a list of JSON’s
  ([\#121](https://github.com/ropensci/rcrossref/issues/121))
  ([\#160](https://github.com/ropensci/rcrossref/issues/160))
  ([\#182](https://github.com/ropensci/rcrossref/issues/182))

#### MINOR IMPROVEMENTS

- package tests now using `vcr` for HTTP request/response caching
  ([\#178](https://github.com/ropensci/rcrossref/issues/178))
  ([\#179](https://github.com/ropensci/rcrossref/issues/179))
- in `works` data, now returning `published-print` and
  `published-online` fields
  ([\#181](https://github.com/ropensci/rcrossref/issues/181))
- add new filters for `/works` routes (when `works = TRUE`): `isbn`,
  `reference_visibility`, `has_content_domain`, and
  `has_domain_restriction`
  ([\#176](https://github.com/ropensci/rcrossref/issues/176))
  ([\#177](https://github.com/ropensci/rcrossref/issues/177))
- add new return element in `/works` routes (when `works = TRUE`):
  `$reference` gives the references cited in the article (these are not
  the articles citing the target article, sorry)
  ([\#176](https://github.com/ropensci/rcrossref/issues/176))
- improve documentation on the “polite pool”. If you supply an email
  address Crossref will put you in the polite pool
  ([\#173](https://github.com/ropensci/rcrossref/issues/173))
  ([\#175](https://github.com/ropensci/rcrossref/issues/175)) thanks
  [@poldham](https://github.com/poldham)
- added example to
  [`cr_abstract()`](https://docs.ropensci.org/rcrossref/reference/cr_abstract.md)
  of handling many DOIs while allowing for failures without stopping
  progress ([\#174](https://github.com/ropensci/rcrossref/issues/174))
  thanks [@zackbatist](https://github.com/zackbatist)

#### BUG FIXES

- fix internal parsing of funder data in
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  ([\#180](https://github.com/ropensci/rcrossref/issues/180)) thanks
  [@nicholasmfraser](https://github.com/nicholasmfraser) for the bug
  report
- fix for
  [`cr_citation_count()`](https://docs.ropensci.org/rcrossref/reference/cr_citation_count.md):
  when given a bad/invalid/malformed DOI, throw warning and give back an
  `NA` ([\#164](https://github.com/ropensci/rcrossref/issues/164))
  thanks for the report [@chreman](https://github.com/chreman)
- Fix for instances in the package where we incorrectly were doing
  logical comparison’s; detected via *R_CHECK_LENGTH_1_LOGIC2*

## rcrossref 0.8.4

CRAN release: 2018-08-06

#### NEW FEATURES

- The RStudio Addin now includes ability to search by article metadata,
  e.g., title
  ([\#148](https://github.com/ropensci/rcrossref/issues/148))
  ([\#152](https://github.com/ropensci/rcrossref/issues/152))
- you can now set a different base url for
  [`cr_cn()`](https://docs.ropensci.org/rcrossref/reference/cr_cn.md)
  ([\#168](https://github.com/ropensci/rcrossref/issues/168))

#### MINOR IMPROVEMENTS

- better behavior for
  [`cr_cn()`](https://docs.ropensci.org/rcrossref/reference/cr_cn.md)
  when bibentry not valid, that is not parseable. before the package we
  use to parse `bibtex` would stop on invalid bibentry data, but now we
  get around the invalid bits and give back the bibentry
  ([\#147](https://github.com/ropensci/rcrossref/issues/147))
- updated and improved documentation for filters
  ([\#161](https://github.com/ropensci/rcrossref/issues/161))
- improved description of the `dois` parameter
  ([\#162](https://github.com/ropensci/rcrossref/issues/162)) thanks
  [@ms609](https://github.com/ms609)
- Much improved error behavior for `cr_*` functions. We now give errors
  like `404 (client error): /works/blblbl - Resource not found.`, which
  includes HTTP status code, major class of error (success, redirect,
  client, server), the route requested, and the error message
  ([\#163](https://github.com/ropensci/rcrossref/issues/163))

#### BUG FIXES

- fixed bug in
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  in which field queries should have been possible for title and
  affiliation, but were not. Fixed now.
  ([\#149](https://github.com/ropensci/rcrossref/issues/149))
- [`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md)
  was not correctly parsing data when more than 1 ISSN given and `works`
  set to `TRUE`, fixed now
  ([\#156](https://github.com/ropensci/rcrossref/issues/156))
- [`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md)
  was not correctly parsing data when no ISSN found and `works` set to
  `TRUE`, fixed now
  ([\#150](https://github.com/ropensci/rcrossref/issues/150))
- [`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md)
  was not correctly handling queries with multiple ISSN’s and `works`
  set to `FALSE`, fixed now
  ([\#151](https://github.com/ropensci/rcrossref/issues/151))
- fixed bug in
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md),
  and any other `cr_*` function that set `works=TRUE`. the `license`
  slot can have more than 1 result, and we were only giving the first
  back. fixed the parsing on this to give back all license results
  ([\#170](https://github.com/ropensci/rcrossref/issues/170))

## rcrossref 0.8.0

CRAN release: 2017-12-03

#### NEW FEATURES

- Include documentation and internals to support passing a user supplied
  email to Crossref to get put into higher rate limit pool
  ([\#145](https://github.com/ropensci/rcrossref/issues/145)) thanks
  [@njahn82](https://github.com/njahn82)
- Functions that operate on the `/works` route gain a `select` parameter
  to select certain fields to return
  ([\#146](https://github.com/ropensci/rcrossref/issues/146))

#### MINOR IMPROVEMENTS

- Updated docs for additional options for the `sort` parameter
  ([\#142](https://github.com/ropensci/rcrossref/issues/142))
- Updated docs for additional options for doing field queries (the `flq`
  parameter) ([\#143](https://github.com/ropensci/rcrossref/issues/143))
- Filters: New filters added to the package, and some removed (e.g,
  `publisher-name`). You can see the filters with the functions
  `filter_details`/`filter_names`. Beware, some filters error sometimes
  with the Crossref API - they may not work, but they may, let me know
  at <https://github.com/ropensci/rcrossref/issues> or let Crossref know
  at <https://github.com/CrossRef/rest-api-doc/issues>
  ([\#136](https://github.com/ropensci/rcrossref/issues/136))
  ([\#139](https://github.com/ropensci/rcrossref/issues/139))
  ([\#141](https://github.com/ropensci/rcrossref/issues/141))

## rcrossref 0.7.0

CRAN release: 2017-04-28

#### NEW FEATURES

- All text mining functionality moved into a new package: `crminer`
  <https://github.com/ropensci-archive/crminer> . Functions that did
  text mining stuff now defunct, see `?rcrossref-defunct`
  ([\#122](https://github.com/ropensci/rcrossref/issues/122))
- All Crossref API requests now using `https` instead of `http`
  ([\#133](https://github.com/ropensci/rcrossref/issues/133))

#### MINOR IMPROVEMENTS

- replace
  [`xml2::xml_find_one`](http://xml2.r-lib.org/reference/xml_find_all.md)
  with
  [`xml2::xml_find_first`](http://xml2.r-lib.org/reference/xml_find_all.md)
  ([\#128](https://github.com/ropensci/rcrossref/issues/128)) thanks
  [@njahn82](https://github.com/njahn82)
- replaced `httr` with `crul` for HTTP requests
  ([\#132](https://github.com/ropensci/rcrossref/issues/132))
- Now using markdown for documentation
  ([\#135](https://github.com/ropensci/rcrossref/issues/135))
- Added more documentation to `cr_journals` and `cr_works` about what
  the returned data fields `backfile_dois` and `current_dois` really
  mean ([\#105](https://github.com/ropensci/rcrossref/issues/105))
  thanks [@SteveViss](https://github.com/SteveViss)

#### BUG FIXES

- Fix to `cr_prefixes` to not fail when no results found
  ([\#130](https://github.com/ropensci/rcrossref/issues/130)) thanks
  [@globbestael](https://github.com/globbestael)
- Fixed `cr_works` to allow queries like `facet = license:*` to be
  passed to `facet` parameter (was always allowed by Crossref, but we
  neglected to allow it - previously only allowed a boolean)
  ([\#129](https://github.com/ropensci/rcrossref/issues/129))
- Fixed `cr_funders` and `cr_journals` to give back facet data along
  with other data
  ([\#134](https://github.com/ropensci/rcrossref/issues/134))
- Fix to `cr_*` functions to check for a missing content-type headers
  and instead of failing, we continue anyway and try to parse data as
  sometimes Crossref doesn’t give back a content type header at all
  ([\#127](https://github.com/ropensci/rcrossref/issues/127))

## rcrossref 0.6.0

CRAN release: 2016-11-09

#### NEW FEATURES

- Added support for field queries (see
  <https://github.com/CrossRef/rest-api-doc/blob/master/rest_api.md#field-queries>
  for information on them). Means that you can query on specific fields
  rather than using `query` parameter which queries across all fields
  ([\#111](https://github.com/ropensci/rcrossref/issues/111))
- Now using `rappdirs` for local storage and caching for `cr_ft_text`
  ([\#106](https://github.com/ropensci/rcrossref/issues/106))

#### MINOR IMPROVEMENTS

- Added to man files where appropriate new 10K max value for the
  `offset` parameter
  ([\#126](https://github.com/ropensci/rcrossref/issues/126))
- Added to pkg level man file new rate limit headers included, and how
  users can get to those, via `config=verbose()` call
  ([\#124](https://github.com/ropensci/rcrossref/issues/124))
- Better failure modes on input parameters, still more work to do surely
  ([\#101](https://github.com/ropensci/rcrossref/issues/101))
- sleeping now between tests to avoid making crossref rate limit gate
  keepers mad
  ([\#125](https://github.com/ropensci/rcrossref/issues/125))
- `cr_search` and `cr_search_free` are now defunct. They were marked
  deprecated in previous version, and warned of defunct, and now they
  are defunct. Similar functionality can be done with e.g.,
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  ([\#102](https://github.com/ropensci/rcrossref/issues/102))
- `crosscite` is now defunct. The functionality of this function can be
  achieved with
  [`cr_cn()`](https://docs.ropensci.org/rcrossref/reference/cr_cn.md)
  ([\#82](https://github.com/ropensci/rcrossref/issues/82))
- `cr_fundref` is now defunct. Crossref changed their name `fundref` to
  `funders`, so we’ve changed our function, see
  [`cr_funders()`](https://docs.ropensci.org/rcrossref/reference/cr_funders.md)
  ([\#83](https://github.com/ropensci/rcrossref/issues/83))
- parameter `sample` maximum value is now 100, was previously 1000.
  documentation updated.
  ([\#118](https://github.com/ropensci/rcrossref/issues/118))
- New filters `has-clinical-trial-number` and `has-abstract` added to
  the package, see
  [`?filters`](https://docs.ropensci.org/rcrossref/reference/filters.md)
  for help ([\#120](https://github.com/ropensci/rcrossref/issues/120))

## rcrossref 0.5.8

CRAN release: 2016-08-26

#### NEW FEATURES

- Added an RStudio Addin for searching for citations. See
  [`?rcrossref`](https://docs.ropensci.org/rcrossref/reference/rcrossref-package.md)
  for more. Addin authored by Hao Zhu
  [@haozhu233](https://github.com/haozhu233)
  ([\#114](https://github.com/ropensci/rcrossref/issues/114))
- New function
  [`cr_abstract()`](https://docs.ropensci.org/rcrossref/reference/cr_abstract.md)
  that tries to get an abstract via XML provided by Crossref - NOTE: an
  abstract is rarely available though
  ([\#116](https://github.com/ropensci/rcrossref/issues/116))

#### BUG FIXES

- Fixed bug in
  [`cr_cn()`](https://docs.ropensci.org/rcrossref/reference/cr_cn.md)
  where DOIs with no minting agency found were failing because we were
  previously stopping when no agency found. Now, we just assume Crossref
  and move on from there.
  ([\#117](https://github.com/ropensci/rcrossref/issues/117)) thanks
  [@dfalster](https://github.com/dfalster) !
- Fix to
  [`cr_r()`](https://docs.ropensci.org/rcrossref/reference/cr_r.md) when
  number requested \> 100. Actual fix is in
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md).
  Max for sample used to be 1000, asked this on the Crossref API forum,
  see <https://github.com/CrossRef/rest-api-doc/issues/146>
  ([\#115](https://github.com/ropensci/rcrossref/issues/115))
- Fix to
  [`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md)
  in internal parsing, was failing in cases where `ISSN` array was of
  length zero

## rcrossref 0.5.4

CRAN release: 2016-07-20

#### MINOR IMPROVEMENTS

- Improved documentation for
  [`cr_citation_count()`](https://docs.ropensci.org/rcrossref/reference/cr_citation_count.md)
  to remove PLOS reference as the function isn’t only for PLOS works
  ([\#108](https://github.com/ropensci/rcrossref/issues/108))
- Changed use of `dplyr::rbind_all()` to
  [`dplyr::bind_rows()`](https://dplyr.tidyverse.org/reference/bind_rows.html)
  ([\#113](https://github.com/ropensci/rcrossref/issues/113))

## rcrossref 0.5.2

CRAN release: 2016-02-10

#### NEW FEATURES

- User-agent string is passed with every request to Crossref with names
  and versions of this package, and its HTTP dependency packages: `httr`
  and `curl` (which `httr` depends on). Will potentially be useful to
  Crossref to know how many requests come from this R client
  ([\#100](https://github.com/ropensci/rcrossref/issues/100))

#### DEPRECATED

- [`cr_search()`](https://docs.ropensci.org/rcrossref/reference/cr_search-defunct.md)
  and
  [`cr_search_free()`](https://docs.ropensci.org/rcrossref/reference/cr_search_free-defunct.md)
  use old Crossref web services, so are now marked deprecated, and will
  throw a deprecation message, but can still be used. They will both be
  defunct in `v0.6` of this package
  ([\#99](https://github.com/ropensci/rcrossref/issues/99))

#### MINOR IMPROVEMENTS

- `XML` replaced with `xml2`
  ([\#98](https://github.com/ropensci/rcrossref/issues/98))
- `httr::content()` calls: all parse to text then parse content
  manually. in addition, encoding explicitly set to `UTF-8` on
  `httr::content()` calls
  ([\#98](https://github.com/ropensci/rcrossref/issues/98))

#### BUG FIXES

- Bug fix to
  [`cr_journals()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md) -
  fix to parse correctly on some failed requests
  ([\#97](https://github.com/ropensci/rcrossref/issues/97)) thanks
  [@nkorf](https://github.com/nkorf)
- Bug fix to `cr_fundref()/cr_funders()` - parsing wasn’t working
  correctly in all cases

## rcrossref 0.5.0

CRAN release: 2016-01-20

Skipped `v0.4` to `v0.5` because of many changes - as described below.

#### NEW FEATURES

- Support added for ‘deep paging’ with the newer Crossref search API.
  Two new params added to each function: `cursor`, which accepts a
  cursor alphanumeric string or the special `*`, which indicates that
  you want to initiate deep paging; `cursor_max`, which is not in the
  Crossref API, but just used here in this package to indicate where to
  stop - otherwise, you’d get all results, even if there was 70 million,
  for example. A new internal `R6` class used to make cursor requests
  easy ([\#77](https://github.com/ropensci/rcrossref/issues/77))
- New function
  [`id_converter()`](https://docs.ropensci.org/rcrossref/reference/id_converter.md)
  to get a PMID from a DOI and vice versa
  ([\#49](https://github.com/ropensci/rcrossref/issues/49))
- Added a Code of Conduct.
- New function
  [`cr_types()`](https://docs.ropensci.org/rcrossref/reference/cr_types.md),
  along with its low level equivalent
  [`cr_types_()`](https://docs.ropensci.org/rcrossref/reference/cr_types.md)
  for when you just want a list or json back
  ([\#92](https://github.com/ropensci/rcrossref/issues/92))
- New suite of functions composing a low-level API for the Crossref
  search API. These functions only do data request, and return json or a
  list, and do not attempt to parse to a data.frame. The new functions:
  [`cr_funders_()`](https://docs.ropensci.org/rcrossref/reference/cr_funders.md),
  [`cr_journals_()`](https://docs.ropensci.org/rcrossref/reference/cr_journals.md),
  [`cr_licenses_()`](https://docs.ropensci.org/rcrossref/reference/cr_licenses.md),
  [`cr_members_()`](https://docs.ropensci.org/rcrossref/reference/cr_members.md),
  [`cr_prefixes_()`](https://docs.ropensci.org/rcrossref/reference/cr_prefixes.md),
  [`cr_types_()`](https://docs.ropensci.org/rcrossref/reference/cr_types.md),
  [`cr_works_()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md).
  These functions are a bit faster, and aren’t subject to parsing errors
  in the event of a change in the Crossref API.
  ([\#93](https://github.com/ropensci/rcrossref/issues/93))
- Added new
  [`filter_names()`](https://docs.ropensci.org/rcrossref/reference/filters.md)
  and
  [`filter_details()`](https://docs.ropensci.org/rcrossref/reference/filters.md)
  functions to get information on what filters are available, the
  expected values, and what they mean.

#### MINOR IMPROVEMENTS

- Added documentation for new filter types, and added them to list of
  filters for
  [`filter_names()`](https://docs.ropensci.org/rcrossref/reference/filters.md)
  and
  [`filter_details()`](https://docs.ropensci.org/rcrossref/reference/filters.md)
  ([\#73](https://github.com/ropensci/rcrossref/issues/73))
- [`cr_funders()`](https://docs.ropensci.org/rcrossref/reference/cr_funders.md)
  alias added to
  [`cr_fundref()`](https://docs.ropensci.org/rcrossref/reference/cr_fundref-defunct.md)
  ([\#74](https://github.com/ropensci/rcrossref/issues/74))
- Made note in docs that funders without IDs don’t show up on the
  `/funders` route,s in
  [`cr_funders()`](https://docs.ropensci.org/rcrossref/reference/cr_funders.md)
  ([\#79](https://github.com/ropensci/rcrossref/issues/79))
- Made note in docs that `sample` parameter ignored unless `works=TRUE`
  ([\#81](https://github.com/ropensci/rcrossref/issues/81))
- Added note to docs that only what is returned in the API is what is
  searched when you search the Crossref API - that is, abstracts and
  full text aren’t searched
  ([\#91](https://github.com/ropensci/rcrossref/issues/91))
- [`cr_cn()`](https://docs.ropensci.org/rcrossref/reference/cr_cn.md)
  now checks that the user supplied content-type is supported for the
  DOI minting agency associated with the DOI
  ([\#88](https://github.com/ropensci/rcrossref/issues/88)) (thanks
  [@njahn82](https://github.com/njahn82))
- Removed `.progress` parameter use internally where it wasn’t
  applicable.
- `sample` parameter dropped from
  [`cr_licenses()`](https://docs.ropensci.org/rcrossref/reference/cr_licenses.md).
- [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  parsing changed. We now don’t attempt to flatten nested arrays, but
  instead give them back as data.frame’s nested within the main
  data.frame. For example, `author` often has many entries, so we return
  that as a single column, but indexing to that column gives back a
  data.frame with a row for each author, and N number of columns.
  Hopefully this doesn’t break too much code downstream :)
- Additional text added to the package level man file
  ([`?rcrossref`](https://docs.ropensci.org/rcrossref/reference/rcrossref-package.md))
  to explain: what you’re actually searching when you search; deprecated
  and defunct functions; and explanation of high vs. low level API.

#### BUG FIXES

- Fix to
  [`cr_members()`](https://docs.ropensci.org/rcrossref/reference/cr_members.md)
  to warn on error instead of stop during parsing
  ([\#68](https://github.com/ropensci/rcrossref/issues/68))
- Fix to internal parser for
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  to output links data, for full text links
  ([\#70](https://github.com/ropensci/rcrossref/issues/70))
- Minor fix in
  [`cr_cn()`](https://docs.ropensci.org/rcrossref/reference/cr_cn.md)
  example that didn’t work
  ([\#80](https://github.com/ropensci/rcrossref/issues/80))
- Fixed parsing of `affiliation` data inside `author` object in Crossref
  search API returned data
  ([\#84](https://github.com/ropensci/rcrossref/issues/84))
- Fixed parsing of funder `award` slot in Crossref search API returned
  data ([\#90](https://github.com/ropensci/rcrossref/issues/90))

#### DEPRECATED

- [`crosscite()`](https://docs.ropensci.org/rcrossref/reference/crosscite-defunct.md)
  deprecated, will be removed in a future version of this package
  ([\#78](https://github.com/ropensci/rcrossref/issues/78))
- [`cr_fundref()`](https://docs.ropensci.org/rcrossref/reference/cr_fundref-defunct.md)
  now has a deprecated message, and will be removed in the next version
  ([\#74](https://github.com/ropensci/rcrossref/issues/74))

## rcrossref 0.3.4

CRAN release: 2015-07-10

#### NEW FEATURES

- Added new function
  [`crosscite()`](https://docs.ropensci.org/rcrossref/reference/crosscite-defunct.md)
  to work with the Citeproc service (<http://crosscite.org/citeproc/>)
  ([\#60](https://github.com/ropensci/rcrossref/issues/60))

#### BUG FIXES

- Fixed problems related to `httr` `v1`
  ([\#65](https://github.com/ropensci/rcrossref/issues/65))
- Import all non-base R functions
  ([\#64](https://github.com/ropensci/rcrossref/issues/64))
- The agency route was down used by the
  [`cr_agency()`](https://docs.ropensci.org/rcrossref/reference/cr_agency.md)
  function, back up and fixed now
  ([\#63](https://github.com/ropensci/rcrossref/issues/63))

## rcrossref 0.3.0

CRAN release: 2015-03-04

#### NEW FEATURES

- New function `extract_pdf()` to extract text from pdfs
- New function
  [`cr_ft_links()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_links-defunct.md)
  to get links for full text content of an article
  ([\#10](https://github.com/ropensci/rcrossref/issues/10))
- New function
  [`cr_ft_text()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_text-defunct.md)
  to get links for full text content of an article. In addition,
  [`cr_ft_pdf()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_pdf-defunct.md),
  [`cr_ft_plain()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_plain-defunct.md),
  and
  [`cr_ft_xml()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_xml-defunct.md)
  are convenience functions that will get the format pdf, plain text, or
  xml, respectively. You can of course specify format in the
  [`cr_ft_text()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_text-defunct.md)
  function with the `type` parameter
  ([\#10](https://github.com/ropensci/rcrossref/issues/10))
  ([\#42](https://github.com/ropensci/rcrossref/issues/42))

#### MINOR IMPROVEMENTS

- Filled out more tests
  ([\#45](https://github.com/ropensci/rcrossref/issues/45))

#### BUG FIXES

- No longer assign queried doi to the `data.frame` in
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md),
  which caused failure if a non-Crossref DOI included
  ([\#52](https://github.com/ropensci/rcrossref/issues/52))
- [`pmid2doi()`](https://docs.ropensci.org/rcrossref/reference/pmid2doi-defunct.md)
  and
  [`doi2pmid()`](https://docs.ropensci.org/rcrossref/reference/pmid2doi-defunct.md)
  functions removed temporarily as the web service is down temporarily,
  but will be online again soon from Crossref
  ([\#48](https://github.com/ropensci/rcrossref/issues/48))

## rcrossref 0.2.1

CRAN release: 2014-12-11

#### MINOR IMPROVEMENTS

- Fixes for man file examples.
  ([\#35](https://github.com/ropensci/rcrossref/issues/35))
- [`cr_citation()`](https://docs.ropensci.org/rcrossref/reference/cr_citation-defunct.md)
  is deprecated (stil useable, but will be removed in a future version
  of the package). use
  [`cr_cn()`](https://docs.ropensci.org/rcrossref/reference/cr_cn.md)
  instead. ([\#34](https://github.com/ropensci/rcrossref/issues/34))

## rcrossref 0.2.0

CRAN release: 2014-11-29

#### NEW FEATURES

- released to CRAN
