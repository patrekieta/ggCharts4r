<div id="main" class="col-md-9" role="main">

# Generate scatter point for matrix

<div class="ref-description section level2">

Draw scatter points chart in matrix coordinate system

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_scatter_matrix(e, z, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   z:

    Column name for data to be used for scatter points

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#series-scatter)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame("Class" = rep(c("Class1", "Class2", "Class3"),each = 3),
                   "Grade" = c("Grade1","Grade2", "Grade3"),
                  "A" = sample(1:10, 9))

df |> e_chart() |>
 e_matrix(xAxis = "Class", yAxis = "Grade") |>
 e_matrix_parent(value = "Primary", children = c("Class1", "Class2")) |>
 e_matrix_parent(value = "High", children = "Class3") |>
 e_matrix_corner(value = "All School",
   label = list(fontSize = 24, color = "#555", position = "inside")) |>
 e_scatter(A, coord_system = "matrix", symbolSize = 0) |>
 e_labels(position = "inside",
          formatter = htmlwidgets::JS(
           'function(params){return(params.value[2]);}'),
          color = "#555",
          fontWeight = "bold")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":[{"value":"Primary","children":["Class1","Class2"]},{"value":"High","children":["Class3"]}],"name":"Class"},"y":{"data":["Grade1","Grade2","Grade3"],"name":"Grade"},"corner":{"data":[{"coord":[-1,-1],"value":"All School","mergeCells":true,"coordClamp":false}],"label":{"fontSize":24,"color":"#555","position":"inside"}}},"series":[{"type":"scatter","coordinateSystem":"matrix","data":[["Class1","Grade1",2],["Class1","Grade2",1],["Class1","Grade3",10],["Class2","Grade1",9],["Class2","Grade2",4],["Class2","Grade3",8],["Class3","Grade1",5],["Class3","Grade2",3],["Class3","Grade3",6]],"symbolSize":0,"label":{"show":true,"position":"inside","formatter":"function(params){return(params.value[2]);}","color":"#555","fontWeight":"bold"}}]},"dispose":true},"evals":["opts.series.0.label.formatter"],"jsHooks":[]}
df |> e_chart() |>
 e_matrix(xAxis = "Class", yAxis = "Grade") |>
 e_scatter_matrix("A") |>
 e_labels(position = "inside",
          formatter = htmlwidgets::JS('function(params){return(params.value[2]);}'),
          color = "#555",
          fontWeight = "bold") |>
 e_visual_map(A, inRange = list(symbolSize = c(1,50)))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":["Class1","Class2","Class3"],"name":"Class"},"y":{"data":["Grade1","Grade2","Grade3"],"name":"Grade"}},"series":[{"type":"scatter","coordinateSystem":"matrix","data":[["Class1","Grade1",2],["Class1","Grade2",1],["Class1","Grade3",10],["Class2","Grade1",9],["Class2","Grade2",4],["Class2","Grade3",8],["Class3","Grade1",5],["Class3","Grade2",3],["Class3","Grade3",6]],"label":{"show":true,"position":"inside","formatter":"function(params){return(params.value[2]);}","color":"#555","fontWeight":"bold"}}],"visualMap":[{"inRange":{"symbolSize":[1,50]},"calculable":true,"type":"continuous","min":1,"max":10}]},"dispose":true},"evals":["opts.series.0.label.formatter"],"jsHooks":[]}
```

</div>

</div>

</div>
