<div id="main" role="main">

# Leaflet & Mapbox

Leaflet only works with `e_scatter` and `e_effect_scatter`.

<div class="section level2">

## Scatter

<div id="cb1" class="sourceCode">

``` r
echarts4r::population |> 
  e_charts(lon) |> 
  e_leaflet() |>
  e_leaflet_tile() |>  
  e_scatter(lat, size = value, coord_system = "leaflet")
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Mapbox

You will need [mapbox](https://www.mapbox.com/) token.

<div id="cb2" class="sourceCode">

``` r
echarts4r::population |> 
  e_charts(lon) |> 
  e_mapbox(
    token = "YOUR_TOKEN",
    style = "mapbox://styles/mapbox/dark-v9"
  ) |> 
  e_bar_3d(lat, value, coord_system = "mapbox") |> 
  e_visual_map(value)
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
