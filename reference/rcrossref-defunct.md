# Defunct functions in rcrossref

These functions are gone, no longer available.

## Details

- [`cr_citation()`](https://docs.ropensci.org/rcrossref/reference/cr_citation-defunct.md):
  Crossref is trying to sunset their OpenURL API, which this function
  uses. So this function is now removed. See the function
  [`cr_cn()`](https://docs.ropensci.org/rcrossref/reference/cr_cn.md),
  which does the same things, but with more functionality, using the new
  Crossref API.

- [`pmid2doi()`](https://docs.ropensci.org/rcrossref/reference/pmid2doi-defunct.md)
  and
  [`doi2pmid()`](https://docs.ropensci.org/rcrossref/reference/pmid2doi-defunct.md):
  The API behind these functions is down for good, see
  [`id_converter()`](https://docs.ropensci.org/rcrossref/reference/id_converter.md)
  for similar functionality.

- [`cr_search()`](https://docs.ropensci.org/rcrossref/reference/cr_search-defunct.md):
  The functionality of this function can be achieved with the new
  Crossref API. See functions
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  et al.

- [`cr_search_free()`](https://docs.ropensci.org/rcrossref/reference/cr_search_free-defunct.md):
  The functionality of this function can be achieved with the new
  Crossref API. See functions
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)
  et al.

- [`crosscite()`](https://docs.ropensci.org/rcrossref/reference/crosscite-defunct.md):
  The functionality of this function can be achieved with
  [`cr_cn()`](https://docs.ropensci.org/rcrossref/reference/cr_cn.md)

- [`cr_fundref()`](https://docs.ropensci.org/rcrossref/reference/cr_fundref-defunct.md):
  Crossref changed their name "fundref" to "funders", so we've changed
  our function, see
  [`cr_funders()`](https://docs.ropensci.org/rcrossref/reference/cr_funders.md)

- [`cr_ft_text()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_text-defunct.md):
  This function and other text mining functions are incorporated in a
  new package `crminer`.

- [`cr_ft_links()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_links-defunct.md):
  This function and other text mining functions are incorporated in a
  new package `crminer`.

- [`cr_ft_pdf()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_pdf-defunct.md):
  This function and other text mining functions are incorporated in a
  new package `crminer`.

- [`cr_ft_plain()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_plain-defunct.md):
  This function and other text mining functions are incorporated in a
  new package `crminer`.

- [`cr_ft_text()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_text-defunct.md):
  This function and other text mining functions are incorporated in a
  new package `crminer`.

- [`cr_ft_xml()`](https://docs.ropensci.org/rcrossref/reference/cr_ft_xml-defunct.md):
  This function and other text mining functions are incorporated in a
  new package `crminer`.

- [`as.tdmurl()`](https://docs.ropensci.org/rcrossref/reference/as.tdmurl-defunct.md):
  This function and other text mining functions are incorporated in a
  new package `crminer`.

- [`extract_xpdf()`](https://docs.ropensci.org/rcrossref/reference/extract_xpdf-defunct.md):
  This function and other text mining functions are incorporated in a
  new package `crminer`.
