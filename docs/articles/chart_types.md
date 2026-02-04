<div id="main" role="main">

# Chart Types

This document include the *standard* chart types *only*.

<div class="section level2">

## Line and Area

<div id="cb1" class="sourceCode">

``` r
library(echarts4r)

df <- data.frame(
  x = seq(50),
  y = rnorm(50, 10, 3),
  z = rnorm(50, 11, 2),
  w = rnorm(50, 9, 2)
)

df |> 
  e_charts(x) |> 
  e_line(z) |> 
  e_area(w) |> 
  e_title("Line and area charts")
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Bar and step

<div id="cb2" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_bar(y, name = "Serie 1") |> 
  e_step(z, name = "Serie 2") |> 
  e_title("Bar and step charts")
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Scatter

<div id="cb3" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_scatter(y, z) |> 
  e_visual_map(z, scale = e_scale) |> # scale color
  e_legend(FALSE) # hide legend
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Effect Scatter

<div id="cb4" class="sourceCode">

``` r
df |> 
  head(10) |> 
  e_charts(x) |> 
  e_effect_scatter(y, z) |> 
  e_visual_map(z) |> # scale color
  e_legend(FALSE) # hide legend
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Polar

<div id="cb5" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_polar() |> 
  e_angle_axis(x) |> # angle = x
  e_radius_axis() |> 
  e_bar(y, coord_system = "polar") |> 
  e_scatter(z, coord_system = "polar")
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Radial

<div id="cb6" class="sourceCode">

``` r
df |> 
  head(10) |> 
  e_charts(x) |> 
  e_polar() |> 
  e_angle_axis() |> 
  e_radius_axis(x) |> 
  e_bar(y, coord_system = "polar") |> 
  e_scatter(z, coord_system = "polar")
```

</div>

<div id="htmlwidget-10b3b7155e8045a1b2ad"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Candlestick

<div id="cb7" class="sourceCode">

``` r
library(quantmod)

getSymbols("GS") #Goldman Sachs
GS <- as.data.frame(GS)
GS$date <- row.names(GS)
```

</div>

<div id="cb8" class="sourceCode">

``` r
GS |> 
  e_charts(date) |> 
  e_candle(GS.Open, GS.Close, GS.Low, GS.High, name = "Goldman Sachs") |> 
  e_datazoom(type = "slider") |> 
  e_title("Candlestick chart", "Quantmod data")
```

</div>

<div id="htmlwidget-4018eef1a407a0df6b52"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Funnel

<div id="cb9" class="sourceCode">

``` r
funnel <- data.frame(stage = c("View", "Click", "Purchase"), value = c(80, 30, 20))

funnel |> 
  e_charts() |> 
  e_funnel(value, stage) |> 
  e_title("Funnel")
```

</div>

<div id="htmlwidget-5b1b2f4ad92281566982"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Sankey

<div id="cb10" class="sourceCode">

``` r
sankey <- data.frame(
  source = c("a", "b", "c", "d", "c"),
  target = c("b", "c", "d", "e", "e"),
  value = ceiling(rnorm(5, 10, 1)),
  stringsAsFactors = FALSE
)

sankey |> 
  e_charts() |> 
  e_sankey(source, target, value) |> 
  e_title("Sankey chart")
```

</div>

<div id="htmlwidget-25c3e940e6859592f801"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Heatmap

<div id="cb11" class="sourceCode">

``` r
v <- LETTERS[1:10]
matrix <- data.frame(
  x = sample(v, 300, replace = TRUE), 
  y = sample(v, 300, replace = TRUE), 
  z = rnorm(300, 10, 1),
  stringsAsFactors = FALSE
) |> 
  dplyr::group_by(x, y) |> 
  dplyr::summarise(z = sum(z)) |> 
  dplyr::ungroup()
#> `summarise()` has grouped output by 'x'. You can override using the `.groups`
#> argument.

matrix |> 
  e_charts(x) |> 
  e_heatmap(y, z) |> 
  e_visual_map(z) |> 
  e_title("Heatmap")
```

</div>

<div id="htmlwidget-3f27c09be0c60bb52829"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Parallel

<div id="cb12" class="sourceCode">

``` r
df <- data.frame(
  price = rnorm(5, 10),
  amount = rnorm(5, 15),
  letter = LETTERS[1:5]
)

df |> 
  e_charts() |> 
  e_parallel(price, amount, letter) |> 
  e_title("Parallel chart")
```

</div>

<div id="htmlwidget-416566eb193bf50d04e6"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Pie

<div id="cb13" class="sourceCode">

