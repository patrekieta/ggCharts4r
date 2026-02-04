<div id="main" class="col-md-9" role="main">

# Dispatch Action

<div class="ref-description section level2">

Create your own proxies, essentially a wrapper around the [action
API](https://echarts.apache.org/en/api.html#action).

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_dispatch_action_p(proxy, type, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   proxy:

    An echarts4r proxy as returned by `echarts4rProxy`.

-   type:

    Type of action to dispatch, i.e.: `highlight`.

-   ...:

    Named options.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
if (FALSE) { # \dontrun{

library(shiny)

ui <- fluidPage(
  fluidRow(
    column(8, echarts4rOutput("chart")),
    column(4, actionButton("zoom", "Zoom"))
  )
)

server <- function(input, output, session) {
  output$chart <- renderEcharts4r({
    cars |>
      e_charts(speed) |>
      e_scatter(dist) |>
      e_datazoom()
  })

  observe({
    req(input$zoom)

    echarts4rProxy("chart") |>
      e_dispatch_action_p("dataZoom", startValue = 1, endValue = 10)
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
