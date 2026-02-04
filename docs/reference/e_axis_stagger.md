<div id="main" class="col-md-9" role="main">

# Stagger Axis Labels

<div class="ref-description section level2">

Stagger axis labels.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_axis_stagger(e)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(
  x = c("a very long label", "Another long label"),
  y = 1:2
)

df |>
  e_charts(x, width = 150) |>
  e_bar(y) |>
  e_axis_stagger()

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"data":["a very long label","Another long label"],"type":"category","boundaryGap":true,"axisLabel":{"formatter":"function(value, index){\n    if(index % 2){\n      return('\\n' + value)\n    }\n\n    return(value)\n  }"}}],"legend":{"data":["y"]},"series":[{"data":[{"value":["a very long label","1"]},{"value":["Another long label","2"]}],"name":"y","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d"}]},"dispose":true},"evals":["opts.xAxis.0.axisLabel.formatter"],"jsHooks":[]}
```

</div>

</div>

</div>
