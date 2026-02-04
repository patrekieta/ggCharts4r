<div id="main" role="main">

# Get Started

Welcome to `echarts4r`, let’s explore the package together.

1.  All functions of the `echarts4r` package start with `e_`.
2.  All its [Shiny](https://shiny.rstudio.com/) proxies end with `_p`.
3.  All `echarts4r` plots are initialised with `e_charts`.
4.  All functions are `|>` friendly.
5.  Most functions have escape hatches ending in `_`.

<div class="section level2">

## Video & Article

Thanks to [Sharon Machlis](https://twitter.com/sharon000) there is an
amazing video and
[article](https://www.infoworld.com/article/3607068/plot-in-r-with-echarts4r.html)
introducing echarts4r.

</div>

<div class="section level2">

## Your first plot

Let’s build a line chart. First, we’ll prepare the data, load the
library and pipe the data to `e_charts`.

<div id="cb1" class="sourceCode">

``` r
# prepare data
df <- airquality

# pad month/day with leading zero and convert to date
df$Month <- sprintf("%02d", df$Month)
df$Day <- sprintf("%02d", df$Day)

df$Date <- paste("1973", df$Month, df$Day, sep = "-") |> 
  as.Date(format = "%Y-%m-%d")
```

</div>

<div id="cb2" class="sourceCode">

``` r
df |> 
  e_charts(x = Date) |> # initialise and set x
  e_line(serie = Temp) # add a line
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

If you wish to use column names as quoted strings you can use the escape
hatches with functions ending in `_`.

<div id="cb3" class="sourceCode">

``` r
df |> 
  e_charts_("Date") |> 
  e_line_("Temp")
```

</div>

The easiest way to build your charts is to use the `|>` pipe operator to
add plots, elements and options. Notice that the charts are interactable
without any specific code additions. Try expanding the average wind
speed view by clicking on *Temp* in the legend to disable the
temperature line.

<div id="cb4" class="sourceCode">

``` r
df |> 
  e_charts(Date) |> 
  e_line(Temp) |>  # add a line
  e_area(Wind) # add area
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Options

We could also change the lines to make them `smooth`.

<div id="cb5" class="sourceCode">

``` r
df |> 
  e_charts(Date) |> # initialise and set x
  e_line(Temp, smooth = TRUE) |>  # add a line
  e_area(Wind, smooth = TRUE) # add area
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Lets label the X axis with the convenience function `e_axis_labels`.

<div id="cb6" class="sourceCode">

``` r
df |> 
  e_charts(Date) |> # initialise and set x
  e_line(Temp, smooth = TRUE) |>  # add a line
  e_area(Wind, smooth = TRUE) |> # add area
  e_axis_labels(x = "1973.") # axis label
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

We can use one of the 13 built-in themes to style the chart, see
`?e_theme` for a complete list. We’ll also add a title with `e_title`.

<div id="cb7" class="sourceCode">

``` r
df |> 
  e_charts(Date) |> # initialise and set x
  e_line(Temp, smooth = TRUE) |>  # add a line
  e_area(Wind, smooth = TRUE) |> # add area
  e_axis_labels(x = "1973.") |> # axis label
  e_title("New York Air Quality Data", "Maximum daily temperature and mean wind speed") |>  # Add title & subtitle
  e_theme("infographic") # theme
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

The legend and title are a bit close, let’s move the legend to another
part the canvas.

<div id="cb8" class="sourceCode">

``` r
df |> 
  e_charts(Date) |> # initialise and set x
  e_line(Temp, smooth = TRUE) |>  # add a line
  e_area(Wind, smooth = TRUE) |> # add area
  e_axis_labels(x = "1973.") |> # axis label
  e_title("New York Air Quality Data", "Maximum daily temperature and mean wind speed") |>  # Add title & subtitle
  e_theme("infographic") |>  # theme
  e_legend(right = 0) # move legend to the top right corner
```

</div>

<div id="htmlwidget-10b3b7155e8045a1b2ad"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Add a tooltip, of which there are numerous
[options](https://echarts.apache.org/en/option.html#tooltip). Here, we
use `trigger = "axis"` to trigger the tooltip across the whole y axis
for a given day, rather than on individual data points.

<div id="cb9" class="sourceCode">

``` r
df |> 
  e_charts(Date) |> # initialise and set x
  e_line(Temp, smooth = TRUE) |>  # add a line
  e_area(Wind, smooth = TRUE) |> # add area
  e_axis_labels(x = "1973.") |> # axis label
  e_title("New York Air Quality Data", "Maximum daily temperature and mean wind speed") |>  # Add title & subtitle
  e_theme("infographic") |>  # theme
  e_legend(right = 0) |> # move legend to the top right corner
  e_tooltip(trigger = "axis") # tooltip
```

</div>

<div id="htmlwidget-4018eef1a407a0df6b52"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Finally, we are currently plotting temperature and wind speed on the
same axis, let’s put them each on their respective y axis by specifying
an extra axis for Wind.

Dual y axes are not considered good data visualisation practice, they
are only here for demonstration purposes.

<div id="cb10" class="sourceCode">

``` r
df |> 
  e_charts(Date) |> # initialise and set x
  e_line(Temp, smooth = TRUE) |>  # add a line
  e_area(Wind, smooth = TRUE, y_index = 1) |> # add area
  e_axis_labels(x = "1973.") |> # axis label
  e_title("New York Air Quality Data", "Maximum daily temperature and mean wind speed") |>  # Add title & subtitle
  e_theme("infographic") |>  # theme
  e_legend(right = 0) |> # move legend to the top right corner
  e_tooltip(trigger = "axis") # tooltip
```

</div>

<div id="htmlwidget-5b1b2f4ad92281566982"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Navigate options

`echarts4r` is highly customisable. There are too many options to have
them all hard-coded in the package but rest assured; they are available,
and can be passed to `...`. You will find all these options in the
[official documentation](https://echarts.apache.org/en/option.html).

[ Official Documentation](https://echarts.apache.org/en/option.html)

For instance the documentation for the tooltip looks like this:

[![](https://echarts4r.john-coene.com/articles/docs.png)](https://echarts.apache.org/en/option.html#tooltip)

Therefore if we want to change our tooltip to an
[axisPointer](https://echarts.apache.org/en/option.html#tooltip.axisPointer)
we can do so by passing a list to `axisPointer`.  
If an option takes a single value, we don’t need to wrap it in a list.
For example, we can try changing the tooltip
[backgroundColor](https://echarts.apache.org/en/option.html#tooltip.backgroundColor).

<div id="cb11" class="sourceCode">

``` r
df |> 
  e_charts(Date) |> # initialise and set x
  e_line(Temp, smooth = TRUE) |>  # add a line
  e_area(Wind, smooth = TRUE) |> # add area
  e_axis_labels(x = "1973.") |> # axis label
  e_title("New York Air Quality Data", "Maximum daily temperature and mean wind speed") |>  # Add title & subtitle
  e_theme("infographic") |>  # theme
  e_legend(right = 0) |> # move legend to the bottom
  e_tooltip(
    axisPointer = list(
      type = "cross"
    ),
    backgroundColor = "#FFFFFF" # hex code for white color
  ) 
```

</div>

<div id="htmlwidget-25c3e940e6859592f801"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Once you come to the realisation that JSON \~= `list` in R, it’s pretty
easy.

You’re caught up on the basics, go to the
[advanced](https://echarts4r.john-coene.com/articles/advanced.html)
section or navigate the site to discover how to add multiple linked
graphs, draw on globes, use the package in shiny, and more.

</div>

</div>
