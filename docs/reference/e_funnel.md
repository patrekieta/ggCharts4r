<div id="main" class="col-md-9" role="main">

# Funnel

<div class="ref-description section level2">

Add a funnel.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_funnel(
  e,
  values,
  labels,
  name = NULL,
  legend = TRUE,
  rm_x = TRUE,
  rm_y = TRUE,
  ...
)

e_funnel_(
  e,
  values,
  labels,
  name = NULL,
  legend = TRUE,
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

    An `echarts4r` object as returned by `e_charts`.

-   values, labels:

    Values and labels of funnel.

-   name:

    name of the serie.

-   legend:

    Whether to add serie to legend.

-   rm_x, rm_y:

    Whether to remove x and y axis, defaults to `TRUE`.

-   ...:

    Any other option to pass to `bar` or `line` char types.

</div>

<div class="section level2">

## Details

No `bind` argument here, with a funnel `bind` = `labels`.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#series-funnel)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
funnel <- data.frame(
  stage = c("View", "Click", "Purchase"),
  value = c(80, 30, 20)
)

funnel |>
  e_charts() |>
  e_funnel(value, stage)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"legend":{"data":["View","Click","Purchase"]},"series":[{"data":[{"value":80,"name":"View"},{"value":30,"name":"Click"},{"value":20,"name":"Purchase"}],"name":null,"type":"funnel"}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
