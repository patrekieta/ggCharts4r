<div id="main" class="col-md-9" role="main">

# Color range

<div class="ref-description section level2">

Build manual color range

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_color_range(
  data,
  input,
  output,
  colors = c("#bf444c", "#d88273", "#f6efa6"),
  ...
)

e_color_range_(
  data,
  input,
  output,
  colors = c("#bf444c", "#d88273", "#f6efa6"),
  ...
)
```

</div>

</div>

<div class="section level2">

## Arguments

-   data:

    Data.frame in which to find column names.

-   input, output:

    Input and output columns.

-   colors:

    Colors to pass to `colorRampPalette`.

-   ...:

    Any other argument to pass to `colorRampPalette`.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(val = 1:10)

e_color_range(df, val, colors)
#>    val  colors
#> 1    1 #BF444C
#> 2    2 #C55354
#> 3    3 #CB615D
#> 4    4 #D06E66
#> 5    5 #D57B6F
#> 6    6 #DC8E79
#> 7    7 #E4A784
#> 8    8 #EBBF8F
#> 9    9 #F1D79A
#> 10  10 #F6EFA6
```

</div>

</div>

</div>
