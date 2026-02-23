<div id="main" class="col-md-9" role="main">

# Add nested data

<div class="ref-description section level2">

Utility function to add data where the original JavaScript library
expects nested data.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_add(e, param, ..., .serie = NULL, .data = NULL)

e_add_nested(e, param, ..., .serie = NULL, .data = NULL)

e_add_unnested(e, param, value, .serie = NULL, .data = NULL)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   param:

    The nested parameter to add data to.

-   ...:

    Any other option to pass, check See Also section.

-   .serie:

    Serie's index to add the data to, if \`NULL\` then it is added to
    all.

-   .data:

    A dataset to use, if none are specified than the original dataset
    passed to \`e_charts\` is used.

-   value:

    The column to map to the parameter.

</div>

<div class="section level2">

## Details

For instance, `e_funnel` lets you pass `values` and `labels` (from your
initial data.frame) which corresponds to `name` and `value` in the
[original
library](https://echarts.apache.org/en/option.html#series-heatmap.data).
However the latter also takes, `label`, `itemStyle`, and `emphasis` but
being JSON arrays they translate to lists in R and dealing with nested
data.frames is not ideal. `e_add` remedies to that. It allows adding
those nested data points, see the examples below.

</div>

<div class="section level2">

## Functions

\- \`e_add_nested\`: Adds nested data, e.g.: \`e_add_nested("itemStyle",
color, fontBold)\` creates \`{itemStyle: {color: 'red', fontBold:
'bold'}}\`. - \`e_add_unnested\`: Adds unnested data, e.g.:
\`e_add_unnested("symbolSize", size)\` creates \`{symbolSize: 4}\`.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
# funnel can take nested itemStyle
# https://echarts.apache.org/en/option.html#series-funnel.data
funnel <- data.frame(
  stage = c("View", "Click", "Purchase"),
  value = c(80, 30, 20),
  color = c("blue", "red", "green")
)

funnel |>
  e_charts() |>
  e_funnel(value, stage) |>
  e_add_nested("itemStyle", color)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"legend":{"data":["View","Click","Purchase"]},"series":[{"data":[{"value":80,"name":"View","itemStyle":{"color":"blue"}},{"value":30,"name":"Click","itemStyle":{"color":"red"}},{"value":20,"name":"Purchase","itemStyle":{"color":"green"}}],"name":null,"type":"funnel"}]},"dispose":true},"evals":[],"jsHooks":[]}
# Heatmap can take nested label
# https://echarts.apache.org/en/option.html#series-heatmap.data
v <- LETTERS[1:10]
matrix <- data.frame(
  x = sample(v, 300, replace = TRUE),
  y = sample(v, 300, replace = TRUE),
  z = rnorm(300, 10, 1),
  stringsAsFactors = FALSE
) |>
  dplyr::group_by(x, y) |>
  dplyr::summarise(z = sum(z)) |>
  dplyr::ungroup() |>
  dplyr::mutate(
    show = TRUE,
    fontStyle = round(runif(dplyr::n(), 5, 12))
  )
#> `summarise()` has grouped output by 'x'. You can override using the `.groups`
#> argument.

matrix |>
  e_charts(x) |>
  e_heatmap(y, z) |>
  e_visual_map(z) |>
  e_add_nested(
    "label",
    show,
    fontStyle
  )

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"data":["A","B","C","D","E","F","G","H","I","J"]}],"xAxis":[{"data":["A","B","C","D","E","F","G","H","I","J"]}],"series":[{"data":[{"value":["A","A","42.713778"],"label":{"show":1,"fontStyle":7}},{"value":["A","B","30.814297"],"label":{"show":1,"fontStyle":6}},{"value":["A","C","26.428722"],"label":{"show":1,"fontStyle":11}},{"value":["A","D","18.863452"],"label":{"show":1,"fontStyle":11}},{"value":["A","E","28.106522"],"label":{"show":1,"fontStyle":10}},{"value":["A","F","18.252600"],"label":{"show":1,"fontStyle":8}},{"value":["A","G","11.195937"],"label":{"show":1,"fontStyle":8}},{"value":["A","H","10.046559"],"label":{"show":1,"fontStyle":11}},{"value":["A","I","31.512559"],"label":{"show":1,"fontStyle":11}},{"value":["A","J","19.477710"],"label":{"show":1,"fontStyle":9}},{"value":["B","A","18.520617"],"label":{"show":1,"fontStyle":9}},{"value":["B","B","29.681415"],"label":{"show":1,"fontStyle":6}},{"value":["B","C","40.009102"],"label":{"show":1,"fontStyle":5}},{"value":["B","D","11.071915"],"label":{"show":1,"fontStyle":12}},{"value":["B","E","83.799897"],"label":{"show":1,"fontStyle":9}},{"value":["B","F","20.858075"],"label":{"show":1,"fontStyle":10}},{"value":["B","G","35.247695"],"label":{"show":1,"fontStyle":5}},{"value":["B","H","48.573601"],"label":{"show":1,"fontStyle":8}},{"value":["B","I","37.499165"],"label":{"show":1,"fontStyle":11}},{"value":["B","J","31.154316"],"label":{"show":1,"fontStyle":10}},{"value":["C","A","50.908878"],"label":{"show":1,"fontStyle":8}},{"value":["C","B","19.843065"],"label":{"show":1,"fontStyle":6}},{"value":["C","C","40.245523"],"label":{"show":1,"fontStyle":9}},{"value":["C","D","19.633769"],"label":{"show":1,"fontStyle":8}},{"value":["C","E","27.517222"],"label":{"show":1,"fontStyle":9}},{"value":["C","F","48.189429"],"label":{"show":1,"fontStyle":5}},{"value":["C","G","39.365442"],"label":{"show":1,"fontStyle":10}},{"value":["C","H","26.655601"],"label":{"show":1,"fontStyle":8}},{"value":["C","I","32.595514"],"label":{"show":1,"fontStyle":9}},{"value":["C","J","33.694636"],"label":{"show":1,"fontStyle":6}},{"value":["D","A","48.549834"],"label":{"show":1,"fontStyle":7}},{"value":["D","B","25.260674"],"label":{"show":1,"fontStyle":9}},{"value":["D","C","20.262019"],"label":{"show":1,"fontStyle":7}},{"value":["D","D","40.995637"],"label":{"show":1,"fontStyle":8}},{"value":["D","E","37.724818"],"label":{"show":1,"fontStyle":9}},{"value":["D","F","30.959030"],"label":{"show":1,"fontStyle":5}},{"value":["D","G","27.973470"],"label":{"show":1,"fontStyle":11}},{"value":["D","H","30.575312"],"label":{"show":1,"fontStyle":5}},{"value":["D","I","22.199978"],"label":{"show":1,"fontStyle":10}},{"value":["D","J","39.392962"],"label":{"show":1,"fontStyle":10}},{"value":["E","A","20.523432"],"label":{"show":1,"fontStyle":8}},{"value":["E","B","41.346767"],"label":{"show":1,"fontStyle":6}},{"value":["E","C","80.366180"],"label":{"show":1,"fontStyle":11}},{"value":["E","D","20.206162"],"label":{"show":1,"fontStyle":7}},{"value":["E","E","18.985302"],"label":{"show":1,"fontStyle":9}},{"value":["E","F"," 9.869327"],"label":{"show":1,"fontStyle":10}},{"value":["E","G","33.619347"],"label":{"show":1,"fontStyle":6}},{"value":["E","H","37.336090"],"label":{"show":1,"fontStyle":11}},{"value":["E","I","22.115589"],"label":{"show":1,"fontStyle":7}},{"value":["E","J","29.418666"],"label":{"show":1,"fontStyle":7}},{"value":["F","A","39.857192"],"label":{"show":1,"fontStyle":9}},{"value":["F","B","54.181296"],"label":{"show":1,"fontStyle":6}},{"value":["F","C","40.049746"],"label":{"show":1,"fontStyle":5}},{"value":["F","D","45.267285"],"label":{"show":1,"fontStyle":7}},{"value":["F","E","28.382914"],"label":{"show":1,"fontStyle":9}},{"value":["F","F","18.503701"],"label":{"show":1,"fontStyle":12}},{"value":["F","G","39.246708"],"label":{"show":1,"fontStyle":11}},{"value":["F","H","40.256547"],"label":{"show":1,"fontStyle":7}},{"value":["F","I","33.268287"],"label":{"show":1,"fontStyle":5}},{"value":["F","J","19.817903"],"label":{"show":1,"fontStyle":12}},{"value":["G","A","21.689709"],"label":{"show":1,"fontStyle":8}},{"value":["G","B","19.487107"],"label":{"show":1,"fontStyle":8}},{"value":["G","C","30.155433"],"label":{"show":1,"fontStyle":6}},{"value":["G","D","21.197128"],"label":{"show":1,"fontStyle":9}},{"value":["G","E","28.818613"],"label":{"show":1,"fontStyle":9}},{"value":["G","F","20.439555"],"label":{"show":1,"fontStyle":9}},{"value":["G","G","51.371273"],"label":{"show":1,"fontStyle":10}},{"value":["G","H","48.067453"],"label":{"show":1,"fontStyle":8}},{"value":["G","I","17.476125"],"label":{"show":1,"fontStyle":8}},{"value":["G","J","53.350189"],"label":{"show":1,"fontStyle":9}},{"value":["H","A","40.610999"],"label":{"show":1,"fontStyle":8}},{"value":["H","B","38.568800"],"label":{"show":1,"fontStyle":6}},{"value":["H","D","30.413037"],"label":{"show":1,"fontStyle":6}},{"value":["H","E","32.482028"],"label":{"show":1,"fontStyle":10}},{"value":["H","F","30.399238"],"label":{"show":1,"fontStyle":9}},{"value":["H","G","29.264279"],"label":{"show":1,"fontStyle":9}},{"value":["H","H","10.836654"],"label":{"show":1,"fontStyle":9}},{"value":["H","I","53.669638"],"label":{"show":1,"fontStyle":11}},{"value":["H","J","39.860697"],"label":{"show":1,"fontStyle":6}},{"value":["I","B","10.689721"],"label":{"show":1,"fontStyle":8}},{"value":["I","C","30.381533"],"label":{"show":1,"fontStyle":11}},{"value":["I","D","37.766585"],"label":{"show":1,"fontStyle":5}},{"value":["I","E"," 9.944084"],"label":{"show":1,"fontStyle":6}},{"value":["I","F","41.677503"],"label":{"show":1,"fontStyle":5}},{"value":["I","G","20.302945"],"label":{"show":1,"fontStyle":8}},{"value":["I","H","22.435191"],"label":{"show":1,"fontStyle":7}},{"value":["I","I","58.888788"],"label":{"show":1,"fontStyle":6}},{"value":["I","J"," 8.645899"],"label":{"show":1,"fontStyle":6}},{"value":["J","A","10.395865"],"label":{"show":1,"fontStyle":8}},{"value":["J","C","47.225554"],"label":{"show":1,"fontStyle":11}},{"value":["J","D"," 9.698159"],"label":{"show":1,"fontStyle":10}},{"value":["J","E","40.131022"],"label":{"show":1,"fontStyle":10}},{"value":["J","F"," 9.917820"],"label":{"show":1,"fontStyle":9}},{"value":["J","G","41.337387"],"label":{"show":1,"fontStyle":8}},{"value":["J","H"," 8.785856"],"label":{"show":1,"fontStyle":5}},{"value":["J","I","19.218070"],"label":{"show":1,"fontStyle":9}},{"value":["J","J","20.514580"],"label":{"show":1,"fontStyle":7}}],"name":null,"type":"heatmap","coordinateSystem":"cartesian2d"}],"visualMap":[{"calculable":true,"type":"continuous","min":8.645898960806047,"max":83.79989668271548}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
