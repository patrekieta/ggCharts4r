<div id="main" class="col-md-9" role="main">

# Country names

<div class="ref-description section level2">

Convert country names to echarts format.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_country_names(data, input, output, type = "iso2c", ...)

e_country_names_(data, input, output = NULL, type = "iso2c", ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   data:

    Data.frame in which to find column names.

-   input, output:

    Input and output columns.

-   type:

    Passed to
    [countrycode](https://vincentarelbundock.github.io/countrycode/reference/countrycode.html)
    `origin` parameter.

-   ...:

    Any other parameter to pass to
    [countrycode](https://vincentarelbundock.github.io/countrycode/reference/countrycode.html).

</div>

<div class="section level2">

## Details

Taiwan and Hong Kong cannot be plotted.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
cns <- data.frame(country = c("US", "BE"))

# replace
e_country_names(cns, country)
#>         country
#> 1 United States
#> 2       Belgium

# specify output
e_country_names(cns, country, country_name)
#>   country  country_name
#> 1      US United States
#> 2      BE       Belgium
```

</div>

</div>

</div>
