<div id="main" class="col-md-9" role="main">

# Flip coordinates

<div class="ref-description section level2">

Flip cartesian 2D coordinates.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_flip_coords(e)
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
  x = LETTERS[1:5],
  y = runif(5, 1, 5),
  z = runif(5, 3, 10)
)

df |>
  e_charts(x) |>
  e_bar(y) |>
  e_line(z) -> plot

plot # normal

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"data":["A","B","C","D","E"],"type":"category","boundaryGap":true}],"legend":{"data":["y","z"]},"series":[{"data":[{"value":["A","2.556350"]},{"value":["B","2.926332"]},{"value":["C","3.828305"]},{"value":["D","3.347530"]},{"value":["E","4.229464"]}],"name":"y","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d"},{"data":[{"value":["A","5.622080"]},{"value":["B","5.926922"]},{"value":["C","7.874934"]},{"value":["D","6.709102"]},{"value":["E","9.626961"]}],"yAxisIndex":0,"xAxisIndex":0,"name":"z","type":"line","coordinateSystem":"cartesian2d"}]},"dispose":true},"evals":[],"jsHooks":[]}e_flip_coords(plot) # flip

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"xAxis":[{"show":true}],"yAxis":[{"data":["A","B","C","D","E"],"type":"category","boundaryGap":true}],"legend":{"data":["y","z"]},"series":[{"data":[{"value":["2.556350","A"]},{"value":["2.926332","B"]},{"value":["3.828305","C"]},{"value":["3.347530","D"]},{"value":["4.229464","E"]}],"name":"y","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d"},{"data":[{"value":["5.622080","A"]},{"value":["5.926922","B"]},{"value":["7.874934","C"]},{"value":["6.709102","D"]},{"value":["9.626961","E"]}],"yAxisIndex":0,"xAxisIndex":0,"name":"z","type":"line","coordinateSystem":"cartesian2d"}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
