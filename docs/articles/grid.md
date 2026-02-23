<div id="main" role="main">

# Grid & Axis

`echarts4r` comes with a highly customisable grid and axis, but
admittedly they take some getting used to.

<div class="section level2">

## Axis helper

You can customise the axis with `e_axis`, `e_x_axis` or `e_y_axis`, you
can see the [official
documentation](https://echarts.apache.org/en/option.html#xAxis) for more
details. There is also a helper function, `e_format_axis` and its
sisters `e_format_x_axis` and `e_format_y_axis`. The latter lets you
easily add suffix or prefix to your axis labels.

Say you want to plot against ceslius.

<div id="cb1" class="sourceCode">

``` r
df <- data.frame(
  x = 1:20, # celsius
  y = runif(20, 1, 100) # percentages
)

df |> 
  e_charts(x) |> 
  e_line(y) |> 
  e_format_x_axis(suffix = "°C") |> 
  e_legend(FALSE)
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Since version `0.2.1` you can also easily format the axis to decimal,
percentages or currencies thanks to contribution from [Artem
Klevtsov](https://github.com/artemklevtsov).

<div id="cb2" class="sourceCode">

``` r
df |> 
  dplyr::mutate(y = y / 100) |> 
  e_charts(x) |> 
  e_line(y, legend = FALSE) |> 
  e_x_axis(
    formatter = e_axis_formatter("currency", currency = "GBP")
  ) |> 
  e_y_axis(
    formatter = e_axis_formatter("decimal", digits = 3)
  )
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Grid

You can also customise the grid to have, for instance, multiple plots on
one canvas.

Let’s initialise a basic plot.

<div id="cb3" class="sourceCode">

``` r
df <- data.frame(
  x = 1:20, 
  w = runif(20, 1, 100),
  z = runif(20, 25, 75)
)

df |> 
  e_charts(x) |> 
  e_line(w) |> 
  e_line(z)
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Now say we don’t want `w` and `z` on the same plot. We could of course
make two entirely different plots (2 plots initialised with
`e_charts()`), but it would be cleaner to have them on the same canvas,
a bit like [ggplot2
facets](http://ggplot2.tidyverse.org/reference/facet_grid.md).

First two plots on the same canvas means multiple axis, so we’ll plot
each serie on its own axis.

`echarts4r` is an R API to a JavaScript library, so arrays start at one;
`x` and `y` indices default to 0 so we only need to change one of the
series’ indices to 1. Therefore one serie is plotted on index 0 and the
other on index 1 for two `x`and `y` axis.

<div id="cb4" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_line(w) |> 
  e_line(z, x_index = 1, y_index = 1)
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Notice how `echarts4r` puts the additional axis on the top and right of
the plot. This is a useful feature but not what we want; we’re missing a
split grid.

We use `e_grid` twice for two grids, we define the height of each; `35%`
is ideal for stacked grids, you need some margin for the legend, the
axis, etc. hence not using `50%`.

<div id="cb5" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_line(w) |> 
  e_line(z, x_index = 1, y_index = 1) |> 
  e_grid(height = "35%") |> # two grids of 35% height
  e_grid(height = "35%", top = "50%") # this grid is 50% from the top
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

However, we still have both line plots on the same grid. Here is how to
think about grids and axis in `echarts4r`.

1.  Your series (i.e.: `e_line`) are plotted against axis (`e_axis`)
2.  These axis are plotted in grids `e_grid`

So we have two grids and two axis but the axis are both plotted on the
same grid(point \#2 above). So we need to move our two additional axis
to another grid. Note that grid indices also start at 0 here.

<div id="cb6" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_line(w) |> 
  e_line(z, x_index = 1, y_index = 1) |> 
  e_grid(height = "35%") |> 
  e_grid(height = "35%", top = "50%") |> 
  e_y_axis(gridIndex = 1) |> # put x and y on grid index 1
  e_x_axis(gridIndex = 1)
```

</div>

<div id="htmlwidget-10b3b7155e8045a1b2ad"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

There you go!

You can also have a different grid to put the plots side by side.

<div id="cb7" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_line(w) |> 
  e_line(z, x_index = 1, y_index = 1) |> 
  e_grid(width = "35%") |> 
  e_grid(width = "35%", left = "55%") |> 
  e_y_axis(gridIndex = 1) |> # put x and y on grid index 1
  e_x_axis(gridIndex = 1)
```

</div>

<div id="htmlwidget-4018eef1a407a0df6b52"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Why bother?

Well now those charts can share interactions.

<div id="cb8" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_line(w) |> 
  e_line(z, x_index = 1, y_index = 1) |> 
  e_grid(height = "35%") |> 
  e_grid(height = "35%", top = "50%") |> 
  e_y_axis(gridIndex = 1) |> 
  e_x_axis(gridIndex = 1) |> 
  e_tooltip(trigger = "axis") |> 
  e_datazoom(x_index = c(0, 1)) # add data zoom for for x axis
```

</div>

<div id="htmlwidget-5b1b2f4ad92281566982"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Axis

You can also mess with the axis to completely change your chart. For
instance, from a regular bar chart:

<div id="cb9" class="sourceCode">

``` r
df <- data.frame(
  x = LETTERS[1:10], 
  y = seq(1, 20, by = 2),
  z = runif(10, 5, 20)
)

df |> 
  e_charts(x) |> 
  e_bar(y)
```

</div>

<div id="htmlwidget-25c3e940e6859592f801"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

to a polar chart.

<div id="cb10" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_polar() |> 
  e_angle_axis(x) |> # angle = x
  e_radius_axis() |> 
  e_bar(y, coord_system = "polar")
```

</div>

<div id="htmlwidget-3f27c09be0c60bb52829"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

or a radial chart one.

<div id="cb11" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_polar() |> 
  e_angle_axis() |> 
  e_radius_axis(x) |> # radius = x 
  e_bar(y, coord_system = "polar")
```

</div>

<div id="htmlwidget-416566eb193bf50d04e6"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

This will also work with other chart types.

<div id="cb12" class="sourceCode">

``` r
df |> 
  e_charts(x) |> 
  e_polar() |> 
  e_angle_axis() |> 
  e_radius_axis(x) |> 
  e_line(y, coord_system = "polar") |> 
  e_scatter(z, coord_system = "polar")
```

</div>

<div id="htmlwidget-72cbf064100ce560a04c"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
