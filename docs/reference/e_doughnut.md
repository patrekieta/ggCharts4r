<div id="main" class="col-md-9" role="main">

# Segmented Doughnut

<div class="ref-description section level2">

Draw segmented doughnut.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_doughnut(
  e,
  numerator = NULL,
  denominator = NULL,
  formatter = "{c}/{b}",
  fontSize = "10em",
  fontColor = "#555",
  center = c("50%", "50%"),
  radius = c("50%", "65%"),
  rm_x = TRUE,
  rm_y = TRUE,
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

-   numerator, denominator:

    numeraetor to provide filled segments and denominator for total
    segments.

-   formatter:

    javascript string formatter for center text of chart.

-   fontSize, fontColor:

    font values for center text of chart.

-   center, radius:

    center provides relative position of the center of chart while
    radius provides the radius of your circle for outer segments.

-   rm_x, rm_y:

    Whether to remove x and y axis, defaults to `TRUE`.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[official
documentation](https://github.com/apache/echarts-custom-series/tree/main/custom-series/segmentedDoughnut)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
e_chart() |>
 e_doughnut(numerator = 3, denominator = 6)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"series":[{"type":"custom","renderItem":"segmentedDoughnut","coordinateSystem":"none","itemPayload":{"center":["50%","50%"],"radius":["50%","65%"],"segmentCount":6,"label":{"show":true,"formatter":"{c}/{b}","fontSize":"10em","color":"#555"}},"data":[3]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
