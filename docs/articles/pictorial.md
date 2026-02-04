<div id="main" role="main">

# Pictorial

Pictorial bar chart is a type of bar chart that custimzed glyph (like
images, SVG PathData) can be used instead of rectangular bar. This kind
of chart is usually used in infographic.

<div class="section level2">

## Built-in symbols

<div id="cb1" class="sourceCode">

``` r
y <- rnorm(10, 10, 2)
df <- data.frame(
  x = 1:10,
  y = y,
  z = y - rnorm(10, 5, 1)
)

df |> 
  e_charts(x) |> 
  e_bar(z, barWidth = 10) |> 
  e_pictorial(y, symbol = "rect", symbolRepeat = TRUE, z = -1,
    symbolSize = c(10, 4)) |> 
  e_theme("westeros") |> 
  e_title("Built-in symbols")
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Icons

[echarts4r.assets](https://echarts4r-assets.john-coene.com) now includes
icons you can easily include in your plots.

<div id="cb2" class="sourceCode">

``` r
library(echarts4r.assets)

mtcars |> 
  e_charts(mpg) |> 
  e_scatter(
    wt, 
    qsec,
    symbol = ea_icons("trash"),
    name = "Trash"
  ) |> 
  e_legend(icons = ea_icons("trash"))
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## SVG path

<div id="cb3" class="sourceCode">

``` r
path <- "path://M0,10 L10,10 C5.5,10 5.5,5 5,0 C4.5,5 4.5,10 0,10 z"

style <- list(
  normal = list(opacity = 0.5), # normal
  emphasis = list(opacity = 1) # on hover
)

df |> 
  e_charts(x) |> 
  e_pictorial(y, symbol = path, 
              barCategoryGap = "-130%", 
              itemStyle = style) |> 
  e_title("SVG path")
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Images

<div id="cb4" class="sourceCode">

``` r
qomo <- paste0(
  "https://echarts.apache.org/examples/",
  "data/asset/img/hill-Qomolangma.png"
)

kili <- paste0(
  "https://echarts.apache.org/examples/", 
  "data/asset/img/hill-Kilimanjaro.png"
)

data <- data.frame(
  x = c("Qomolangma", "Kilimanjaro"), 
  value = c(8844, 5895),
  symbol = c(paste0("image://", qomo),
    paste0("image://", kili))
)

data |> 
  e_charts(x) |> 
  e_pictorial(value, symbol) |> 
  e_legend(FALSE) |> 
  e_title("Images", "Mountains height")
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
