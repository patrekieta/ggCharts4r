<div id="main" role="main">

# Map 3D

`e_map_3d` family is similar to `e_geo_3d` `e_map`, or `e_globe`.

<div class="section level2">

## Choropleth

<div id="cb1" class="sourceCode">

``` r
choropleth <- data.frame(
  countries = c("France", "Brazil", "China", "Russia", "Canada", "India", "United States",
                "Argentina", "Australia"),
  values = round(runif(9, 10, 25))
)

choropleth |> 
  e_charts(countries) |> 
  e_map_3d(values, shading = "lambert") |> 
  e_visual_map(values) # scale to values
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Buildings

<div id="cb2" class="sourceCode">

``` r
buildings <- jsonlite::read_json("https://echarts.apache.org/examples/data-gl/asset/data/buildings.json")

heights <- purrr::map(buildings$features, "properties") |> 
  purrr::map("height") |> 
  unlist()
  
names <- purrr::map(buildings$features, "properties") |> 
  purrr::map("name") |> 
  unlist()
  
data <- dplyr::tibble(
  name = names,
  value = round(runif(length(names), 0, 1), 6),
  height = heights / 10
)

data |> 
  e_charts() |> 
  e_map_register("buildings", buildings) |>
  e_map_3d_custom(name, value, height) |> 
  e_visual_map(
    show = FALSE,
    min = 0.4,
    max = 1
  )
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
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

USArrests$state <- row.names(USArrests) # add states as column

USArrests |> 
  e_charts(state) |>
  em_map("USA") |> 
  e_map_3d(Murder, map = "USA") |> 
  e_visual_map(Murder)
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

You can also use your own geoJSON with `e_map_register`.

</div>

</div>
