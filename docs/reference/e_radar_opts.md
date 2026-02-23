<div id="main" class="col-md-9" role="main">

# Radar axis

<div class="ref-description section level2">

Radar axis setup and options.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_radar_opts(e, index = 0, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   index:

    Index of axis to customise.

-   ...:

    Any other option to pass, check See Also section.

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
  e_radar_opts(center = c("25%", "25%")) |>
  e_tooltip(trigger = "item")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"radar":[{"indicator":[{"name":"A","max":"7"},{"name":"B","max":"7"},{"name":"C","max":"7"},{"name":"D","max":"7"},{"name":"E","max":"7"}],"center":["25%","25%"]}],"series":[{"type":"radar","data":[{"value":[2.320630583912134,2.086617673747241,3.999835765920579,3.448582136072218,3.628747564740479],"name":"y"},{"value":[3.950491623021662,6.536196880042553,6.516848317347467,4.501920194365084,6.439912614412606],"name":"z"}],"radarIndex":0}],"legend":{"data":["y","z"]},"tooltip":{"trigger":"item"}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
