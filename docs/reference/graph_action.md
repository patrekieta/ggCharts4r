<div id="main" class="col-md-9" role="main">

# Nodes Adjacency

<div class="ref-description section level2">

Actions related to `e_graph`.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_focus_adjacency(e, ..., btn = NULL)

e_unfocus_adjacency(e, ..., btn = NULL)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   ...:

    Any options, see [official
    documentation](https://echarts.apache.org/en/api.html#action.graph)

-   btn:

    A `e_button` id.

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

e_charts() |>
  e_graph() |>
  e_graph_nodes(nodes, name, value, size, grp) |>
  e_graph_edges(edges, source, target) |>
  e_focus_adjacency(
    seriesIndex = 0,
    dataIndex = 4
  )

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[{"data":{"type":"focusNodeAdjacency","seriesIndex":0,"dataIndex":4}}],"buttons":[],"opts":{"series":[{"name":null,"type":"graph","layout":"force","categories":[{"name":"grp1"},{"name":"grp2"}],"data":[{"name":"Z","value":" 9.838490","symbolSize":" 9.838490","category":"grp1"},{"name":"O","value":"14.451139","symbolSize":"14.451139","category":"grp2"},{"name":"X","value":" 8.468096","symbolSize":" 8.468096","category":"grp1"},{"name":"W","value":" 9.136815","symbolSize":" 9.136815","category":"grp2"},{"name":"K","value":" 9.700741","symbolSize":" 9.700741","category":"grp1"},{"name":"J","value":"10.802435","symbolSize":"10.802435","category":"grp2"},{"name":"C","value":" 9.814017","symbolSize":" 9.814017","category":"grp1"},{"name":"D","value":"13.447850","symbolSize":"13.447850","category":"grp2"},{"name":"U","value":"12.628372","symbolSize":"12.628372","category":"grp1"},{"name":"B","value":"10.729494","symbolSize":"10.729494","category":"grp2"}],"links":[{"source":"Z","target":"O"},{"source":"B","target":"O"},{"source":"O","target":"O"},{"source":"J","target":"D"},{"source":"B","target":"W"},{"source":"W","target":"U"},{"source":"J","target":"Z"},{"source":"K","target":"U"},{"source":"K","target":"W"},{"source":"D","target":"D"},{"source":"Z","target":"D"},{"source":"Z","target":"W"},{"source":"B","target":"K"},{"source":"B","target":"J"},{"source":"W","target":"U"},{"source":"K","target":"U"},{"source":"O","target":"D"},{"source":"U","target":"J"},{"source":"X","target":"K"},{"source":"B","target":"Z"}]}],"legend":{"data":["grp1","grp2"]}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
