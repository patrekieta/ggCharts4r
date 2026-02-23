<div id="main" class="col-md-9" role="main">

# Axis ZigZags

<div class="ref-description section level2">

helper function for generating axis break zigzags in chart

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_zigzag(e, axis = "y", start, end, gap = "3%", zigzagAmplitude = 10, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   axis:

    Axis to apply formatter to. Supports x and y axis

-   start, end:

    Start and End point for boundary of zigzag. Also supports vectors
    for generating multiple breaks. Can also support time values.

-   gap:

    Determines the visual size of the axis break area. Supports
    Percentage(String) as proportional value relative to axis. Supports
    Absolute value(numeric) which refers to literal values in the axis
    similar to start,end (Not a pixel value).

-   zigzagAmplitude:

    Amplitude of zigzag. Unit is pixels.

-   ...:

    Any other arguments to pass to breakArea argument.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#series-bar)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(
              x = c("a", "b", "c", "d", "c"),
              y = c(100, 200, 200, 700, 300)
             )

df |>
  e_charts(x) |>
  e_bar(y) |>
  e_zigzag(axis = 'y', start = 400, end = 500)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"breaks":[{"start":"400","end":"500","gap":"3%"}],"breakArea":{"zigzagAmplitude":10}}],"xAxis":[{"data":["a","b","c","d"],"type":"category","boundaryGap":true}],"legend":{"data":["y"]},"series":[{"data":[{"value":["a","100"]},{"value":["b","200"]},{"value":["c","200"]},{"value":["d","700"]},{"value":["c","300"]}],"name":"y","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d"}]},"dispose":true},"evals":[],"jsHooks":[]}
df |>
  e_charts(x) |>
  e_bar(y) |>
  e_zigzag(axis = 'y', start = c(125,400), end = c(150,500))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"breaks":[{"start":"125","end":"150","gap":"3%"},{"start":"400","end":"500","gap":"3%"}],"breakArea":{"zigzagAmplitude":10}}],"xAxis":[{"data":["a","b","c","d"],"type":"category","boundaryGap":true}],"legend":{"data":["y"]},"series":[{"data":[{"value":["a","100"]},{"value":["b","200"]},{"value":["c","200"]},{"value":["d","700"]},{"value":["c","300"]}],"name":"y","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d"}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
