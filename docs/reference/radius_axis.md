<div id="main" class="col-md-9" role="main">

# Radius axis

<div class="ref-description section level2">

Customise radius axis.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_radius_axis(e, serie, show = TRUE, ...)

e_radius_axis_(e, serie = NULL, show = TRUE, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   serie:

    Serie to use as axis labels.

-   show:

    Whether to display the axis.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#radiusAxis)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(x = LETTERS[1:10], y = seq(1, 20, by = 2))

df |>
  e_charts(x) |>
  e_polar() |>
  e_angle_axis() |>
  e_radius_axis(x) |>
  e_bar(y, coord_system = "polar")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"polar":{"show":true},"angleAxis":{"show":true},"radiusAxis":{"show":true,"data":["A","B","C","D","E","F","G","H","I","J"]},"legend":{"data":["y"]},"series":[{"data":[1,3,5,7,9,11,13,15,17,19],"name":"y","type":"bar","yAxisIndex":0,"xAxisIndex":0,"coordinateSystem":"polar"}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
