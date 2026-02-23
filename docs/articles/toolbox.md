<div id="main" role="main">

# Toolbox

The toolbox allows you to add neat little interactive functions to your
plots.

<div class="section level2">

## Features

-   saveAsImage
-   brush
-   restore
-   dataView
-   dataZoom
-   magicType

</div>

<div class="section level2">

## Save plot

<div id="cb1" class="sourceCode">

``` r
echart <- mtcars |> 
  e_charts(qsec) |> 
  e_line(mpg, smooth = TRUE)

echart |> e_toolbox_feature(feature = "saveAsImage") # hit the download button!
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## data Zoom

<div id="cb2" class="sourceCode">

``` r
echart |> e_toolbox_feature(feature = "dataZoom")
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## data view

<div id="cb3" class="sourceCode">

``` r
echart |> e_toolbox_feature(feature = "dataView")
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

See the [official
documentation](https://echarts.apache.org/en/option.html#toolbox.feature)
for the full list.

</div>

</div>
