<div id="main" class="col-md-9" role="main">

# Boxplot

<div class="ref-description section level2">

Draw boxplot.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_boxplot(e, serie, name = NULL, outliers = TRUE, ...)

e_boxplot_(e, serie, name = NULL, outliers = TRUE, ...)
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

-   name:

    name of the serie.

-   outliers:

    Whether to plot outliers.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#series-boxplot)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(
  x = c(1:10, 25),
  y = c(1:10, -6)
)

df |>
  e_charts() |>
  e_boxplot(y, outliers = TRUE) |>
  e_boxplot(x, outliers = TRUE)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"series":[{"name":"y","type":"boxplot","data":[[1,2.5,5,7.5,10],[1,3.5,6,8.5,10]]},{"type":"scatter","data":[[0,-6],[1,25]]}],"xAxis":[{"data":["y","x"],"type":"category"}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
