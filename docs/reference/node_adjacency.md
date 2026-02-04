<div id="main" class="col-md-9" role="main">

# Node Adjacency

<div class="ref-description section level2">

Focus or unfocus on node adjacency.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_focus_adjacency_p(proxy, index, ...)

e_unfocus_adjacency_p(proxy, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   proxy:

    An echarts4r proxy as returned by `echarts4rProxy`.

-   index:

    One or more node index to focus on.

-   ...:

    Any other options, see [official
    documentation](https://echarts.apache.org/en/api.html#action.graph)
    and details.

</div>

<div class="section level2">

## Details

Must pass `seriesId`, `seriesIndex`, or `seriesName`, generally
`seriesIndex = 0` will work.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
value <- rnorm(10, 10, 2)

nodes <- data.frame(
  name = sample(LETTERS, 10),
  value = value,
  size = value,
  grp = rep(c("grp1", "grp2"), 5),
  stringsAsFactors = FALSE
)

edges <- data.frame(
  source = sample(nodes$name, 20, replace = TRUE),
  target = sample(nodes$name, 20, replace = TRUE),
  stringsAsFactors = FALSE
)
if (FALSE) { # \dontrun{

library(shiny)

ui <- fluidPage(
  fluidRow(
    column(
      2,
      numericInput("index", "Node", value = 3, min = 1, max = 9)
    ),
    column(
      2,
      br(),
      actionButton("focus", "Focus")
    ),
    column(
      2,
      br(),
      actionButton("unfocus", "Unfocus")
    )
  ),
  fluidRow(
    column(12, echarts4rOutput("graph"))
  )
)

server <- function(input, output, session) {
  output$graph <- renderEcharts4r({
    e_charts() |>
      e_graph() |>
      e_graph_nodes(nodes, name, value, size, grp) |>
      e_graph_edges(edges, source, target)
  })

  observeEvent(input$focus, {
    echarts4rProxy("graph") |>
      e_focus_adjacency_p(
        seriesIndex = 0,
        index = input$index
      )
  })

  observeEvent(input$unfocus, {
    echarts4rProxy("graph") |>
      e_unfocus_adjacency_p(seriesIndex = 0)
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
