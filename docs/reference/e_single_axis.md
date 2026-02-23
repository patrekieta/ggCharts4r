<div id="main" class="col-md-9" role="main">

# Single Axis

<div class="ref-description section level2">

Setup single axis.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_single_axis(e, index = 0, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   index:

    Index of axis to customise.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(
  axis = LETTERS[1:10],
  value = runif(10, 3, 20),
  size = runif(10, 3, 20)
)

df |>
  e_charts(axis) |>
  e_single_axis() |> # add the single axis
  e_scatter(
    value,
    size,
    coord_system = "singleAxis"
  )

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"singleAxis":{"type":"category","data":["A","B","C","D","E","F","G","H","I","J"]},"legend":{"data":["value"]},"series":[{"data":[{"value":["A","14.965604"," 7.172316"," 5.081728"]},{"value":["B","10.792073","19.718881","20.000000"]},{"value":["C","12.000164","18.383641","18.412357"]},{"value":["D","18.640727","14.986178","14.372663"]},{"value":["E"," 8.754958","18.170802","18.159283"]},{"value":["F","18.147561","10.356471"," 8.867792"]},{"value":["G","19.591992","14.266882","13.517396"]},{"value":["H","11.283864","17.499860","17.361512"]},{"value":["I","16.060058"," 3.739502"," 1.000000"]},{"value":["J","18.416140"," 5.029583"," 2.533949"]}],"name":"value","type":"scatter","symbol":null,"coordinateSystem":"singleAxis","singleAxisIndex":0,"symbolSize":"function(data){ return data[3];}"}]},"dispose":true},"evals":["opts.series.0.symbolSize"],"jsHooks":[]}
```

</div>

</div>

</div>
