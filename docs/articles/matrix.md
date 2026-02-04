<div id="main" role="main">

# Matrix

Build charts using the new matrix system added in [Echarts
v6](https://echarts.apache.org/handbook/en/basics/release-note/v6-feature/#).
`echarts4r` now comes with a highly customisable matrix coordinate
system, which in some methods is easier to use than the previous grid
functionality. Build custom tables using the new matrix functions. Note
that as of Echarts4r v0.5.0, timelines are not currently supported with
matrix functions.

<div class="section level2">

## Matrix

To get started with using a matrix, there are a few options you can use.
The two starting options consist of `e_matrix` and `e_matrix_raw`. You
can learn more about the matrix system using the [official
documentation](https://echarts.apache.org/en/option.html#matrix) for
additional details. It is worth mentioning that not all series will
support the matrix system and some require the matrix to be used in
combination with the already existing grid system. See the table at the
bottom of the page for additional details.

Now let’s get started with building some matrix charts! `e_matrix` will
take two columns that contain your x and y groupings and will plot the
unique combinations in a table style format. There is no need to use
`group_by` with the matrix functions.

<div id="cb1" class="sourceCode">

``` r
df <- data.frame("Class" = rep(c("Class1", "Class2", "Class3"),each = 3),
"Grade" = c("Grade1","Grade2", "Grade3"))

df |> 
  e_charts() |> 
  e_matrix(xAxis = "Class", yAxis = "Grade")
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

If we only want to create the table with no additional headers or column
names, we can instead use the `e_matrix_raw` to generate the matrix.
This will be especially useful when adding new charts directly to the
matrix later on. When using `e_matrix_raw` you will need to specify how
many columns and rows you want in your table.

<div id="cb2" class="sourceCode">

``` r
e_matrix_raw(rows = 3, cols = 3, backgroundStyle=list(borderWidth=0))
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

All tables are fully customizable through the supported css options
found [here](https://echarts.apache.org/en/option.html#matrix.body). We
can use these options to fully remove the lines of the table leaving an
blank matrix if desired.

</div>

<div class="section level2">

## Format matrix

There are a few other ways that we can customize our matrix table to
reach our desired output. First we can take our initial example from
`e_matrix` and add some text to the corner cell of the headers. To do
this, we will use `e_matrix_corner` to access that corner cell.
Documentation for the corner cell can be found
[here](https://echarts.apache.org/en/option.html#matrix.corner).

<div id="cb3" class="sourceCode">

``` r
df |> 
  e_charts() |> 
  e_matrix(xAxis = "Class", yAxis = "Grade") |> 
  e_matrix_corner(value = "Schools")
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Now we can add additional levels to our headers. This is done using
`e_matrix_parent` to add new levels. To use this function, we will give
it our new text value. We also need to specify which existing headers
will be children of this new header parent. As you mess around with
`e_matrix_parent` you may notice that additional cells are being
generated for the corner of the table. In `e_matrix_corner` we can
specify where we want that corner value to go using the coord attribute.
As of Echarts4r v0.5.0, there is no way to add new children to the
headers.

<div id="cb4" class="sourceCode">

``` r
df |> e_charts() |> 
  e_matrix(xAxis = "Class", yAxis = "Grade") |>
  e_matrix_parent(value = "Primary", children = c("Class1", "Class2")) |>
  e_matrix_parent(value = "High", children = "Class3") |>
  e_matrix_parent(value = "ALL", children = c("Primary", "High")) |>
  e_matrix_corner(value = "Schools", coord = c(-1,-2))
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

When working with the matrix functions, it is important to remember that
the coordinate system is formatted as \[col_number, row_number\].
Additionally, row and column counting starts at 0. If we need to make
additional changes to how our headers look, we can easily access the
formatting options using `e_format_matrix_axis`. Documentation for the
axis options can be found
[here](https://echarts.apache.org/en/option.html#matrix.x).

<div id="cb5" class="sourceCode">

``` r
df |> 
  e_charts() |> 
  e_matrix(xAxis = "Class", yAxis = "Grade") |> 
  e_matrix_corner(value = "Schools") |>
  e_matrix_parent(value = "Primary", children = c("Class1", "Class2")) |>
  e_format_matrix_axis(axis = "y", label = list(color = "red")) |>
  e_format_matrix_axis(axis = "x", itemStyle = list(color = "#999"), label = list(fontSize = 25))
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Adding charts

<div class="section level3">

### Table Style

Now that we have built our table, we can start adding some charts to
each cell. In order to do this, we will use `e_matrix_addChart`. This
will allows us to pre-build an Echart and add it to a specific cell
(Note: Each Echart will need a unique ID when added to the matrix).

Let’s get building! First we can build some basic charts that we want to
add.

<div id="cb6" class="sourceCode">

``` r
echart1 <- iris |>
  group_by(Species) |>
  e_charts(Sepal.Length) |>
  e_line(Sepal.Width) |>
  e_tooltip(trigger = "axis")

echart2 <- mtcars |>
  head() |>
  tibble::rownames_to_column("model") |>
  e_charts(model) |>
  e_pie(carb)

echart3 <- mtcars |>
  tibble::rownames_to_column("model") |>
  mutate(total = mpg + qsec) |>
  arrange(desc(total)) |>
  e_charts(model) |>
  e_bar(mpg, stack = "grp") |>
  e_bar(qsec, stack = "grp") |>
  e_tooltip(trigger = "item")

echart4 <- iris |>
  e_charts() |>
  e_boxplot(Sepal.Length) |>
  e_tooltip()


df |> 
  e_charts() |> 
  e_matrix(xAxis = "Class", yAxis = "Grade") |> 
  e_matrix_corner(value = "Schools") |>
  e_matrix_addChart(chart = echart1, id = "Chart1", coord = c(0,0)) |>
  e_matrix_addChart(chart = echart2, id = "Chart2", coord = c(1,1), legend = FALSE) |>
  e_matrix_addChart(chart = echart3, id = "Chart3", coord = c(2,1))
```

</div>

<div id="htmlwidget-10b3b7155e8045a1b2ad"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level3">

### Dashboard style

In addition to filling single cells of the matrix, we can also fill
multiple / merge multiple cells. To do this we use the format
\[(col_start, col_end), (row_start, row_end)\]. This functionality can
be used to create dashboard style presentations of multiple charts.

<div id="cb7" class="sourceCode">

``` r
e_matrix_raw(3,3, body = list(itemStyle = list(borderWidth = 0))) |>
  e_matrix_addChart(echart1, id = "Chart1", coord = list(c(0,2),0)) |>
  e_matrix_addChart(echart3, id = "Chart2", coord = list(c(1,2),c(1,2))) |>
  e_matrix_addChart(echart4, id = "Chart3", coord = list(0,c(1,2)), legend = FALSE) |>
  e_tooltip()
```

</div>

<div id="htmlwidget-4018eef1a407a0df6b52"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level3">

### geoFacet style

Inspired by the [geofacet package](https://hafen.github.io/geofacet/)
for ggplot, you can now use the matrix system to generate tables that
are shaped like a specified grid. This functionality supports custom
grids or a string containing the name of an existing geofacet grid. You
can find the pre-built grids
[here](https://hafen.github.io/geofacet/reference/grids.html).

<div id="cb8" class="sourceCode">

``` r
df <- data.frame(group = rep(letters[1:6], each = 20),
  date = seq(from = as.Date("2025-01-01"),
             to = as.Date("2025-01-20"), by = "day"),
  temp = sample(c(10:20), size = 60, replace = TRUE))

grid <- data.frame(name = unique(df$group), row = c(1:6), col = c(1:6))

df |>
  group_by(group) |>
  e_chart(date) |>
  e_line(temp, symbol = "none") |>
  e_x_axis(splitNumber = 2) |>
  e_y_axis(splitNumber = 2) |>
  e_geoFacet(legend = FALSE,
             grid = grid,
             margin_trbl = c("t"="25%"),
             left = "5%",
             width = "90%") |>
  e_title(text = "Group Temps") |>
  e_tooltip(trigger = "axis")
```

</div>

<div id="htmlwidget-5b1b2f4ad92281566982"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

We can also add titles to each graph using `e_title_matrix`.

<div id="cb9" class="sourceCode">

``` r
df |>
  group_by(group) |>
  e_chart(date) |>
  e_line(temp, symbol = "none") |>
  e_x_axis(splitNumber = 2) |>
  e_y_axis(splitNumber = 2) |>
  e_geoFacet(legend = FALSE,
             grid = grid,
             margin_trbl = c("t"="25%"),
             left = "5%",
             width = "90%") |>
  e_title(text = "Group Temps") |>
  e_tooltip(trigger = "axis") |>
  e_title_matrix()
```

</div>

<div id="htmlwidget-25c3e940e6859592f801"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>

<div class="section level2">

## Supported Series

<div class="section level3">

### Heatmap Chart

<div id="cb10" class="sourceCode">

``` r
df <- data.frame("Class" = rep(c("Class1", "Class2", "Class3"),each = 3),
                   "Grade" = c("Grade1","Grade2", "Grade3"),
                  "A" = sample(1:10, 9),
                  "B" = sample(1:10,9),
                  "C" = sample(1:10,9))

df |> e_chart() |>
 e_matrix(xAxis = "Class", yAxis = "Grade") |>
 e_heatmap(A, coord_system = "matrix") |>
 e_labels(position = "inside",
          formatter = htmlwidgets::JS(
            'function(params){return(params.value[2]);}'),
          fontWeight = "bold") |>
 e_visual_map(A, inRange = list(color = c("#bf444c", "#d88273", "#f6efa6")))
```

</div>

<div id="htmlwidget-3f27c09be0c60bb52829"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level3">

### Pie Chart

<div id="cb11" class="sourceCode">

``` r
df |> e_chart() |>
 e_matrix(xAxis = "Class", yAxis = "Grade") |>
 e_pie_(serie = c("A","B","C"), coord_system = "matrix", label = list(show = FALSE))
```

</div>

<div id="htmlwidget-416566eb193bf50d04e6"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level3">

### Scatter Chart

<div id="cb12" class="sourceCode">

``` r
df |> e_chart() |>
 e_matrix(xAxis = "Class", yAxis = "Grade") |>
 e_scatter(A, coord_system = "matrix", symbolSize = 20) |>
 e_labels(position = "inside",
          formatter = htmlwidgets::JS(
           'function(params){return(params.value[2]);}'),
          color = "black",
          fontWeight = "bold") |>
  e_visual_map(A, inRange = list(symbolSize = c(20,50)))
```

</div>

<div id="htmlwidget-72cbf064100ce560a04c"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>

<div class="section level2">

## [Matrix Support](https://echarts.apache.org/en/option.html#series-line.coordinateSystem)

|                                               | no coord sys                               | [grid](#grid) (cartesian2d) | [polar](#polar) | [geo](#geo) | [singleAxis](#singleAxis) | [radar](#radar) | [parallel](#parallel) | [calendar](#calendar)                                           | [matrix](#matrix)                                               |
|-----------------------------------------------|--------------------------------------------|-----------------------------|-----------------|-------------|---------------------------|-----------------|-----------------------|-----------------------------------------------------------------|-----------------------------------------------------------------|
| [grid](#grid) (cartesian2d)                   | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [polar](#polar)                               | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [geo](#geo)                                   | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [singleAxis](#singleAxis)                     | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [calendar](#calendar)                         | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ❌                                                              | ❌                                                              |
| [matrix](#matrix)                             | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ❌                                                              | ❌                                                              |
| [series-line](#series-line)                   | ❌                                         | ✅                          | ✅              | ❌          | ❌                        | ❌              | ❌                    | ❌ (✅ if via another coord sys like [grid](#grid))             | ❌ (✅ if via another coord sys like [grid](#grid))             |
| [series-bar](#series-bar)                     | ❌                                         | ✅                          | ✅              | ❌          | ❌                        | ❌              | ❌                    | ❌ (✅ if via another coord sys like [grid](#grid))             | ❌ (✅ if via another coord sys like [grid](#grid))             |
| [series-pie](#series-pie)                     | ✅                                         | ✅                          | ✅              | ✅          | ✅                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-scatter](#series-scatter)             | ❌                                         | ✅                          | ✅              | ✅          | ✅                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-effectScatter](#series-effectScatter) | ❌                                         | ✅                          | ✅              | ✅          | ✅                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-radar](#series-radar)                 | ❌                                         | ❌                          | ❌              | ❌          | ❌                        | ✅              | ❌                    | ❌ (✅ if via [radar](#radar) coord sys)                        | ❌ (✅ if via [radar](#radar) coord sys)                        |
| [series-tree](#series-tree)                   | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-treemap](#series-treemap)             | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-sunburst](#series-sunburst)           | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-boxplot](#series-boxplot)             | ❌                                         | ✅                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ❌ (✅ if via another coord sys like [grid](#grid))             | ❌ (✅ if via another coord sys like [grid](#grid))             |
| [series-candlestick](#series-candlestick)     | ❌                                         | ✅                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ❌ (✅ if via another coord sys like [grid](#grid))             | ❌ (✅ if via another coord sys like [grid](#grid))             |
| [series-heatmap](#series-heatmap)             | ❌                                         | ✅                          | ❌              | ✅          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-map](#series-map)                     | ✅ (create a geo coord sys exclusively)    | ❌                          | ❌              | ✅          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-parallel](#series-parallel)           | ❌                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ✅                    | ❌ (✅ if via [parallel](#parallel) coord sys)                  | ❌ (✅ if via [parallel](#parallel) coord sys)                  |
| [series-lines](#series-lines)                 | ❌                                         | ✅                          | ✅              | ✅          | ✅                        | ❌              | ❌                    | ❌ (✅ if via another coord sys like [geo](#geo))               | ❌ (✅ if via another coord sys like [geo](#geo))               |
| [series-graph](#series-graph)                 | ✅ (create a “view” coord sys exclusively) | ✅                          | ✅              | ✅          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-sankey](#series-sankey)               | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-funnel](#series-funnel)               | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-gauge](#series-gauge)                 | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [series-pictorialBar](#series-pictorialBar)   | ❌                                         | ✅                          | ✅              | ❌          | ❌                        | ❌              | ❌                    | ❌ (✅ if via another coord sys like [grid](#grid))             | ❌ (✅ if via another coord sys like [grid](#grid))             |
| [series-themeRiver](#series-themeRiver)       | ❌                                         | ❌                          | ❌              | ❌          | ✅                        | ❌              | ❌                    | ❌ (✅ if via another coord sys like [singleAxis](#singleAxis)) | ❌ (✅ if via another coord sys like [singleAxis](#singleAxis)) |
| [series-chord](#series-chord)                 | ✅                                         | ✅                          | ✅              | ✅          | ✅                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [title](#title)                               | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [legend](#legend)                             | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [dataZoom](#dataZoom)                         | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [visualMap](#visualMap)                       | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [toolbox](#toolbox)                           | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [timeline](#timeline)                         | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |
| [thumbnail](#thumbnail)                       | ✅                                         | ❌                          | ❌              | ❌          | ❌                        | ❌              | ❌                    | ✅                                                              | ✅                                                              |

</div>

</div>
