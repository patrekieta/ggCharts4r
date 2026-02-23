<div id="main" role="main">

# Geo

`e_geo` family is similar to `e_geo_3d` `e_map`, `e_map_3d` or
`e_globe`.

<div class="section level2">

## Points

<div id="cb1" class="sourceCode">

``` r
quakes |> 
  e_charts(long) |> 
  e_geo(
    roam = TRUE,
    boundingCoords = list(
      c(185, - 10),
      c(165, -40)
    )
  ) |> 
  e_scatter(
    lat, mag, 
    coord_system = "geo"
  ) |> 
  e_visual_map(mag, scale = e_scale)
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Lines

<div id="cb2" class="sourceCode">

``` r
flights <- read.csv(
  paste0("https://raw.githubusercontent.com/plotly/datasets/",
         "master/2011_february_aa_flight_paths.csv")
)

flights |> 
  e_charts() |> 
  e_geo() |> 
  e_lines(
    start_lon, 
    start_lat, 
    end_lon, 
    end_lat,
    name = "flights",
    lineStyle = list(normal = list(curveness = 0.3))
   )
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Heatmap

<div id="cb3" class="sourceCode">

``` r
quakes |>
  e_charts(long) |> 
  e_geo(
    boundingCoords = list(
      c(190, -10),
      c(180, -40)
   )
  ) |> 
  e_heatmap(
    lat, 
    mag, 
    coord_system = "geo", 
    blurSize = 5, 
    pointSize = 3
  ) |> 
  e_visual_map(mag)
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## GeoJSON

The companion package
[echarts4r.maps](https://echarts4r-maps.john-coene.com) comes with 215
maps.

You can install the package with:

<div id="cb4" class="sourceCode">

``` r
install.packages("remotes")
remotes::install_github('JohnCoene/echarts4r.maps')
```

</div>

View the full list of maps with `echarts4r.maps::em_bank()`.

<div id="cb5" class="sourceCode">

``` r
library(echarts4r.maps)

flights <- read.csv(
  paste0("https://raw.githubusercontent.com/plotly/datasets/",
         "master/2011_february_aa_flight_paths.csv")
)

flights |> 
  e_charts() |> 
  em_map("USA") |>
  e_geo("USA") |> 
  e_lines(
    start_lon, 
    start_lat, 
    end_lon, 
    end_lat,
    name = "flights",
    lineStyle = list(normal = list(curveness = 0.3))
   )
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

You can also use your own geoJSON with `e_map_register`.

</div>

</div>
