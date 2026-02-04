<div id="main" class="col-md-9" role="main">

# Confidence bands

<div class="ref-description section level2">

Add confidence bands

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_band(
  e,
  min,
  max,
  stack = "confidence-band",
  symbol = c("none", "none"),
  areaStyle = list(list(color = "rgba(0,0,0,0)"), list()),
  legend = list(FALSE, FALSE),
  ...
)

e_band_(
  e,
  min,
  max,
  stack = "confidence-band",
  symbol = c("none", "none"),
  areaStyle = list(list(color = "rgba(0,0,0,0)"), list()),
  legend = list(FALSE, FALSE),
  ...
)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   min, max:

    series.

-   stack:

    Name of stack.

-   symbol:

    Whether to show symbols on lower and upper band lines.

-   areaStyle:

    The style of lower and upper bands, i.e.: color.

-   legend:

    Whether to show `min` and `max` in legend.

-   ...:

    All options must be of vectors or lists of length 2 where the first
    argument is for the lower bound and the second for the upper bound,
    see examples.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(
  x = 1:10,
  y = runif(10, 5, 10)
) |>
  dplyr::mutate(
    lwr = y - runif(10, 1, 3),
    upr = y + runif(10, 2, 4)
  )

df |>
  e_charts(x) |>
  e_line(y) |>
  e_band(lwr, upr)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"type":"category"}],"legend":{"data":["y"]},"series":[{"data":[{"value":[1,9.712029489455745]},{"value":[2,8.273902086075395]},{"value":[3,9.718653876334429]},{"value":[4,5.35084204049781]},{"value":[5,5.359867089428008]},{"value":[6,6.731293258490041]},{"value":[7,9.176327877212316]},{"value":[8,7.240026692161337]},{"value":[9,9.337397053604946]},{"value":[10,5.113887310726568]}],"yAxisIndex":0,"xAxisIndex":0,"name":"y","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,6.720879852538928]},{"value":[2,6.954618339426816]},{"value":[3,8.641919273883104]},{"value":[4,3.025244214572012]},{"value":[5,4.35866085300222]},{"value":[6,4.781416568206623]},{"value":[7,6.935168103780597]},{"value":[8,5.303894304903224]},{"value":[9,7.475740438560024]},{"value":[10,3.139641279121861]}],"yAxisIndex":0,"xAxisIndex":0,"name":"lwr","type":"line","coordinateSystem":"cartesian2d","lineStyle":{"normal":{"opacity":0}},"symbol":"none","areaStyle":{"color":"rgba(0,0,0,0)"},"stack":"confidence-band"},{"data":[{"value":[1,6.480287220794708]},{"value":[2,3.791436417028308]},{"value":[3,4.069688166491687]},{"value":[4,4.589779764879495]},{"value":[5,4.328062675427645]},{"value":[6,4.385108711197972]},{"value":[7,5.725471286568791]},{"value":[8,4.011707448400557]},{"value":[9,5.165251004043967]},{"value":[10,4.643017379101366]}],"yAxisIndex":0,"xAxisIndex":0,"name":"upr","type":"line","coordinateSystem":"cartesian2d","lineStyle":{"normal":{"opacity":0}},"symbol":"none","areaStyle":[],"stack":"confidence-band"}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
