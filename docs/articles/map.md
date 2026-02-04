<div id="main" role="main">

# Maps

This document describes the maps.

<div class="section level2">

## Choropleth

Pass countries as `x` argument.

<div id="cb1" class="sourceCode">

``` r
cns <- countrycode::codelist$country.name.en
cns <- data.frame(
  country = cns,
  value = runif(length(cns), 1, 100)
)

cns |> 
  e_charts(country) |> 
  e_map(value) |> 
  e_visual_map(value)
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Lines

Use `e_lines` (not ~~`e_line`~~)

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

## Countries

The companion package
[echarts4r.maps](https://echarts4r-maps.john-coene.com) comes with 215
maps.

You can install the package with:

<div id="cb3" class="sourceCode">

``` r
install.packages("remotes")
remotes::install_github('JohnCoene/echarts4r.maps')
```

</div>

View the full list of maps with `echarts4r.maps::em_bank()`.

<div id="cb4" class="sourceCode">

``` r
library(echarts4r.maps)

df <- data.frame(
    region = c("Rajasthan", "Odisha", "Gujarat"), 
    value = c(1,2, 3)
)

df |> 
  e_charts(region) |>
  em_map("India") |> 
  e_map(value, map = "India") |> 
  e_visual_map(value) |> 
  e_theme("infographic")
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## GeoJSON support

Use a custom [geojson](https://geojson.org/) map; 1) read the json and
register it with `e_register_map`.

<div id="cb5" class="sourceCode">

``` r
json <- jsonlite::read_json("https://raw.githubusercontent.com/shawnbot/topogram/master/data/us-states.geojson")

USArrests |>
  tibble::rownames_to_column("states") |> 
  e_charts(states) |>
  e_map_register("USA", json) |>
  e_map(Murder, map = "USA") |> 
  e_visual_map(Murder)
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
