<div id="main" class="col-md-9" role="main">

# Select & Unselect Pie

<div class="ref-description section level2">

Actions related to `e_pie`.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_pie_select(e, ..., btn = NULL)

e_pie_unselect(e, ..., btn = NULL)
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
    documentation](https://echarts.apache.org/en/api.html#action.pie)

-   btn:

    A `e_button` id.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
mtcars |>
  head() |>
  tibble::rownames_to_column("model") |>
  e_charts(model) |>
  e_pie(carb) |>
  e_pie_select(dataIndex = 0)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[{"data":{"type":"pieSelect","dataIndex":0}}],"buttons":[],"opts":{"legend":{"data":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Hornet 4 Drive","Hornet Sportabout","Valiant"]},"series":[{"name":"carb","type":"pie","data":[{"value":4,"name":"Mazda RX4"},{"value":4,"name":"Mazda RX4 Wag"},{"value":1,"name":"Datsun 710"},{"value":1,"name":"Hornet 4 Drive"},{"value":2,"name":"Hornet Sportabout"},{"value":1,"name":"Valiant"}]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
