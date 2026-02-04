<div id="main" class="col-md-9" role="main">

# Liquid fill

<div class="ref-description section level2">

Draw liquid fill.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_liquid(e, serie, color, rm_x = TRUE, rm_y = TRUE, ...)

e_liquid_(e, serie, color = NULL, rm_x = TRUE, rm_y = TRUE, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   serie:

    Column name of serie to plot.

-   color:

    Column of color to plot.

-   rm_x, rm_y:

    Whether to remove x and y axis, defaults to `TRUE`.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[official documentation](https://github.com/ecomfe/echarts-liquidfill)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(val = c(0.6, 0.5, 0.4))

df |>
  e_charts() |>
  e_liquid(val) |>
  e_theme("dark")

{"x":{"theme":"dark","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"series":[{"type":"liquidFill","data":[0.6,0.5,0.4]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
