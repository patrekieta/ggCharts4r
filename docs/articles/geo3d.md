<div id="main" role="main">

# Geo 3D

`e_geo_3d` family is similar to `e_geo_3d` `e_map`, `e_map_3d` or
`e_globe`.

<div class="section level2">

## Height Choropleth

<div id="cb1" class="sourceCode">

``` r
choropleth <- data.frame(
  countries = c("France", "Brazil", "China", "Russia", "Canada", "India", "United States",
                "Argentina", "Australia"),
  height = runif(9, 1, 5)
)

choropleth |> 
  dplyr::arrange(-height) |> 
  e_color_range(height, color) |> 
  e_charts(countries) |> 
  e_geo_3d(height, color)
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
  e_geo_3d() |> 
  e_lines_3d(
    start_lon, 
    start_lat, 
    end_lon, 
    end_lat,
    name = "flights",
    coord_system = "geo3D",
    lineStyle = list(normal = list(curveness = 0.3)),
    effect = list(show = TRUE)
   )
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Bars

<div id="cb3" class="sourceCode">

``` r
url <- "https://echarts.apache.org/examples/data-gl/asset/data/population.json"
data <- jsonlite::fromJSON(url)
data <- as.data.frame(data)
names(data) <- c("lon", "lat", "value")

data |> 
  e_charts(lon) |> 
  e_geo_3d() |> 
  e_bar_3d(lat, value, coord_system = "geo3D") |> 
  e_visual_map()
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

USArrests$state <- row.names(USArrests) # add states as column

USArrests |> 
  e_color_range(Murder, Color) |> 
  e_charts(state) |>
  em_map("USA") |> 
  e_geo_3d(Murder, Color, type = "USA", regionHeight = 1) |> 
  e_visual_map(Murder)
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

You can also use your own geoJSON with `e_map_register`.

</div>

</div>
