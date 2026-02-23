<div id="main" class="col-md-9" role="main">

# Bar range chart

<div class="ref-description section level2">

Draw a bar range plot with labels on each end.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_barRange(
  e,
  lower,
  upper,
  name = "barRange",
  legend = TRUE,
  y_index = 0,
  x_index = 0,
  barWidth = 10,
  borderRadius = 5,
  margin = 10,
  textSymbol = "F",
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

-   lower, upper:

    series of lower and upper borders of the band

-   name:

    name of the serie.

-   legend:

    Whether to add serie to legend.

-   x_index, y_index:

    Indexes of x and y axis.

-   barWidth:

    width of each bar

-   borderRadius:

    roundness of the bar ends

-   margin:

    space between the text labels and the bar

-   textSymbol:

    string for the label to end with

-   ...:

    additional options

</div>

<div class="section level2">

## See also

<div class="dont-index">

[official
documentation](https://github.com/apache/echarts-custom-series/tree/main/custom-series/barRange)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- iris |>
  dplyr::group_by(Species) |>
  dplyr::summarise(min_length = min(Sepal.Length),
                   max_length = max(Sepal.Length))

df |> e_chart(Species) |>
  e_barRange(lower = min_length,
             upper = max_length,
             textSymbol = '"'
  )

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"data":["setosa","versicolor","virginica"],"type":"category","boundaryGap":true}],"series":[{"type":"custom","renderItem":"barRange","name":"barRange","encode":{"x":0,"y":[1,2],"tooltip":[1,2]},"data":[{"value":["setosa","4.3","5.8"]},{"value":["versicolor","4.9","7.0"]},{"value":["virginica","4.9","7.9"]}],"itemPayload":{"textSymbol":"\"","barWidth":10,"borderRadius":5,"margin":10}},{"data":[{"value":["setosa","4.3","5.8"]},{"value":["versicolor","4.9","7.0"]},{"value":["virginica","4.9","7.9"]}]}],"legend":{"data":["barRange"]}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
