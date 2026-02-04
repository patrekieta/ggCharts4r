<div id="main" class="col-md-9" role="main">

# Parallel

<div class="ref-description section level2">

Draw parallel coordinates.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_parallel(e, ..., name = NULL, rm_x = TRUE, rm_y = TRUE, opts = list())

e_parallel_(e, ..., name = NULL, rm_x = TRUE, rm_y = TRUE, opts = list())
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   ...:

    Columns to select from the data passed to `e_charts`.

-   name:

    name of the serie.

-   rm_x, rm_y:

    Whether to remove x and y axis, defaults to `TRUE`.

-   opts:

    A list of additional options to pass to the serie.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#series-parallel)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(
  price = rnorm(5, 10),
  amount = rnorm(5, 15),
  letter = LETTERS[1:5]
)

df |>
  e_charts() |>
  e_parallel(price, amount, letter, opts = list(smooth = TRUE))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"series":{"name":null,"type":"parallel","data":[["10.386435","15.04492","A"],["8.389964","15.72566","B"],["11.760761","14.30748","C"],["9.013599","14.26416","D"],["11.996950","14.80526","E"]],"smooth":true},"parallelAxis":[{"dim":0,"name":"price"},{"dim":1,"name":"amount"},{"dim":2,"name":"letter","type":"category","data":["A","B","C","D","E"]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
