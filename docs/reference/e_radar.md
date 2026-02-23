<div id="main" class="col-md-9" role="main">

# Radar

<div class="ref-description section level2">

Add a radar chart

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_radar(
  e,
  serie,
  max = 100,
  name = NULL,
  legend = TRUE,
  rm_x = TRUE,
  rm_y = TRUE,
  ...,
  radar = list()
)

e_radar_(
  e,
  serie,
  max = 100,
  name = NULL,
  legend = TRUE,
  rm_x = TRUE,
  rm_y = TRUE,
  ...,
  radar = list()
)
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

-   max:

    Maximum value.

-   name:

    name of the serie.

-   legend:

    Whether to add serie to legend.

-   rm_x, rm_y:

    Whether to remove x and y axis, defaults to `TRUE`.

-   ...:

    Any other option to pass, check See Also section.

-   radar:

    A `list` of options to pass to the `radar` rather than the serie,
    see [official
    documentation](https://echarts.apache.org/en/option.html#radar)
    alternatively, use the `e_radar_opts`.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(
  x = LETTERS[1:5],
  y = runif(5, 1, 5),
  z = runif(5, 3, 7)
)

df |>
  e_charts(x) |>
  e_radar(y, max = 7) |>
  e_radar(z) |>
  e_tooltip(trigger = "item")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"radar":[{"indicator":[{"name":"A","max":"7"},{"name":"B","max":"7"},{"name":"C","max":"7"},{"name":"D","max":"7"},{"name":"E","max":"7"}]}],"series":[{"type":"radar","data":[{"value":[4.686408122070134,1.740797747857869,4.199765197001398,1.341521601192653,4.689943125471473],"name":"y"},{"value":[6.170177514664829,4.373845785856247,3.619638945907354,4.679578265175223,4.531138227321208],"name":"z"}],"radarIndex":0}],"legend":{"data":["y","z"]},"tooltip":{"trigger":"item"}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
