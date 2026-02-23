<div id="main" class="col-md-9" role="main">

# Formatters

<div class="ref-description section level2">

Simple formatters as helpers.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_format_axis(e, axis = "y", suffix = NULL, prefix = NULL, ...)

e_format_x_axis(e, suffix = NULL, prefix = NULL, ...)

e_format_y_axis(e, suffix = NULL, prefix = NULL, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   axis:

    Axis to apply formatter to.

-   suffix, prefix:

    Suffix and prefix of label.

-   ...:

    Any other arguments to pass to `e_axis`.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
# Y = %
df <- data.frame(
  x = 1:10,
  y = round(
    runif(10, 1, 100),
    2
  )
)

df |>
  e_charts(x) |>
  e_line(y) |>
  e_format_y_axis(suffix = "%") |>
  e_format_x_axis(prefix = "A")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"axisLabel":{"formatter":" {value} %"}}],"xAxis":[{"type":"value","axisLabel":{"formatter":"A {value} "}}],"legend":{"data":["y"]},"series":[{"data":[{"value":[1,30.64]},{"value":[2,53.5]},{"value":[3,9.02]},{"value":[4,88.31999999999999]},{"value":[5,23.68]},{"value":[6,4.18]},{"value":[7,93.58]},{"value":[8,98.56999999999999]},{"value":[9,72.41]},{"value":[10,58.66]}],"yAxisIndex":0,"xAxisIndex":0,"name":"y","type":"line","coordinateSystem":"cartesian2d"}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
