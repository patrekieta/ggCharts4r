<div id="main" role="main">

# Mark Points, Lines & Areas

You can mark points, lines and areas on your chart to emphasise certain
things.

<div class="section level2">

## Type

You mark things by passing a `list` to the `data` argument, this list
can be of many different format, see the [official
documentation](https://echarts.apache.org/en/option.html#series-line.markPoint.data).

One of the format is to pass a `type`:

-   `min`
-   `max`
-   `avg`

<div id="cb1" class="sourceCode">

``` r
max <- list(
  name = "Max",
  type = "max"
)

min <- list(
  name = "Min",
  type = "min"
)

avg <- list(
  type = "average",
  name = "AVG"
)
```

</div>

By default `e_mark_*` is applied to all series.

<div id="cb2" class="sourceCode">

``` r
iris |> 
  group_by(Species) |> 
  e_charts(Sepal.Length) |> 
  e_line(Sepal.Width) |> 
  e_mark_point(data = max) |> 
  e_mark_point(data = min) |> 
  e_mark_point(data = avg)
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

But you can specify one or more serie it should apply apply to.

<div id="cb3" class="sourceCode">

``` r
iris |> 
  group_by(Species) |> 
  e_charts(Sepal.Length) |> 
  e_line(Sepal.Width) |> 
  e_mark_point(serie = "setosa", data = max) |> 
  e_mark_point(serie = c("virginica", "setosa"), data = min) |> 
  e_mark_point(serie = c("virginica", "versicolor"), data = avg)
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Custom

<div id="cb4" class="sourceCode">

``` r
library(dplyr)

# get a random point
(
  point <- iris |> 
    filter(Species == "setosa") |> 
    sample_n(1) |>  
    select(
      xAxis = Sepal.Length,
      yAxis = Sepal.Width,
      value = Petal.Width
    ) |> 
    as.list()
)
#> $xAxis
#> [1] 5.1
#> 
#> $yAxis
#> [1] 3.8
#> 
#> $value
#> [1] 0.4

iris |> 
  group_by(Species) |> 
  e_charts(Sepal.Length) |> 
  e_line(Sepal.Width) |> 
  e_mark_point(serie = "setosa", data = point) |> 
  e_x_axis(min = 4)
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Point

<div id="cb5" class="sourceCode">

``` r
iris |> 
  group_by(Species) |> 
  e_charts(Sepal.Length) |> 
  e_line(Sepal.Width) |> 
  e_mark_point(data = avg) |> 
  e_x_axis(min = 4)
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Line

Horizontally.

<div id="cb6" class="sourceCode">

``` r
iris |> 
  group_by(Species) |> 
  e_charts(Sepal.Length) |> 
  e_line(Sepal.Width) |> 
  e_mark_line(data = avg) |> 
  e_x_axis(min = 4)
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Vertically.

<div id="cb7" class="sourceCode">

``` r
cars |> 
  e_charts(speed) |> 
  e_scatter(dist, symbol_size = 5) |> 
  e_legend(FALSE) |> 
  e_mark_line(data = list(xAxis = 7), title = "Tortoise") |> 
  e_mark_line(data = list(xAxis = 12), title = "Speed Limit") |> 
  e_mark_line(data = list(xAxis = 22), title = "Need for Speed") 
```

</div>

<div id="htmlwidget-10b3b7155e8045a1b2ad"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Area

<div id="cb8" class="sourceCode">

``` r
iris |> 
  group_by(Species) |> 
  e_charts(Sepal.Length) |> 
  e_line(Sepal.Width) |> 
  e_mark_area(
    data = list(
      list(xAxis = "min", yAxis = "min"), 
      list(xAxis = "max", yAxis = "max")
    )
  ) |> 
  e_x_axis(min = 4)
```

</div>

<div id="htmlwidget-4018eef1a407a0df6b52"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
