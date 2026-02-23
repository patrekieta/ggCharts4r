<div id="main" class="col-md-9" role="main">

# Polar

<div class="ref-description section level2">

Customise polar coordinates.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_polar(e, show = TRUE, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   show:

    Whether to display the axis.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional arguments](https://echarts.apache.org/en/option.html#polar)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(x = 1:10, y = seq(1, 20, by = 2))

df |>
  e_charts(x) |>
  e_polar() |>
  e_angle_axis() |>
  e_radius_axis() |>
  e_line(y, coord_system = "polar", smooth = TRUE)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"polar":{"show":true},"angleAxis":{"show":true},"radiusAxis":{"show":true},"legend":{"data":["y"]},"series":[{"data":[1,3,5,7,9,11,13,15,17,19],"name":"y","type":"line","coordinateSystem":"polar","smooth":true}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
