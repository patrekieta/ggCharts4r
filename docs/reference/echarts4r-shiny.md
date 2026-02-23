<div id="main" class="col-md-9" role="main">

# Shiny bindings for echarts4r

<div class="ref-description section level2">

Output and render functions for using echarts4r within Shiny
applications and interactive Rmd documents.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
echarts4rOutput(outputId, width = "100%", height = "400px")

renderEcharts4r(expr, env = parent.frame(), quoted = FALSE)

echarts4rProxy(
  id,
  data,
  x,
  timeline = FALSE,
  session = shiny::getDefaultReactiveDomain(),
  reorder = TRUE
)

echarts4r_proxy(
  id,
  data,
  x,
  timeline = FALSE,
  session = shiny::getDefaultReactiveDomain(),
  reorder = TRUE
)
```

</div>

</div>

<div class="section level2">

## Arguments

-   outputId:

    output variable to read from.

-   width, height:

    Must be a valid CSS unit (like `'100%'`, `'400px'`, `'auto'`) or a
    number, which will be coerced to a string and have `'px'` appended.

-   expr:

    An expression that generates a echarts4r

-   env:

    The environment in which to evaluate `expr`.

-   quoted:

    Is `expr` a quoted expression (with `quote()`)? This is useful if
    you want to save an expression in a variable.

-   id:

    Target chart id.

-   data:

    A `data.frame`.

-   x:

    Column name containing x axis.

-   timeline:

    Set to `TRUE` to build a timeline, see timeline section.

-   session:

    Shiny session.

-   reorder:

    Set to `FALSE` to not reorder numeric x axis values.

</div>

<div class="section level2">

## Details

The chart is created inside a parent `'<div>'` element, the dimensions
of which are controlled by the `'width'` and `'height'` arguments. When
these dimensions are small, it is possible that the chart `'grid'`
resizes to a size larger than the parent, which might result in
unexpected size given the input arguments. To disable this automatic
readjustment, define a static `e_grid` like the following:
`'e_grid(e = current_chart, top = 0, left = 20, right = 0,   bottom = 20)'`.

</div>

<div class="section level2">

## Callbacks

-   `id_brush`: returns data on brushed data points.

-   `id_legend_change`: returns series name of legend
    selected/unselected.

-   `id_clicked_data`: returns data of clicked data point.

-   `id_clicked_data_value`: returns value of clicked data point.

-   `id_clicked_row`: returns row number of clicked data point.

-   `id_clicked_serie`: returns name of serie of clicked data point.

-   `id_mouseover_data`: returns data on hovered data point.

-   `id_mouseover_data_value`: returns value of hovered data point.

-   `id_mouseover_row`: returns row o hovered data point.

-   `id_mouseover_serie`: returns name of serie of hovered data point.

-   `id_dragged_annotation`: returns data on dragged annotation.

</div>

<div class="section level2">

## Proxies

The `echarts4rProxy` function returns a proxy for chart which allows
manipulating a drawn chart, adding data, adding or removing series, etc.
without redrawing the entire chart.

-   `e_append1_p` & `e_append2_p`

-   `e_showtip_p` & `e_hidetip_p`

-   `e_highlight_p` & `e_downplay_p`

-   `e_focus_adjacency` & `e_unfocus_adjacency`

-   `e_dispatch_action_p`

-   `e_execute`

-   `e_remove_serie_p`

</div>

</div>
