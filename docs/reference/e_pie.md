<div id="main" class="col-md-9" role="main">

# Pie

<div class="ref-description section level2">

Draw pie and donut charts.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_pie(
  e,
  serie,
  name = NULL,
  legend = TRUE,
  coord_system = "",
  rm_x = TRUE,
  rm_y = TRUE,
  ...
)

e_pie_(
  e,
  serie,
  name = NULL,
  legend = TRUE,
  coord_system = "",
  rm_x = TRUE,
  rm_y = TRUE,
  ...
)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   serie:

    Column name of serie to plot.

-   name:

    name of the serie.

-   legend:

    Whether to add serie to legend.

-   coord_system:

    Coordinate system to plot against.

-   rm_x, rm_y:

    Whether to remove x and y axis, defaults to `TRUE`.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#series-pie)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
mtcars |>
  head() |>
  tibble::rownames_to_column("model") |>
  e_charts(model) |>
  e_pie(carb)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"legend":{"data":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Hornet 4 Drive","Hornet Sportabout","Valiant"]},"series":[{"name":"carb","type":"pie","data":[{"value":4,"name":"Mazda RX4"},{"value":4,"name":"Mazda RX4 Wag"},{"value":1,"name":"Datsun 710"},{"value":1,"name":"Hornet 4 Drive"},{"value":2,"name":"Hornet Sportabout"},{"value":1,"name":"Valiant"}]}]},"dispose":true},"evals":[],"jsHooks":[]}
# timeline
df <- data.frame(
  grp = c("A", "A", "A", "B", "B", "B"),
  labels = rep(LETTERS[1:3], 2),
  values = runif(6, 1, 5)
)

df |>
  group_by(grp) |>
  e_charts(labels, timeline = TRUE) |>
  e_pie(values)

{"x":{"theme":"","tl":true,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"baseOption":{"timeline":{"data":["A","B"],"axisType":"category"},"series":[{"name":null,"type":"pie"}]},"options":[{"series":[{"data":[{"value":2.762141366489232,"name":"A"},{"value":3.01908803358674,"name":"B"},{"value":4.776135037653148,"name":"C"}]}]},{"series":[{"data":[{"value":2.958744345232844,"name":"A"},{"value":4.048609269782901,"name":"B"},{"value":3.770423071458936,"name":"C"}]}]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
