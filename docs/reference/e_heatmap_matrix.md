<div id="main" class="col-md-9" role="main">

# Generate heatmap for matrix

<div class="ref-description section level2">

Draw heatmap chart in matrix coordinate system

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_heatmap_matrix(e, z_val, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   z_val:

    Column name for data to be used for heatmap

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
 e_matrix_corner(value = "All School", label = list(
   fontSize = 24, color = "#555", position = "inside")) |>
 e_heatmap(A, coord_system = "matrix") |>
 e_labels(position = "inside",
          formatter = htmlwidgets::JS(
            'function(params){return(params.value[2]);}'),
          color = "#555",
          fontWeight = "bold")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":[{"value":"Primary","children":["Class1","Class2"]},{"value":"High","children":["Class3"]}],"name":"Class"},"y":{"data":["Grade1","Grade2","Grade3"],"name":"Grade"},"corner":{"data":[{"coord":[-1,-1],"value":"All School","mergeCells":true,"coordClamp":false}],"label":{"fontSize":24,"color":"#555","position":"inside"}}},"series":[{"type":"heatmap","coordinateSystem":"matrix","data":[["Class1","Grade1",6],["Class1","Grade2",1],["Class1","Grade3",7],["Class2","Grade1",3],["Class2","Grade2",8],["Class2","Grade3",4],["Class3","Grade1",9],["Class3","Grade2",10],["Class3","Grade3",5]],"label":{"show":true,"position":"inside","formatter":"function(params){return(params.value[2]);}","color":"#555","fontWeight":"bold"}}]},"dispose":true},"evals":["opts.series.0.label.formatter"],"jsHooks":[]}
df |> e_chart() |>
 e_matrix(xAxis = "Class", yAxis = "Grade") |>
 e_heatmap_matrix("A") |>
 e_labels(position = "inside",
          formatter = htmlwidgets::JS(
            'function(params){return(params.value[2]);}'),
          fontWeight = "bold") |>
 e_visual_map(A, inRange = list(color = c("#bf444c", "#d88273", "#f6efa6")))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":["Class1","Class2","Class3"],"name":"Class"},"y":{"data":["Grade1","Grade2","Grade3"],"name":"Grade"}},"series":[{"type":"heatmap","coordinateSystem":"matrix","data":[["Class1","Grade1",6],["Class1","Grade2",1],["Class1","Grade3",7],["Class2","Grade1",3],["Class2","Grade2",8],["Class2","Grade3",4],["Class3","Grade1",9],["Class3","Grade2",10],["Class3","Grade3",5]],"label":{"show":true,"position":"inside","formatter":"function(params){return(params.value[2]);}","fontWeight":"bold"}}],"visualMap":[{"inRange":{"color":["#bf444c","#d88273","#f6efa6"]},"calculable":true,"type":"continuous","min":1,"max":10}]},"dispose":true},"evals":["opts.series.0.label.formatter"],"jsHooks":[]}
```

</div>

</div>

</div>
