<div id="main" role="main">

# Graph

There are two core functions that let you build graphs in `echarts4r`;
`e_graph` and `e_graph_gl`. The latter is the webGL “version.”

<div class="section level2">

## Basic

Initialise your graph with `e_charts` then add nodes and edges with
`e_graph_nodes` and `e_graph_edges` respectively.

<div id="cb1" class="sourceCode">

``` r
value <- rnorm(10, 10, 2)

nodes <- data.frame(
  name = sample(LETTERS, 10),
  value = value,
  size = value,
  stringsAsFactors = FALSE
)

edges <- data.frame(
  source = sample(nodes$name, 20, replace = TRUE),
  target = sample(nodes$name, 20, replace = TRUE),
  stringsAsFactors = FALSE
)

e_charts() |> 
  e_graph() |> 
  e_graph_nodes(nodes, name, value, size) |> 
  e_graph_edges(edges, source, target) |> 
  e_tooltip()
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Groups

The same but with groups.

<div id="cb2" class="sourceCode">

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

e_charts() |> 
  e_graph() |> 
  e_graph_nodes(nodes, name, value, size, grp) |> 
  e_graph_edges(edges, source, target) |> 
  e_tooltip()
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Groups

The same but with groups and symbols.

<div id="cb3" class="sourceCode">

``` r
value <- rnorm(10, 10, 2)

nodes <- data.frame(
  name = sample(LETTERS, 10),
  value = value,
  size = value,
  grp = rep(c("grp1", "grp2"), 5),
  symbol = sample(c("circle", "rect", "triangle"), 10, replace = TRUE),
  stringsAsFactors = FALSE
)

edges <- data.frame(
  source = sample(nodes$name, 20, replace = TRUE),
  target = sample(nodes$name, 20, replace = TRUE),
  stringsAsFactors = FALSE
)

e_charts() |> 
  e_graph() |> 
  e_graph_nodes(nodes, name, value, size, grp, symbol) |> 
  e_graph_edges(edges, source, target) |> 
  e_tooltip()
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Graph GL

Simply use `e_graph_gl` instead of `e_graph`.

<div id="cb4" class="sourceCode">

``` r
flights <- read.csv(
  paste0("https://raw.githubusercontent.com/plotly/datasets/",
         "master/2011_february_aa_flight_paths.csv")
) |> 
  dplyr::select(airport1, airport2)

airports <- read.csv(
  paste0("https://raw.githubusercontent.com/plotly/datasets/",
         "master/2011_february_us_airport_traffic.csv")
) |> 
  dplyr::select(iata, cnt)

# remove airports with no flights
airp <- unique(c(as.character(flights$airport1), as.character(flights$airport2)))
airports <- airports |> 
  dplyr::filter(iata %in% airp)

e_charts() |> 
    e_graph_gl() |> 
    e_graph_nodes(airports, iata, cnt) |> 
    e_graph_edges(flights, airport1, airport2) |> 
    e_modularity() |> 
    e_tooltip()
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Les Miserables

The Les Miserables dataset is a popular visualization that demonstrates
network graphs. An example of this graph is provided below.

<div id="cb5" class="sourceCode">

``` r
library(echarts4r)

les <- jsonlite::fromJSON("https://gist.githubusercontent.com/tylerlittlefield/0d7a53f2a1f55cb3c6ffe22c67618267/raw/0684a839c3e49dac1157721ddd906eff8f9491d4/les-miserables.json")


e_charts() |> 
  e_graph(
    layout = "circular", 
    circular = list(
      rotateLabel = TRUE
    ),
    roam = TRUE,
    lineStyle = list(
      color = "source",
      curveness = 0.3
    ),
    label = list(
      position = "right",
      formatter = "{b}"
    )
  ) |>
  e_graph_nodes(
    nodes = les$nodes, 
    names = name, 
    value = value, 
    size = size, 
    category = grp
  ) |> 
  e_graph_edges(
    edges = les$edges, 
    source = from,
    target = to
  ) |>
  e_tooltip()
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
