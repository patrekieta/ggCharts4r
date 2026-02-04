<div id="main" class="col-md-9" role="main">

# Generate Matrix

<div class="ref-description section level2">

helper function for generating default

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_matrix_raw(rows = NULL, cols = NULL, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   rows, cols:

    provide integer values for the number of rows and columns in the
    matrix grid

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
e_matrix_raw(rows = 3, cols = 3, backgroundStyle=list(borderWidth=0))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":[null,null,null],"show":false},"y":{"data":[null,null,null],"show":false},"backgroundStyle":{"borderWidth":0}}},"dispose":true},"evals":[],"jsHooks":[]}
e_matrix_raw(rows = 3, cols = 3, body = list(itemStyle = list(borderWidth = 0)))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"matrix":{"x":{"data":[null,null,null],"show":false},"y":{"data":[null,null,null],"show":false},"body":{"itemStyle":{"borderWidth":0}}}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
