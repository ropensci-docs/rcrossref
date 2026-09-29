# Get a random set of DOI's through CrossRef.

Get a random set of DOI's through CrossRef.

## Usage

``` r
cr_r(sample = 10, ...)
```

## Arguments

- sample:

  The number of returned random DOIs. Maximum: 100. Default: 20.

- ...:

  Further args passed on to
  [`cr_works()`](https://docs.ropensci.org/rcrossref/reference/cr_works.md)

## Value

A character vector of DOIs

## Author

Scott Chamberlain <myrmecocystus@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
# Default search gets 10 random DOIs
cr_r()

# Get 30 DOIs
cr_r(30)
} # }
```
