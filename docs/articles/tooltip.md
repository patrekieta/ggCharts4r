<div id="main" role="main">

# Tooltip

<div class="section level2">

## Helper

Since version `0.2.1` you can also easily format the axis to decimal,
percentages or currencies thanks to contribution from [Artem
Klevtsov](https://github.com/artemklevtsov).

<div id="cb1" class="sourceCode">

``` r
cars |> 
  dplyr::mutate(
    dist = dist / 120
  ) |> 
  e_charts(speed) |> 
  e_scatter(dist, symbol_size = 10) |> 
  e_tooltip(
    formatter = e_tooltip_item_formatter("percent")
  )
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## JavaScript

*Thanks to [Sharon Machlis](https://github.com/smach) for helping put
this document together.*

You can display a default tooltip by adding `e_tooltip()` to the code
that creates your visualization, such as

<div id="cb2" class="sourceCode">

``` r
mtcars |>
  e_charts(wt) |>
  e_scatter(mpg, qsec) |>
  e_tooltip(trigger = "item")
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

Note that you can change the trigger to `axis`.

<div id="cb3" class="sourceCode">

``` r
mtcars |>
  e_charts(wt) |>
  e_line(mpg) |>
  e_line(qsec) |> 
  e_tooltip(trigger = "axis")
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

In order to *customize* the tooltip, you’ll need to be comfortable
adding a little JavaScript to your R code. Tooltip customization uses
the formatter.

<div id="cb4" class="sourceCode">

``` r
e_tooltip(
  formatter = htmlwidgets::JS("
    function(params){
      return();
    }
  ")
)
```

</div>

Where the specific information you’d like to appear goes within
return().

Here’s what you need to know about adding variables into that return()
code:

The x-axis variable is params.value\[0\]. The y-axis variable is
params.value\[1\]. If you added another, size variable to the scatter
plot, that would be params.value\[2\]. (Note that because this is
JavaScript, indexing starts with 0 as in most computer languages, and
not 1 as in R.)

Here’s how you might customize a tooltip for a scatter plot of mtcars wt
and mpg, in order to show both wt and mpg in the tooltip:

<div id="cb5" class="sourceCode">

``` r
mtcars |>
  e_charts(wt) |>
  e_scatter(mpg, qsec) |>
  e_tooltip(formatter = htmlwidgets::JS("
      function(params){
        return('wt: ' + params.value[0] + '<br />mpg: ' + params.value[1])
      }
    ")
  )
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

If you’d like to add information about a data frame column that’s not
included in the chart, you can pass in that data using the bind
argument. As an example, you might want to include the name of the car
model in the tooltip. With this particular data set, you’d first need to
create that column, which you can do with code such as
`mtcars <- tibble::rownames_to_column(mtcars, "model")`. Then, you can
pass that column into your scatter plot visualization with
`e_scatter(mpg, bind = model)`.

<div id="cb6" class="sourceCode">

``` r
mtcars |>  
  tibble::rownames_to_column("model") |> 
  e_charts(wt) |> 
  e_scatter(mpg, qsec, bind = model) |>
  e_tooltip(
    formatter = htmlwidgets::JS("
      function(params){
        return('<strong>' + params.name + 
                '</strong><br />wt: ' + params.value[0] + 
                '<br />mpg: ' + params.value[1]) 
                }
    ")
  )
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
