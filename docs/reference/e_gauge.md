<div id="main" class="col-md-9" role="main">

# Gauge

<div class="ref-description section level2">

Plot a gauge.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_gauge(e, value, name = NULL, rm_x = TRUE, rm_y = TRUE, ...)

e_gauge_(e, value, name = NULL, rm_x = TRUE, rm_y = TRUE, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   value:

    Value to gauge.

-   name:

    Text on gauge.

-   rm_x, rm_y:

    Whether to remove x and y axis, defaults to `TRUE`.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#series-gauge)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
e_charts() |>
  e_gauge(57, "PERCENT")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"series":[{"data":[{"value":57,"name":"PERCENT"}],"type":"gauge"}]},"dispose":true},"evals":[],"jsHooks":[]}
# timeline
data.frame(time = 2015:2017) |>
  group_by(time) |>
  e_charts(timeline = TRUE) |>
  e_gauge(
    c(57, 23, 65),
    c("percent", "percentage", "cases")
  )

{"x":{"theme":"","tl":true,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"baseOption":{"timeline":{"data":["2015","2016","2017"],"axisType":"category"},"series":[{"type":"gauge"}]},"options":[{"series":[{"data":[{"value":57,"name":"percent"}]}]},{"series":[{"data":[{"value":23,"name":"percentage"}]}]},{"series":[{"data":[{"value":65,"name":"cases"}]}]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
