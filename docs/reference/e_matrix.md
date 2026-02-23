<div id="main" class="col-md-9" role="main">

# Generate Matrix

<div class="ref-description section level2">

helper function for generating the x and y axes for a matrix grid.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_matrix(e, xAxis, yAxis, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   xAxis, yAxis:

    provide column name of dataframe to generate X-axis and Y-axis
    header cells

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

df |> e_charts() |> e_matrix(xAxis = "Class", yAxis = "Grade")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":["Class1","Class2","Class3"],"name":"Class"},"y":{"data":["Grade1","Grade2","Grade3"],"name":"Grade"}}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