``` r
mtcars |> 
  head() |> 
  tibble::rownames_to_column("model") |> 
  e_charts(model) |> 
  e_pie(carb) |> 
  e_title("Pie chart")
```

</div>

<div id="htmlwidget-72cbf064100ce560a04c"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Donut

<div id="cb14" class="sourceCode">

``` r
mtcars |> 
  head() |> 
  tibble::rownames_to_column("model") |> 
  e_charts(model) |> 
  e_pie(carb, radius = c("50%", "70%")) |> 
  e_title("Donut chart")
```

</div>

<div id="htmlwidget-d11fc4360aa0230696d7"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Rosetype

<div id="cb15" class="sourceCode">

``` r
mtcars |> 
  head() |> 
  tibble::rownames_to_column("model") |> 
  e_charts(model) |> 
  e_pie(hp, roseType = "radius")
```

</div>

<div id="htmlwidget-21c7483268bafca56cec"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Sunburst

<div id="cb16" class="sourceCode">

``` r
df <- data.frame(
  parents = c("","earth", "earth", "mars", "mars", "land", "land", "ocean", "ocean", "fish", "fish", "Everything", "Everything", "Everything"),
  labels = c("Everything", "land", "ocean", "valley", "crater", "forest", "river", "kelp", "fish", "shark", "tuna", "venus","earth", "mars"),
  value = c(0, 30, 40, 10, 10, 20, 10, 20, 20, 8, 12, 10, 70, 20)
)

# create a tree object
universe <- data.tree::FromDataFrameNetwork(df)

# use it in echarts4r
universe |> 
  e_charts() |> 
  e_sunburst()
```

</div>

<div id="htmlwidget-1834a22cd196f3aa03a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Tree

<div id="cb17" class="sourceCode">

``` r
library(tibble)
#> Warning: package 'tibble' was built under R version 4.5.2

tree <- tibble(
  name = "earth",        # 1st level
  children = list(
    tibble(name = c("land", "ocean"),             # 2nd level
       children = list(
         tibble(name = c("forest", "river")),   # 3rd level 
         tibble(name = c("fish", "kelp"),
            children = list(
               tibble(name = c("shark", "tuna")),  # 4th level 
               NULL  # kelp
            )
         )
       ))
  )
)

tree |> 
  e_charts() |> 
  e_tree() |> 
  e_title("Tree graph")
```

</div>

<div id="htmlwidget-28515d92cb327f90c9eb"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Treemap

<div id="cb18" class="sourceCode">

``` r
universe |> 
  e_charts() |> 
  e_treemap() |> 
  e_title("Treemap chart")
```

</div>

<div id="htmlwidget-0caf26d4e3c00206b0c5"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## River

<div id="cb19" class="sourceCode">

``` r
dates <- seq.Date(Sys.Date() - 30, Sys.Date(), by = "day")

river <- data.frame(
  dates = dates,
  apples = runif(length(dates)),
  bananas = runif(length(dates)),
  pears = runif(length(dates))
)

river |> 
  e_charts(dates) |> 
  e_river(apples) |> 
  e_river(bananas) |> 
  e_river(pears) |> 
  e_tooltip(trigger = "axis") |> 
  e_title("River charts", "(Streamgraphs)")
```

</div>

<div id="htmlwidget-da0b268a2927f570ebf3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Calendar

<div id="cb20" class="sourceCode">

``` r
dates <- seq.Date(as.Date("2017-01-01"), as.Date("2018-12-31"), by = "day")
values <- rnorm(length(dates), 20, 6)

year <- data.frame(date = dates, values = values)

year |> 
  e_charts(date) |> 
  e_calendar(range = "2018") |> 
  e_heatmap(values, coord_system = "calendar") |> 
  e_visual_map(max = 30) |> 
  e_title("Calendar", "Heatmap")
```

</div>

<div id="htmlwidget-0ed12bb554391c49c2e3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

For multiple years, lay multiple calendars, group by year.

<div id="cb21" class="sourceCode">

``` r
year |> 
  dplyr::mutate(year = format(date, "%Y")) |> # get year from date
  group_by(year) |> 
  e_charts(date) |> 
  e_calendar(range = "2017",top="40") |> 
  e_calendar(range = "2018",top="260") |> 
  e_heatmap(values, coord_system = "calendar") |> 
  e_visual_map(max = 30) |> 
  e_title("Calendar", "Heatmap")|>
  e_tooltip("item") 
```

</div>

<div id="htmlwidget-ec658d41f8c4f2d124e9"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Gauge

<div id="cb22" class="sourceCode">

``` r
e_charts() |> 
  e_gauge(41, "PERCENT") |> 
  e_title("Gauge")
```

</div>

<div id="htmlwidget-6b83523733b890d61edc"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Radar

