<div id="main" class="col-md-9" role="main">

# Globe

<div class="ref-description section level2">

Add globe.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_globe(e, environment = NULL, base_texture = NULL, height_texture = NULL, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   environment:

    Texture of background.

-   base_texture:

    Base texture of globe.

-   height_texture:

    Texture of height.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

`e_country_names`, [Additional
arguments](https://echarts.apache.org/en/option-gl.html#globe)

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
  e_globe(
    displacementScale = 0.04
  ) |>
  e_bar_3d(lat, value, "globe") |>
  e_visual_map(show = FALSE)
} # }
```

</div>

</div>

</div>
