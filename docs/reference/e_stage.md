<div id="main" class="col-md-9" role="main">

# Stage chart

<div class="ref-description section level2">

Draw a stage plot.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_stage(
  e,
  start,
  end,
  stage,
  legend = TRUE,
  name = "stage",
  borderRadius = 8,
  verticalMargin = 10,
  minHorizontalSize = 3,
  envelope = list(show = TRUE, color = "#888", opacity = 0.25, externalRadius = 8),
  axisLabel = list(formatter = NULL, color = "#8A8A8A"),
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

-   start:

    column for start of stage on x axis

-   end:

    column for end of stage on x axis

-   stage:

    column for stage on y axis

-   legend:

    Whether to add serie to legend.

-   name:

    name of the serie.

-   borderRadius:

    The border radius of the stage.

-   verticalMargin:

    The vertical margin of the bars.

-   minHorizontalSize:

    The minimum width of the bars.

-   envelope:

    The envelope of the stage.

-   axisLabel:

    The style of the axis label.

-   ...:

    additional options

</div>

<div class="section level2">

## See also

<div class="dont-index">

[official
documentation](https://github.com/apache/echarts-custom-series/tree/main/custom-series/stage)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(
  start = as.POSIXct(c(
    "2024-09-07 06:12", "2024-09-07 06:15", "2024-09-07 05:45",
    "2024-09-07 04:57", "2024-09-07 06:12", "2024-09-07 06:18"
  )),

  end = as.POSIXct(c(
    "2024-09-07 06:12", "2024-09-07 06:18", "2024-09-07 06:12",
    "2024-09-07 05:45", "2024-09-07 06:15", "2024-09-07 07:37"
  )),

  stage = c(
    "Awake", "Awake",  "REM",
    "Core", "Core", "Deep"
  ),
  stringsAsFactors = FALSE
 )
stage_order = c( "Deep", "Core","REM", "Awake")

df |>
  e_charts() |>
  e_stage(start = start,
          end = end,
          stage = stage) |>
          e_x_axis(type = 'time') |>
          e_y_axis(type = 'category', data = stage_order)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"type":"category","data":["Deep","Core","REM","Awake"]}],"series":[{"type":"custom","renderItem":"stage","colorBy":"data","encode":{"x":[0,1],"y":2,"tooltip":[0,1]},"name":"stage","itemPayload":{"borderRadius":8,"verticalMargin":10,"minHorizontalSize":3,"envelope":{"show":true,"color":"#888","opacity":0.25,"externalRadius":8},"axisLabel":{"formatter":null,"color":"#8A8A8A"}}}],"legend":{"data":["stage"]},"dataset":{"source":[["2024-09-07T04:12:00Z","2024-09-07T04:12:00Z","Awake"],["2024-09-07T04:15:00Z","2024-09-07T04:18:00Z","Awake"],["2024-09-07T03:45:00Z","2024-09-07T04:12:00Z","REM"],["2024-09-07T02:57:00Z","2024-09-07T03:45:00Z","Core"],["2024-09-07T04:12:00Z","2024-09-07T04:15:00Z","Core"],["2024-09-07T04:18:00Z","2024-09-07T05:37:00Z","Deep"]]},"xAxis":{"type":"time"}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
