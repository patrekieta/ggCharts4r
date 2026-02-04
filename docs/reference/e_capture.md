<div id="main" class="col-md-9" role="main">

# Capture event

<div class="ref-description section level2">

Add an event capture.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_capture(e, event)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   event:

    An event name from the [event
    documentation](https://echarts.apache.org/en/api.html#events).

</div>

<div class="section level2">

## Details

Many events can be captured, however not all are integrated, you can
pass one that is not implemented with this function.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
if (FALSE) { # \dontrun{
# add datazoom
library(shiny)

ui <- fluidPage(
  echarts4rOutput("chart"),
  verbatimTextOutput("zoom")
)

server <- function(input, output) {
  output$chart <- renderEcharts4r({
    mtcars |>
      e_charts(mpg) |>
      e_scatter(qsec) |>
      e_datazoom() |>
      e_capture("datazoom")
  })

  output$zoom <- renderPrint({
    input$chart_datazoom
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
