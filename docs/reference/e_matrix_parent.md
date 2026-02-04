<div id="main" class="col-md-9" role="main">

# Generate Matrix Axis Parents

<div class="ref-description section level2">

helper function for generating parent values for x or y axis headers

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_matrix_parent(e, axis = "x", value, children, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   axis:

    which axis the parent should be added

-   value:

    text for the new parent header cell

-   children:

    vector containing values for which current header cells will be
    children for the new parent cell

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#matrix.x.data)

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
e_matrix_parent(value = "High", children = "Class3")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":[{"value":"Primary","children":["Class1","Class2"]},{"value":"High","children":["Class3"]}],"name":"Class"},"y":{"data":["Grade1","Grade2","Grade3"],"name":"Grade"}}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
