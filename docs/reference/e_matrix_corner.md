<div id="main" class="col-md-9" role="main">

# Fill Matrix Axis Corner

<div class="ref-description section level2">

helper function for adding data to the corner of matrix

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_matrix_corner(
  e,
  coord = c(-1, -1),
  value,
  mergeCells = TRUE,
  coordClamp = FALSE,
  ...
)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   coord:

    corner cell coordinate location

-   value:

    text to display in corner cell

-   mergeCells:

    whether the body cells and corner cells can be merged

-   coordClamp:

    determines whether null values can be used to indicate an entire
    row/column

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#matrix.corner)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame("Class" = rep(c("Class1", "Class2", "Class3"),each = 3),
"Grade" = c("Grade1","Grade2", "Grade3"),
"A" = sample(1:10, 9),
"B" = sample(1:10,9))

df |> e_charts() |> e_matrix(xAxis = "Class", yAxis = "Grade") |>
e_matrix_parent(value = "Primary", children = c("Class1", "Class2")) |>
e_matrix_parent(value = "High", children = "Class3") |>
e_matrix_corner(value = "All School",
label = list(fontSize = 24, color = "#555", position = "inside"))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":[{"value":"Primary","children":["Class1","Class2"]},{"value":"High","children":["Class3"]}],"name":"Class"},"y":{"data":["Grade1","Grade2","Grade3"],"name":"Grade"},"corner":{"data":[{"coord":[-1,-1],"value":"All School","mergeCells":true,"coordClamp":false}],"label":{"fontSize":24,"color":"#555","position":"inside"}}}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
