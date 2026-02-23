<div id="main" class="col-md-9" role="main">

# Pictorial

<div class="ref-description section level2">

Pictorial bar chart is a type of bar chart that customized glyph (like
images, SVG PathData) can be used instead of rectangular bar.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_pictorial(
  e,
  serie,
  symbol,
  bind,
  name = NULL,
  legend = TRUE,
  y_index = 0,
  x_index = 0,
  ...
)

e_pictorial_(
  e,
  serie,
  symbol,
  bind = NULL,
  name = NULL,
  legend = TRUE,
  y_index = 0,
  x_index = 0,
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

-   serie:

    Column name of serie to plot.

-   symbol:

    Symbol to plot.

-   bind:

    Binding between datasets, namely for use of `e_brush`.

-   name:

    name of the serie.

-   legend:

    Whether to add serie to legend.

-   x_index, y_index:

    Indexes of x and y axis.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## Symbols

-   Built-in:

    `circle`, `rect`, `roundRect`, `triangle`, `diamond`, `pin`,
    `arrow`.

-   SVG Path:

    Path data for SVG graphics.

-   Images:

    Path to image, don't forget to precede it with `image://`, see
    examples.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#series-pictorialBar)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
# built-in symbols
y <- rnorm(10, 10, 2)
df <- data.frame(
  x = 1:10,
  y = y,
  z = y - rnorm(10, 5, 1)
)

df |>
  e_charts(x) |>
  e_bar(z, barWidth = 10) |>
  e_pictorial(
    y,
    symbol = "rect",
    symbolRepeat = TRUE,
    z = -1,
    symbolSize = c(10, 4)
  ) |>
  e_theme("westeros")

{"x":{"theme":"westeros","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"type":"value"}],"legend":{"data":["z","y"]},"series":[{"data":[{"value":[1,3.680418325189625]},{"value":[2,2.797482994710832]},{"value":[3,6.870432462126657]},{"value":[4,5.168975050252445]},{"value":[5,5.587862003758179]},{"value":[6,0.9605032733092038]},{"value":[7,5.257642060928768]},{"value":[8,9.670092645280976]},{"value":[9,4.248217727265358]},{"value":[10,6.573344602162518]}],"name":"z","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"cartesian2d","barWidth":10},{"data":[{"value":[1,9.281663461037441]},{"value":[2,8.584655251689309]},{"value":[3,10.76918333141315]},{"value":[4,9.210001117003053]},{"value":[5,9.221908594443505]},{"value":[6,7.253182481733599]},{"value":[7,9.928782089086203]},{"value":[8,11.60929880617437]},{"value":[9,10.04461614082031]},{"value":[10,11.08679857861155]}],"name":"y","type":"pictorialBar","yAxisIndex":0,"xAxisIndex":0,"symbolRepeat":true,"z":-1,"symbolSize":[10,4],"symbol":"rect"}]},"dispose":true},"evals":[],"jsHooks":[]}
# svg path
path <- "path://M0,10 L10,10 C5.5,10 5.5,5 5,0 C4.5,5 4.5,10 0,10 z"

style <- list(
  normal = list(opacity = 0.5),
  # normal
  emphasis = list(opacity = 1) # on hover
)

df |>
  e_charts(x) |>
  e_pictorial(
    y,
    symbol = path,
    barCategoryGap = "-130%",
    itemStyle = style
  )

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"type":"value"}],"legend":{"data":["y"]},"series":[{"data":[{"value":[1,9.281663461037441]},{"value":[2,8.584655251689309]},{"value":[3,10.76918333141315]},{"value":[4,9.210001117003053]},{"value":[5,9.221908594443505]},{"value":[6,7.253182481733599]},{"value":[7,9.928782089086203]},{"value":[8,11.60929880617437]},{"value":[9,10.04461614082031]},{"value":[10,11.08679857861155]}],"name":"y","type":"pictorialBar","yAxisIndex":0,"xAxisIndex":0,"barCategoryGap":"-130%","itemStyle":{"normal":{"opacity":0.5},"emphasis":{"opacity":1}},"symbol":"path://M0,10 L10,10 C5.5,10 5.5,5 5,0 C4.5,5 4.5,10 0,10 z"}]},"dispose":true},"evals":[],"jsHooks":[]}
# image
# might not work in RStudio viewer
# open in browser
qomo <- paste0(
  "https://ecomfe.github.io/echarts-examples/public/",
  "data/asset/img/hill-Qomolangma.png"
)

kili <- paste0(
  "https://ecomfe.github.io/echarts-examples/public/",
  "data/asset/img/hill-Kilimanjaro.png"
)

data <- data.frame(
  x = c("Qomolangma", "Kilimanjaro"),
  value = c(8844, 5895),
  symbol = c(
    paste0("image://", qomo),
    paste0("image://", kili)
  )
)

data |>
  e_charts(x) |>
  e_pictorial(value, symbol) |>
  e_legend(FALSE)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"data":["Qomolangma","Kilimanjaro"],"type":"category","boundaryGap":true}],"legend":{"data":["value"],"show":false,"type":"plain"},"series":[{"data":[{"value":["Qomolangma","8844"],"symbol":"image://https://ecomfe.github.io/echarts-examples/public/data/asset/img/hill-Qomolangma.png"},{"value":["Kilimanjaro","5895"],"symbol":"image://https://ecomfe.github.io/echarts-examples/public/data/asset/img/hill-Kilimanjaro.png"}],"name":"value","type":"pictorialBar","yAxisIndex":0,"xAxisIndex":0}]},"dispose":true},"evals":[],"jsHooks":[]}
# timeline
df <- data.frame(
  x = rep(1:5, 2),
  y = runif(10, 1, 10),
  year = c(
    rep(2017, 5),
    rep(2018, 5)
  )
)

df |>
  group_by(year) |>
  e_charts(x, timeline = TRUE) |>
  e_pictorial(
    y,
    symbol = "rect",
    symbolRepeat = TRUE,
    z = -1,
    symbolSize = c(10, 4)
  )

{"x":{"theme":"","tl":true,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"baseOption":{"yAxis":[{"show":true}],"timeline":{"data":["2017","2018"],"axisType":"category"},"xAxis":[{"type":"value"}],"legend":{"data":["y"]},"series":[{"name":"y","type":"pictorialBar","yAxisIndex":0,"xAxisIndex":0,"symbolRepeat":true,"z":-1,"symbolSize":[10,4]}]},"options":[{"series":[{"data":[{"value":[1,1.075496610719711]},{"value":[2,9.923466887325048]},{"value":[3,8.939253968186677]},{"value":[4,2.90356103470549]},{"value":[5,3.550573884742334]}]}]},{"series":[{"data":[{"value":[1,6.445330921560526]},{"value":[2,9.416053681168705]},{"value":[3,6.853089564479887]},{"value":[4,8.792824093718082]},{"value":[5,4.375954407500103]}]}]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
