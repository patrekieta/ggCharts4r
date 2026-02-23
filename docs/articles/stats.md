<div id="main" role="main">

# Statistical plots

<div class="section level2">

## Confidence Bands

<div id="cb1" class="sourceCode">

``` r
data <- jsonlite::fromJSON("https://echarts.apache.org/examples/data/asset/data/confidence-band.json")

data |> 
  dplyr::mutate(
    date = as.Date(date, "%Y-%m-%d"),
    l = l + value,
    u = u - value
  ) |> 
  e_charts(date) |> 
  e_line(value, symbol = "none") |> 
  e_band(
    l, u, 
    areaStyle = list(list(color = "grey"), list(color = "grey"))
  )
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Area Bands

<div id="cb2" class="sourceCode">

``` r
data(EuStockMarkets)
as.data.frame(EuStockMarkets) |> dplyr::slice_head(n=200) |>
  dplyr::mutate(day=1:dplyr::n()) |>
  e_charts(day) |>
  e_line(CAC, symbol='none') |>
  e_band2(DAX, FTSE, color='lemonchiffon') |> 
  e_band2(DAX, SMI, color='lightblue', itemStyle=list(borderWidth=0)) |>
  e_y_axis(scale=TRUE) |>
  e_datazoom(start = 50) 
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Correlation Matrix

<div id="cb3" class="sourceCode">

``` r
cor(mtcars) |> 
  e_charts() |> 
  e_correlations(order = "hclust") |> 
  e_tooltip()
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Error bars

<div id="cb4" class="sourceCode">

``` r
df <- data.frame(
  x = factor(c(1, 2)),
  y = c(1, 5),
  upper = c(1.1, 5.3),
  lower = c(0.8, 4.3)
)

df |> 
  e_charts(x) |> 
  e_bar(y) |> 
  e_error_bar(lower, upper)
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Boxplot

<div id="cb5" class="sourceCode">

``` r
df <- data.frame(
  x = c(
    rnorm(100),
    runif(100, -5, 10),
    rnorm(100, 10, 3)
  ),
  grp = c(
    rep(LETTERS[1], 100),
    rep(LETTERS[2], 100),
    rep(LETTERS[3], 100)
  )
)

df |> 
  group_by(grp) |> 
  e_charts() |> 
  e_boxplot(x)
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Histogram

<div id="cb6" class="sourceCode">

``` r
# data.frame
df <- data.frame(
  x = 1:100,
  y = rnorm(100, 20, 12)
)

df |> 
  e_charts() |> 
  e_histogram(y, name = "histogram") |> 
  e_tooltip()
```

</div>

<div id="htmlwidget-10b3b7155e8045a1b2ad"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Density

Plot the density on a different Y axis as its range differs much from
the that of the histogram.

<div id="cb7" class="sourceCode">

``` r
df |>
  e_charts() |> 
  e_histogram(y) |> 
  e_density(y, name = "density", areaStyle = list(opacity = .4), 
            smooth = TRUE, y_index = 1) |> 
  e_tooltip()
```

</div>

<div id="htmlwidget-4018eef1a407a0df6b52"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Linear

<div id="cb8" class="sourceCode">

``` r
iris |> 
  group_by(Species) |> 
  e_charts(Sepal.Length) |> 
  e_line(Sepal.Width) |> 
  e_lm(Sepal.Width ~ Sepal.Length) |> 
  e_x_axis(min = 4)
```

</div>

<div id="htmlwidget-5b1b2f4ad92281566982"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Polynomial

<div id="cb9" class="sourceCode">

``` r
mtcars |> 
  e_charts(disp) |> 
  e_scatter(mpg, qsec) |> 
  e_loess(mpg ~ disp)
```

</div>

<div id="htmlwidget-25c3e940e6859592f801"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