<div id="cb23" class="sourceCode">

``` r
df <- data.frame(
  x = LETTERS[1:5],
  y = runif(5, 1, 5),
  z = runif(5, 3, 7)
)

df |> 
  e_charts(x) |> 
  e_radar(y, max = 7, name = "radar") |>
  e_radar(z, max = 7, name = "chart") |>
  e_tooltip(trigger = "item")
```

</div>

<div id="htmlwidget-b3f7c917b6c8ff580948"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Wordcloud

<div id="cb24" class="sourceCode">

``` r
words <- function(n = 5000) {
  a <- do.call(paste0, replicate(5, sample(LETTERS, n, TRUE), FALSE))
  paste0(a, sprintf("%04d", sample(9999, n, TRUE)), sample(LETTERS, n, TRUE))
}

tf <- data.frame(terms = words(100), 
  freq = rnorm(100, 55, 10)) |> 
  dplyr::arrange(-freq)

tf |> 
  e_color_range(freq, color) |> 
  e_charts() |> 
  e_cloud(terms, freq, color, shape = "circle", sizeRange = c(3, 15)) |> 
  e_title("Wordcloud", "Random strings")
```

</div>

<div id="htmlwidget-d258b2ee1c304ebe1664"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Liquifill

<div id="cb25" class="sourceCode">

``` r
liquid <- data.frame(val = c(0.6, 0.5, 0.4))

liquid |> 
  e_charts() |> 
  e_liquid(val) 
```

</div>

<div id="htmlwidget-b8f31ebacaee3527bb86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Chord

<div id="cb26" class="sourceCode">

``` r
chord_data <- data.frame(
  source = c("a", "b", "c", "d", "c"),
  target = c("b", "c", "d", "e", "e"),
  value = ceiling(rnorm(5, 10, 1)),
  stringsAsFactors = FALSE
)

chord_data |>
  e_charts() |>
  e_chord(source, target, value)
```

</div>

<div id="htmlwidget-b25b670b028f478bf741"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Doughnut

<div id="cb27" class="sourceCode">

``` r
 e_chart() |>
  e_doughnut(numerator = 3, denominator = 6)
```

</div>

<div id="htmlwidget-46d1193f7ba074d981c8"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Violin

<div id="cb28" class="sourceCode">

``` r
PlantGrowth |>
  e_charts(group) |>
  e_scatter(weight) |>
  e_violin(binCount = 200)
```

</div>

<div id="htmlwidget-382a200f56fb8e6a1fd3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Bar Range

<div id="cb29" class="sourceCode">

``` r
df <- iris |>
  dplyr::group_by(Species) |>
  dplyr::summarise(min_length = min(Sepal.Length),
                   max_length = max(Sepal.Length))

df |> e_chart(Species) |>
  e_barRange(lower = min_length,
             upper = max_length,
             textSymbol = '"'
  )
```

</div>

<div id="htmlwidget-da403bf8187c892ade73"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Contour

<div id="cb30" class="sourceCode">

``` r
mtcars |>
 e_charts(mpg) |>
 e_contour(serie = mpg)
```

</div>

<div id="htmlwidget-756e3bf13eb93ebd21f9"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Line Range

<div id="cb31" class="sourceCode">

``` r
df <- iris |>
  dplyr::group_by(Species) |>
  dplyr::summarise(lower = min(Sepal.Length),
                   upper = max(Sepal.Length))
df |>
  e_chart(Species) |>
  e_lineRange(lower = lower, upper = upper)
```

</div>

<div id="htmlwidget-2931a41253ddcd61f464"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Stage

<div id="cb32" class="sourceCode">

``` r
df <- data.frame(
  start = as.POSIXct(c(
    "2024-09-07 06:12", "2024-09-07 06:15", "2024-09-07 05:45",
    "2024-09-07 04:57", "2024-09-07 06:12", "2024-09-07 06:18"
  )),

  end = as.POSIXct(c(
    "2024-09-07 06:12", "2024-09-07 06:18", "2024-09-07 06:12",
    "2024-09-07 05:45", "2024-09-07 06:15", "2024-09-07 07:37"
  )),

  stage = c(
    "Awake", "Awake",  "REM",
    "Core", "Core", "Deep"
  ),
  stringsAsFactors = FALSE
 )
stage_order <- c( "Deep", "Core","REM", "Awake")

df |>
  e_charts() |>
  e_stage(start = start,
          end = end,
          stage = stage) |>
          e_x_axis(type = 'time') |>
          e_y_axis(type = 'category', data = stage_order)
```

</div>

<div id="htmlwidget-853270d7a7ddd5c78dff"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
