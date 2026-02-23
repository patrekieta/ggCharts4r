<div id="main" class="col-md-9" role="main">

# Mapbox

<div class="ref-description section level2">

Use mapbox.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_mapbox(e, token, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   token:

    Your mapbox token from [mapbox](https://www.mapbox.com/).

-   ...:

    Any option.

</div>

<div class="section level2">

## Note

Mapbox may not work properly in the RSudio console.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Official
documentation](https://echarts.apache.org/en/option-gl.html#mapbox3D.style),
[mapbox documentation](https://docs.mapbox.com/mapbox-gl-js/api/)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
if (FALSE) { # \dontrun{
url <- paste0(
  "https://echarts.apache.org/examples/",
  "data-gl/asset/data/population.json"
)
data <- jsonlite::fromJSON(url)
data <- as.data.frame(data)
names(data) <- c("lon", "lat", "value")

data |>
  e_charts(lon) |>
  e_mapbox(
    token = "YOUR_MAPBOX_TOKEN",
    style = "mapbox://styles/mapbox/dark-v9"
  ) |>
  e_bar_3d(lat, value, coord_system = "mapbox") |>
  e_visual_map()
} # }
```

</div>

</div>

</div>
