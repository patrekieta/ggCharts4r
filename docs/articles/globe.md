<div id="main" role="main">

# Globe

`e_globe` family is similar to `e_geo_3d` `e_map`, or `e_map_3d`.

**Note**: As the package became too large (borderline for CRAN), assets
have been moved to another package: `echarts4r.assets`. This also allows
the introduction of more assets.

Deprecated:

-   `e_stars_texture`
-   `e_globe_texture`
-   `e_map_texture`

Visit the [website](https://echarts4r-assets.john-coene.com) for more
examples.

<div id="cb1" class="sourceCode">

``` r
#install.packages("remotes")
remotes::install_github("JohnCoene/echarts4r.assets")
```

</div>

<div class="section level2">

## Scatter 3D

<div id="cb2" class="sourceCode">

``` r
library(echarts4r.assets)

airports <- read.csv(
  paste0("https://raw.githubusercontent.com/plotly/datasets/",
         "master/2011_february_us_airport_traffic.csv")
)

airports |> 
  e_charts(long) |> 
  e_globe(
    environment = ea_asset("starfield"),
    base_texture = ea_asset("world"), 
    globeOuterRadius = 100
  ) |> 
  e_scatter_3d(lat, cnt, coord_system = "globe", blendMode = 'lighter') |> 
  e_visual_map(inRange = list(symbolSize = c(1, 10)))
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Bar

<div id="cb3" class="sourceCode">

``` r
url <- "https://echarts.apache.org/examples/data-gl/asset/data/population.json"
data <- jsonlite::fromJSON(url)
data <- as.data.frame(data)
names(data) <- c("lon", "lat", "value")

data |> 
  e_charts(lon) |> 
  e_globe(
    environment = ea_asset("starfield"),
    base_texture = ea_asset("world topo"), 
    height_texture = ea_asset("world topo"),
    displacementScale = 0.04
  ) |> 
  e_bar_3d(lat, value, coord_system = "globe") |> 
  e_visual_map(show = FALSE)
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Lines

<div id="cb4" class="sourceCode">

``` r
flights <- read.csv(
  paste0("https://raw.githubusercontent.com/plotly/datasets/",
         "master/2011_february_aa_flight_paths.csv")
)

flights |> 
  e_charts() |> 
  e_globe(
    environment = ea_asset("starfield"),
    base_texture = ea_asset("world topo"), 
    height_texture = ea_asset("world topo"),
    displacementScale = 0.05
  ) |> 
  e_lines_3d(
    start_lon, 
    start_lat, 
    end_lon, 
    end_lat,
    name = "flights",
    effect = list(show = TRUE)
  ) |> 
  e_legend(FALSE)
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
