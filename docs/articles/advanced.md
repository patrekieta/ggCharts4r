<div id="main" role="main">

# Advanced

This document details some more advanced usage of the `echarts4r`
package.

<div class="section level2">

## Common options

You can set two common options with `e_common`:

-   Font family
-   [Theme](http://echarts4r.john-coene.com/articles/articles/themes.md)

<div id="cb1" class="sourceCode">

``` r
e_common(
  font_family = "Raleway",
  theme = NULL
)
```

</div>

All charts on this page will use the `Raleway` font (sourced in CSS from
Google fonts).

</div>

<div class="section level2">

## Grouping

The package also understands `dplyr::group_by` in order to avoid having
to add many layers manually one by one. `echarts4r` essentially will
plot one serie for each group.

<div id="cb2" class="sourceCode">

``` r
iris |> 
  group_by(Species) |> 
  e_charts(Sepal.Length) |> 
  e_line(Sepal.Width) |> 
  e_title("Grouped data")
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

The above plot one line (`e_line`) for each group (`group_by`). *At one
exception*, since `0.2.1`, when `timeline` is set to `TRUE` when the
chart is initialised with `e_charts`. In the latter case each group is
used as a step of the timeline.

<div id="cb3" class="sourceCode">

``` r
iris |> 
  group_by(Species) |> 
  e_charts(Sepal.Length, timeline = TRUE) |> 
  e_line(Sepal.Width) |> 
  e_title("Timeline")
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Stacked

<div id="cb4" class="sourceCode">

``` r
df <- data.frame(
  x = LETTERS[1:10],
  a = runif(10),
  b = runif(10),
  c = runif(10),
  d = runif(10)
)

df |> 
  e_charts(x) |> 
  e_bar(a, stack = "grp") |> 
  e_bar(b, stack = "grp") |> 
  e_bar(c, stack = "grp2") |> 
  e_bar(d, stack = "grp2") 
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Scatter

Since `0.2.0` the `e_scatter` and `e_effect_scatter` functions take a
different, much improved `scale` argument which is a scaling function.

<div id="cb5" class="sourceCode">

``` r
iris |> 
    group_by(Species) |> 
    e_charts(Sepal.Length) |> 
    e_scatter(Petal.Length, Sepal.Width)
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

The default scaling function is `e_scale` which rescales from 1 to 20,
but you can pass your own. The scaling function should take a vector of
`integer` or `numeric` and return a similar vector of the same length.
For instance, to create a function that rescales from 5 to 30:

<div id="cb6" class="sourceCode">

``` r
my_scale <- function(x){
  scales::rescale(x, to = c(5, 30))
}

iris |> 
    group_by(Species) |> 
    e_charts(Sepal.Length) |> 
    e_scatter(Petal.Length, Sepal.Width, scale = my_scale)
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

This also works with R 4.1.0 syntax.

<div id="cb7" class="sourceCode">

``` r
iris |>  
    group_by(Species) |> 
    e_charts(Sepal.Length) |> 
    e_scatter(
      Petal.Length, 
      Sepal.Width, 
      scale = \(x) scales::rescale(x, to = c(5, 30))
    )
```

</div>

When `size` is not passed the size of the points are defined by
`symbol_size`.

<div id="cb8" class="sourceCode">

``` r
iris |> 
    group_by(Species) |> 
    e_charts(Sepal.Length) |> 
    e_scatter(Petal.Length, symbol_size = 15)
```

</div>

<div id="htmlwidget-10b3b7155e8045a1b2ad"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

When `size` is passed `symbol_size` becomes a multiplier executed after
the scaling function is run. For instance log (1+*x*) \* 5

<div id="cb9" class="sourceCode">

``` r
iris |> 
    group_by(Species) |> 
    e_charts(Sepal.Length) |> 
    e_scatter(Petal.Length, Sepal.Width, scale = log1p, symbol_size = 10)
```

</div>

<div id="htmlwidget-4018eef1a407a0df6b52"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

This behaviour was added as it is important to be able to scale points
within a reasonable range, ideally points are between 1 and 30\~40 in
size.

Note that rescaling the color means you should also rescale the
`e_visual_map`, if used.

<div id="cb10" class="sourceCode">

``` r
echart <- mtcars |> 
  e_charts(mpg) |> 
  e_scatter(qsec, wt, scale = e_scale) |> 
  e_legend(show = FALSE)

echart |> 
  e_visual_map(wt, scale = e_scale)
```

</div>

<div id="htmlwidget-5b1b2f4ad92281566982"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

<div id="cb11" class="sourceCode">

``` r
# or 
# echart |> 
#   e_visual_map(min = 1, max = 20)
```

</div>

If you want to keep the original size then you can use `scale_js`,
because you might want the `e_visual_map` to remain true to the original
data.

<div id="cb12" class="sourceCode">

``` r
mtcars |> 
  e_charts(mpg) |> 
  e_scatter(qsec, wt, scale = NULL, scale_js = "function(data){ return data[3] * 3;}") |> 
  e_legend(show = FALSE) |> 
  e_visual_map(wt, scale = NULL)
```

</div>

<div id="htmlwidget-25c3e940e6859592f801"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

This way the bubbles are of an appropriate size but the the range of the
visual map remains true.

</div>

<div class="section level2">

## Jitter

Since version `0.2.1` you can jitter points with `e_scatter`.

<div id="cb13" class="sourceCode">

``` r
mtcars |> 
  e_charts(cyl) |> 
  e_scatter(drat, symbol_size = 4) |> 
  e_scatter(
    drat, jitter_factor = 2, symbol_size = 6,
    name = "noisy"
  )
```

</div>

<div id="htmlwidget-3f27c09be0c60bb52829"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## coord_system

Chart types are not only applicable to the standard 2D cartesian
coordinate system, though most charts will default to the `cartesian2d`
coordinate system, they may be applied to others.

Let’s look at the heatmap. First a regular heatmap.

<div id="cb14" class="sourceCode">

``` r
v <- LETTERS[1:10]
matrix <- data.frame(
  x = sample(v, 300, replace = TRUE), 
  y = sample(v, 300, replace = TRUE), 
  z = rnorm(300, 10, 1),
  stringsAsFactors = FALSE
) |> 
  dplyr::group_by(x, y) |> 
  dplyr::summarise(z = sum(z)) |> 
  dplyr::ungroup()
#> `summarise()` has grouped output by 'x'. You can override using the `.groups`
#> argument.

matrix |> 
  e_charts(x) |> 
  e_heatmap(y, z) |> 
  e_visual_map(z)
```

</div>

<div id="htmlwidget-416566eb193bf50d04e6"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

One could also plot the heatmap on different coordinates, such as a
calendar by first adding a calendar with `e_calendar` then specifying
`coord_system = "calendar"`.

<div id="cb15" class="sourceCode">

``` r
dates <- seq.Date(as.Date("2018-01-01"), as.Date("2018-12-31"), by = "day")
values <- rnorm(length(dates), 20, 6)

year <- data.frame(date = dates, values = values)

year |> 
  e_charts(date) |> 
  e_calendar(range = "2018") |> 
  e_heatmap(values, coord_system = "calendar") |> 
  e_visual_map(max = 30)
```

</div>

<div id="htmlwidget-72cbf064100ce560a04c"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Another example, using polar coordinates, plot a line on 2D cartesian
coordinates, then change to polar.

<div id="cb16" class="sourceCode">

``` r
df <- data.frame(x = 1:10, y = seq(1, 20, by = 2))

df |> 
  e_charts(x) |> 
  e_line(y) 
```

</div>

<div id="htmlwidget-d11fc4360aa0230696d7"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

<div id="cb17" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_polar() |> 
  e_angle_axis() |> 
  e_radius_axis() |> 
  e_line(y, coord_system = "polar", smooth = TRUE) 
```

</div>

<div id="htmlwidget-21c7483268bafca56cec"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

There are numerous coordinate system available in `echarts4r`; `globe`,
`cartesian3d` and `polar` **to name a few.** Note that when there are
more than one `coord_system` available the latter are documented with
examples in their respective function’s `man` page.

</div>

<div class="section level2">

## Customise the Axis

Use multiple axis, by speecifying the index of the axis. *Note that
JavaScript starts from 0 not 1, so `y_index = 1` is the second axis,
`y_index = 0` is the first axis (default)*

<div id="cb18" class="sourceCode">

``` r
USArrests |> 
  e_charts(Assault) |> 
  e_line(Murder, smooth = TRUE) |> 
  e_line(Rape, y_index = 1) |>  # add secondary axis
  e_y_axis(splitLine = list(show = FALSE)) # hide split lines on first Y axis
```

</div>

<div id="htmlwidget-1834a22cd196f3aa03a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Flip coordinates

You can flip coordinates with `e_flip_coords`, note that it will not
work if you have multiple y axis.

<div id="cb19" class="sourceCode">

``` r
data.frame(
  x = LETTERS[1:5],
  y = runif(5, 1, 15)
) |> 
  e_charts(x) |> 
  e_bar(y, name = "flipped") |> 
  e_flip_coords() # flip axis
```

</div>

<div id="htmlwidget-28515d92cb327f90c9eb"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Mark Points and Lines

Highlight points and lines on your plot with the `e_mark` family of
functions.

<div id="cb20" class="sourceCode">

``` r
USArrests |> 
  tibble::rownames_to_column("State") |> 
  dplyr::mutate(
    Rape = -Rape
  ) |> 
  e_charts(State) |> 
  e_area(Murder) |>
  e_bar(Rape, name = "Sick basterd", x_index = 1) |> # second y axis 
  e_mark_line("Sick basterd", data = list(type = "average")) |> 
  e_mark_point("Murder", data = list(type = "min"))
```

</div>

<div id="htmlwidget-0caf26d4e3c00206b0c5"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Look for arguments

Look for more arguments, with `echarts4r` you are often only one
argument away from from what you want.

<div id="cb21" class="sourceCode">

``` r
library(dplyr)
#> Warning: package 'dplyr' was built under R version 4.5.2
#> 
#> Attaching package: 'dplyr'
#> The following objects are masked from 'package:stats':
#> 
#>     filter, lag
#> The following objects are masked from 'package:base':
#> 
#>     intersect, setdiff, setequal, union
df <- tibble(
  name = "earth",        # 1st level
  children = list(
    tibble(name = c("land", "ocean"),             # 2nd level
       children = list(
         tibble(name = c("forest", "river")),   # 3rd level 
         tibble(name = c("fish", "kelp"),
            children = list(
               tibble(name = c("shark", "tuna"),  # 4th level 
               NULL  # kelp
            ))
         )
       ))
  )
)

df |> 
  e_charts() |> 
  e_tree()
```

</div>

<div id="htmlwidget-da0b268a2927f570ebf3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

to radial:

<div id="cb22" class="sourceCode">

``` r
df |> 
  e_charts() |> 
  e_tree(layout = "radial")
```

</div>

<div id="htmlwidget-0ed12bb554391c49c2e3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Show labels

You can, for most series show labels like so:

<div id="cb23" class="sourceCode">

``` r
USArrests |> 
  tibble::rownames_to_column("State") |> 
  dplyr::slice(1:10) |> 
  e_charts(State) |> 
  e_area(Murder, label = list(normal = list(show = TRUE))) 
```

</div>

There is also a helper function that provides an easier API

<div id="cb24" class="sourceCode">

``` r
USArrests |> 
  tibble::rownames_to_column("State") |> 
  dplyr::slice(1:10) |> 
  e_charts(State) |> 
  e_area(Murder) |> 
  e_labels()
```

</div>

<div id="htmlwidget-ec658d41f8c4f2d124e9"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Nested data

You might observe in the official documentation that some series can
take more *data* points than just x and y points, like
[e_bar](https://echarts.apache.org/en/option.html#series-line.data); In
the [official documentation](https://echarts.apache.org/en/option.html)
go to “serie”, select the one you are interested in (i.e.: bar) then
select “data”.

`e_bar` lets you pass `serie` (from your initial data.frame) which
corresponds to `value` in the [original
library](https://echarts.apache.org/en/option.html#series-bar.data).
However the latter also takes, `label`, `itemStyle`, and `tooltip` but
being JSON arrays they translate to lists in R and dealing with nested
data.frames is not ideal. `e_add_nested` remedies to that. It allows
adding those nested data points.

Let’s add some columns to the `iris` dataset which we will use in
`e_add_nested` to customize the appearance of the
[`label`](https://echarts.apache.org/en/option.html#series-bar.data.label).

<div id="cb25" class="sourceCode">

``` r
# add columns to iris
iris_dat <- iris |> 
  dplyr::mutate(
    show = TRUE, # to show the labels
    fontSize = exp(Sepal.Length) / 10, # font size will correspond to Sepal.Length
    color = sample(c("red", "black", "blue"), dplyr::n(), replace = TRUE) # assign a random color to the label
  )

iris_dat |> 
  dplyr::slice(1:10) |> # simplify the graph. 
  e_charts(Sepal.Width) |> 
  e_line(Sepal.Length) |> 
  e_add_nested("label", show, fontSize, color) |> # add our columns to "label"
  e_x_axis(min = 2.5)
```

</div>

<div id="htmlwidget-6b83523733b890d61edc"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Another example with `e_funnel`.

<div id="cb26" class="sourceCode">

``` r
funnel <- data.frame(
  stage = c("View", "Click", "Purchase"), 
  value = c(80, 30, 20),
  color = c("blue", "red", "green")
)

funnel |> 
  e_charts() |> 
  e_funnel(value, stage) |> 
  e_add_nested("itemStyle", color)
```

</div>

<div id="htmlwidget-b3f7c917b6c8ff580948"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## List

Since version `0.2.1` you can pass a raw list of options.

<div id="cb27" class="sourceCode">

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
```

</div>

<div id="htmlwidget-d258b2ee1c304ebe1664"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

`e_list` can also be used to append options.

</div>

</div>
