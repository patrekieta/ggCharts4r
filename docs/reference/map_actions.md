<div id="main" class="col-md-9" role="main">

# Map Actions

<div class="ref-description section level2">

Map-related actions.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_map_select(e, ..., btn = NULL)

e_map_unselect(e, ..., btn = NULL)

e_map_toggle_select(e, ..., btn = NULL)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   ...:

    Any options, see [official
    documentation](https://echarts.apache.org/en/api.html#action.map)

-   btn:

    A `e_button` id.

</div>

<div class="section level2">

## See also

<div class="dont-index">

`e_map_register`

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
choropleth <- data.frame(
  countries = c(
    "France",
    "Brazil",
    "China",
    "Russia",
    "Canada",
    "India",
    "United States",
    "Argentina",
    "Australia"
  ),
  values = round(runif(9, 10, 25))
)

choropleth |>
  e_charts(countries) |>
  e_map(values) |>
  e_visual_map(min = 10, max = 25) |>
  e_map_toggle_select(name = "China", btn = "btn") |>
  e_button("btn", "Select China")
Select China

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":{"btn":[{"id":"btn","data":{"type":"mapToggleSelect","name":"China"}}]},"opts":{"series":[{"type":"map","map":"world","name":"values","data":[{"value":14,"name":"France"},{"value":22,"name":"Brazil"},{"value":13,"name":"China"},{"value":20,"name":"Russia"},{"value":23,"name":"Canada"},{"value":14,"name":"India"},{"value":11,"name":"United States"},{"value":21,"name":"Argentina"},{"value":19,"name":"Australia"}]}],"visualMap":[{"min":10,"max":25,"calculable":true,"type":"continuous"}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
