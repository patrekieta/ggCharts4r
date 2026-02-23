<div id="main" class="col-md-9" role="main">

# Draw

<div class="ref-description section level2">

Draw the chart.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_draw_p(proxy)
```

</div>

</div>

<div class="section level2">

## Arguments

-   proxy:

    An echarts4r proxy as returned by `echarts4rProxy`.

</div>

<div class="section level2">

## Details

Useful if you set `draw` to `FALSE` in `e_charts`.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
if (FALSE) { # \dontrun{
library(shiny)

ui <- fluidPage(
  echarts4rOutput("chart"),
  actionButton("draw", "draw")
)

server <- function(input, output) {
  output$chart <- renderEcharts4r({
    mtcars |>
      e_charts(mpg, draw = FALSE) |>
      e_scatter(qsec) |>
      e_datazoom()
  })

  observeEvent(input$draw, {
    echarts4rProxy("chart") |>
      e_draw_p()
  })
}

if (interactive()) {
  shinyApp(ui, server)
}
} # }
```

</div>

</div>

</div>
