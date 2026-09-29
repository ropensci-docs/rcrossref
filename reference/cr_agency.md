# Check the DOI minting agency on one or more dois

Check the DOI minting agency on one or more dois

## Usage

``` r
cr_agency(dois = NULL, .progress = "none", ...)
```

## Arguments

- dois:

  (character) One or more article or organization dois.

- .progress:

  Show a `plyr`-style progress bar? Options are "none", "text", "tk",
  "win", and "time". See
  [`create_progress_bar`](https://rdrr.io/pkg/plyr/man/create_progress_bar.html)
  for details of each. Only used when passing in multiple ids (e.g.,
  multiple DOIs, DOI prefixes, etc.), or when using the `cursor` param.
  When using the `cursor` param, this argument only accept a boolean,
  either `TRUE` or `FALSE`; any non-boolean is coerced to `FALSE`.

- ...:

  Named parameters passed on to
  [`verb-GET`](https://docs.ropensci.org/crul/reference/verb-GET.html)

## References

https://github.com/CrossRef/rest-api-doc

## Author

Scott Chamberlain <myrmecocystus@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
cr_agency(dois = '10.13039/100000001')
cr_agency(
  dois = c('10.13039/100000001','10.13039/100000015','10.5284/1011335'))
} # }
```
