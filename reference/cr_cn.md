# Get citations in various formats from CrossRef.

Get citations in various formats from CrossRef.

## Usage

``` r
cr_cn(
  dois,
  format = "bibtex",
  style = "apa",
  locale = "en-US",
  raw = FALSE,
  .progress = "none",
  url = NULL,
  cache = FALSE,
  ...
)
```

## Arguments

- dois:

  Search by a single DOI or many DOIs.

- format:

  Name of the format. One of "rdf-xml", "turtle", "citeproc-json",
  "citeproc-json-ish", "text", "ris", "bibtex" (default),
  "crossref-xml", "datacite-xml","bibentry", or "crossref-tdm". The
  format "citeproc-json-ish" is a format that is not quite proper
  citeproc-json. Note that the package bibtex is required when
  `format="bibtex"`; the package is in Suggests so is not required when
  installing rcrossref

- style:

  a CSL style (for text format only). See
  [`get_styles()`](https://docs.ropensci.org/rcrossref/reference/get_styles.md)
  for options. Default: 'apa'. If there's a style that CrossRef doesn't
  support you'll get a `(500) Internal Server Error`

- locale:

  Language locale. See
  [`?Sys.getlocale`](https://rdrr.io/r/base/locales.html)

- raw:

  (logical) Return raw text in the format given by `format` parameter.
  Default: `FALSE`

- .progress:

  Show a `plyr`-style progress bar? Options are "none", "text", "tk",
  "win", and "time". See
  [`create_progress_bar`](https://rdrr.io/pkg/plyr/man/create_progress_bar.html)
  for details of each. Only used when passing in multiple ids (e.g.,
  multiple DOIs, DOI prefixes, etc.), or when using the `cursor` param.
  When using the `cursor` param, this argument only accept a boolean,
  either `TRUE` or `FALSE`; any non-boolean is coerced to `FALSE`.

- url:

  (character) Base URL for the content negotiation request. Default:
  "https://doi.org"

- cache:

  (logical) Should requests be cached and/or retrieved from the cache?
  Note that the cache only persists while the package is loaded.

- ...:

  Named parameters passed on to
  [`verb-GET`](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Details

See http://citation.crosscite.org/docs.html for more info on the
Crossref Content Negotiation API service.

DataCite DOIs: Some values of the `format` parameter won't work with
DataCite DOIs, i.e. "citeproc-json", "crossref-xml", "crossref-tdm",
"onix-xml".

MEDRA DOIs only work with "rdf-xml", "turtle", "citeproc-json-ish",
"ris", "bibtex", "bibentry", "onix-xml".

See examples below.

See
[`cr_agency()`](https://docs.ropensci.org/rcrossref/reference/cr_agency.md)

Note that the format type `citeproc-json` uses the CrossRef API at
`api.crossref.org`, while all others are content negotiated via
`http://data.crossref.org`, `http://data.datacite.org` or
`http://data.medra.org`. DOI agency is checked first (see
[`cr_agency()`](https://docs.ropensci.org/rcrossref/reference/cr_agency.md)).

## Examples

``` r
if (FALSE) { # \dontrun{
cr_cn(dois="10.1126/science.169.3946.635")
cr_cn(dois="10.1126/science.169.3946.635", "citeproc-json")
cr_cn(dois="10.1126/science.169.3946.635", "citeproc-json-ish")
cr_cn("10.1126/science.169.3946.635", "rdf-xml")
cr_cn("10.1126/science.169.3946.635", "crossref-xml")
cr_cn("10.1126/science.169.3946.635", "text")

# return an R bibentry type
cr_cn("10.1126/science.169.3946.635", "bibentry")
cr_cn("10.6084/m9.figshare.97218", "bibentry")

# return an apa style citation
cr_cn("10.1126/science.169.3946.635", "text", "apa")
cr_cn("10.1126/science.169.3946.635", "text", "harvard3")
cr_cn("10.1126/science.169.3946.635", "text", "elsevier-harvard")
cr_cn("10.1126/science.169.3946.635", "text", "ecoscience")
cr_cn("10.1126/science.169.3946.635", "text", "heredity")
cr_cn("10.1126/science.169.3946.635", "text", "oikos")

# example with many DOIs
dois <- cr_r(2)
cr_cn(dois, "text", "apa")

# Cycle through random styles - print style on each try
stys <- get_styles()
foo <- function(x){
 cat(sprintf("<Style>:%s\n", x), sep = "\n\n")
 cat(cr_cn("10.1126/science.169.3946.635", "text", style=x))
}
foo(sample(stys, 1))

# Using DataCite DOIs
## some formats don't work
# cr_cn("10.5284/1011335", "crossref-xml")
# cr_cn("10.5284/1011335", "crossref-tdm")
## But most do work
cr_cn("10.5284/1011335", "text")
cr_cn("10.5284/1011335", "datacite-xml")
cr_cn("10.5284/1011335", "rdf-xml")
cr_cn("10.5284/1011335", "turtle")
cr_cn("10.5284/1011335", "citeproc-json-ish")
cr_cn("10.5284/1011335", "ris")
cr_cn("10.5284/1011335", "bibtex")
cr_cn("10.5284/1011335", "bibentry")

# Using Medra DOIs
cr_cn("10.1430/8105", "onix-xml")

# Get raw output
cr_cn(dois = "10.1002/app.27716", format = "citeproc-json", raw = TRUE)

# sometimes messy DOIs even work
## in this case, a DOI minting agency can't be found
## but we proceed anyway, just assuming it's "crossref"
cr_cn("10.1890/0012-9615(1999)069[0569:EDILSA]2.0.CO;2")

# Use a different base url
cr_cn("10.1126/science.169.3946.635", "text", url = "http://dx.doi.org")
cr_cn("10.1126/science.169.3946.635", "text", "heredity", url = "http://dx.doi.org")
cr_cn("10.5284/1011335", url = "https://citation.crosscite.org/format",
   style = "oikos")
cr_cn("10.5284/1011335", url = "https://citation.crosscite.org/format",
   style = "plant-cell-and-environment")

# A temporary cache can be used to avoid sending the same request repeatedly
# within the same R session.
cr_cn("10.5284/1011335", cache = TRUE)
} # }
```
