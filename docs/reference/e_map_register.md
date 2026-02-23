<div id="main" class="col-md-9" role="main">

# Register map

<div class="ref-description section level2">

Register a [geojson](https://geojson.org/) map.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_map_register(e, name, json, ...)

e_svg_register(e, name, svg)

e_map_register_p(
  name,
  json,
  async = FALSE,
  session = shiny::getDefaultReactiveDomain()
)

e_map_register_ui(name, json, async = FALSE)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts`.

-   name:

    Name of map, to used in `e_map`.

-   json, svg:

    [Geojson](https://geojson.org/), or SVG.

-   ...:

    Additional options passed to
    [registerMap](https://echarts.apache.org/en/api.html#echarts.registerMap).

-   async:

    Whether to read the file asynchronously.

-   session:

    A valid Shiny session.

</div>

<div class="section level2">

## Details

`e_map_register_p` is not truly a proxy as it does not require a chart
to function. While the function `e_map_register_ui` is meant to register
the map globally in the Shiny UI, not that then `json` must be
accessible from the UI (generally www folder).

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
if (FALSE) { # \dontrun{
json <- jsonlite::read_json("https://echarts.apache.org/examples/data/asset/geo/USA.json")

USArrests |>
  tibble::rownames_to_column("states") |>
  e_charts(states) |>
  e_map_register("USA", json) |>
  e_map(Murder, map = "USA") |>
  e_visual_map(Murder)
} # }
```

</div>

</div>

</div>
