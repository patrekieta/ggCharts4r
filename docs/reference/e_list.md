<div id="main" class="col-md-9" role="main">

# List

<div class="ref-description section level2">

simply pass a list of options, similar to a `JSON`.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_list(e, list, append = FALSE)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   list:

    A `list` of options passed to `setOptions`.

-   append:

    if `TRUE` the `list` is appended to the options, otherwise it
    *overwrites* everything.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
N <- 20 # data points

opts <- list(
  xAxis = list(
    type = "category",
    data = LETTERS[1:N]
  ),
  yAxis = list(
    type = "value"
  ),
  series = list(
    list(
      type = "line",
      data = round(runif(N, 5, 20))
    )
  )
)

e_charts() |>
  e_list(opts)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"xAxis":{"type":"category","data":["A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T"]},"yAxis":{"type":"value"},"series":[{"type":"line","data":[12,19,8,12,13,13,17,8,10,18,19,16,5,15,7,6,14,7,7,9]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
