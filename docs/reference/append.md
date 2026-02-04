<div id="main" class="col-md-9" role="main">

# Append Proxy

<div class="ref-description section level2">

Append data dynamically.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_append1_p(proxy, series_index = NULL, data, x, y, name = NULL)

e_append1_p_(proxy, series_index = NULL, data, x, y, name = NULL)

e_append2_p(
  proxy,
  series_index = NULL,
  data,
  x,
  y,
  z,
  scale = NULL,
  symbol_size = 1
)

e_append2_p_(
  proxy,
  series_index = NULL,
  data,
  x,
  y,
  z,
  scale = NULL,
  symbol_size = 1
)
```

</div>

</div>

<div class="section level2">

## Arguments

-   proxy:

    An echarts4r proxy as returned by `echarts4rProxy`.

-   series_index:

    Index of serie to append to (starts from 0).

-   data:

    Data.frame containing data to append.

-   x, y, z:

    Columns names to plot.

-   name:

    if using \`bind\` with e.g \`e_scatter\` this can be used to supply
    the colname for the name attribute bind is mapping to

-   scale:

    A scaling function as passed to `e_scatter`.

-   symbol_size:

    Multiplier of scaling function as in `e_scatter`.

</div>

<div class="section level2">

## Details

Currently not all types of series supported incremental rendering when
using appendData. Only these types of series support it: `e_scatter` and
`e_line` of pure echarts, and `e_scatter_3d`, and `e_line_3d` of
echarts-gl.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
if (FALSE) { # \dontrun{
library(shiny)

ui <- fluidPage(
  actionButton("add", "Add Data to y"),
  echarts4rOutput("plot"),
  h4("Brush"),
  verbatimTextOutput("selected"),
  h4("Legend select change"),
  verbatimTextOutput("legend")
)

server <- function(input, output, session) {
  data <- data.frame(x = rnorm(10, 5, 3), y = rnorm(10, 50, 12), z = rnorm(10, 5, 20))

  react <- eventReactive(input$add, {
    set.seed(sample(1:1000, 1))
    data.frame(x = rnorm(10, 5, 2), y = rnorm(10, 50, 10), z = rnorm(10, 5, 20))
  })

  output$plot <- renderEcharts4r({
    data |>
      e_charts(x) |>
      e_scatter(y, z, scale = NULL) |>
      e_scatter(z) |>
      e_brush()
  })

  observeEvent(input$add, {

    echarts4rProxy("plot") |>
      e_append2_p(0, react(), x, y, z)
  })

  output$selected <- renderPrint({
    input$plot_brush
  })

  output$legend <- renderPrint({
    input$plot_legend_change
  })
}

shinyApp(ui, server)
} # }
```

</div>

</div>

</div>
