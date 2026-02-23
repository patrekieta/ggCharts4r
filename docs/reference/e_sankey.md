<div id="main" class="col-md-9" role="main">

# Sankey

<div class="ref-description section level2">

Draw a sankey diagram.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_sankey(
  e,
  source,
  target,
  value,
  layout = "none",
  rm_x = TRUE,
  rm_y = TRUE,
  ...
)

e_sankey_(
  e,
  source,
  target,
  value,
  layout = "none",
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

-   source, target:

    Source and target columns.

-   value:

    Value change from `source` to `target`.

-   layout:

    Layout of sankey.

-   rm_x, rm_y:

    Whether to remove the x and y axis, defaults to `TRUE`.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#series-sankey)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
sankey <- data.frame(
  source = c("a", "b", "c", "d", "c"),
  target = c("b", "c", "d", "e", "e"),
  value = ceiling(rnorm(5, 10, 1)),
  stringsAsFactors = FALSE
)

sankey |>
  e_charts() |>
  e_sankey(source, target, value)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"series":[{"type":"sankey","orient":"none","data":[{"name":"a"},{"name":"b"},{"name":"c"},{"name":"d"},{"name":"e"}],"links":[{"source":"a","target":"b","value":"11"},{"source":"b","target":"c","value":"10"},{"source":"c","target":"d","value":"11"},{"source":"d","target":"e","value":"12"},{"source":"c","target":"e","value":"11"}]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
