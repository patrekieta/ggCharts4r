<div id="main" class="col-md-9" role="main">

# Format Matrix Axis

<div class="ref-description section level2">

helper function for formatting the x and y axes for a matrix grid.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_format_matrix_axis(e, axis = "x", ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   axis:

    indicate which axis shoud be adjusted

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional arguments](https://echarts.apache.org/en/option.html#matrix)

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
e_format_matrix_axis(axis = "x", label = list(color = "red"))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":["Class1","Class2","Class3"],"name":"Class","label":{"color":"red"}},"y":{"data":["Grade1","Grade2","Grade3"],"name":"Grade"}}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
