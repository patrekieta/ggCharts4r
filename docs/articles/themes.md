<div id="main" role="main">

# Themes

You can easily customise the appearance of your chart using one of the
13 themes provided, or even build you own theme: use the online [theme
builder](https://echarts.apache.org/en/theme-builder.html) to create
your own.

<div class="section level2">

## default

<div id="cb1" class="sourceCode">

``` r
p <- USArrests |> 
  tibble::rownames_to_column("State") |> 
  dplyr::mutate(Rape = -Rape) |> 
  e_charts(State) |> 
  e_line(Murder) |> 
  e_area(Rape, name = "Sick basterd", x_index = 1) |>  # second y axis
  e_title("Your plot", "Subtext", sublink = "https://john-coene.com") |> 
  e_x_axis(index = 1, show = FALSE) |> # hide second X Axis
  e_tooltip(trigger = "axis")

p # default plot
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## dark

<div id="cb2" class="sourceCode">

``` r
p |> e_theme("dark")
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## vintage

<div id="cb3" class="sourceCode">

``` r
p |> e_theme("vintage")
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## westeros

<div id="cb4" class="sourceCode">

``` r
p |> e_theme("westeros")
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## essos

<div id="cb5" class="sourceCode">

``` r
p |> e_theme("essos")
```

</div>

<div id="htmlwidget-1fb4450895fe099f74a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## wonderland

<div id="cb6" class="sourceCode">

``` r
p |> e_theme("wonderland")
```

</div>

<div id="htmlwidget-10b3b7155e8045a1b2ad"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## walden

<div id="cb7" class="sourceCode">

``` r
p |> e_theme("walden")
```

</div>

<div id="htmlwidget-4018eef1a407a0df6b52"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## chalk

<div id="cb8" class="sourceCode">

``` r
p |> e_theme("chalk")
```

</div>

<div id="htmlwidget-5b1b2f4ad92281566982"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## infographic

<div id="cb9" class="sourceCode">

``` r
p |> e_theme("infographic")
```

</div>

<div id="htmlwidget-25c3e940e6859592f801"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## macarons

<div id="cb10" class="sourceCode">

``` r
p |> e_theme("macarons")
```

</div>

<div id="htmlwidget-3f27c09be0c60bb52829"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## roma

<div id="cb11" class="sourceCode">

``` r
p |> e_theme("roma")
```

</div>

<div id="htmlwidget-416566eb193bf50d04e6"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## shine

<div id="cb12" class="sourceCode">

``` r
p |> e_theme("shine")
```

</div>

<div id="htmlwidget-72cbf064100ce560a04c"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## purple-passion

<div id="cb13" class="sourceCode">

``` r
p |> e_theme("purple-passion")
```

</div>

<div id="htmlwidget-d11fc4360aa0230696d7"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## halloween

<div id="cb14" class="sourceCode">

``` r
p |> e_theme("halloween")
```

</div>

<div id="htmlwidget-21c7483268bafca56cec"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## azul

<div id="cb15" class="sourceCode">

``` r
p |> e_theme("azul")
```

</div>

<div id="htmlwidget-1834a22cd196f3aa03a1"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## blue

<div id="cb16" class="sourceCode">

``` r
p |> e_theme("blue")
```

</div>

<div id="htmlwidget-28515d92cb327f90c9eb"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## caravan

<div id="cb17" class="sourceCode">

``` r
p |> e_theme("caravan")
```

</div>

<div id="htmlwidget-0caf26d4e3c00206b0c5"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## carp

<div id="cb18" class="sourceCode">

``` r
p |> e_theme("carp")
```

</div>

<div id="htmlwidget-da0b268a2927f570ebf3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## cool

<div id="cb19" class="sourceCode">

``` r
p |> e_theme("cool")
```

</div>

<div id="htmlwidget-0ed12bb554391c49c2e3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## dark-blue

<div id="cb20" class="sourceCode">

``` r
p |> e_theme("dark-blue")
```

</div>

<div id="htmlwidget-ec658d41f8c4f2d124e9"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## dark-bold

<div id="cb21" class="sourceCode">

``` r
p |> e_theme("dark-bold")
```

</div>

<div id="htmlwidget-6b83523733b890d61edc"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## dark-digerati

<div id="cb22" class="sourceCode">

``` r
p |> e_theme("dark-digerati")
```

</div>

<div id="htmlwidget-b3f7c917b6c8ff580948"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## dark-fresh-cut

<div id="cb23" class="sourceCode">

``` r
p |> e_theme("dark-fresh-cut")
```

</div>

<div id="htmlwidget-d258b2ee1c304ebe1664"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## dark-mushroom

<div id="cb24" class="sourceCode">

``` r
p |> e_theme("dark-mushroom")
```

</div>

<div id="htmlwidget-b8f31ebacaee3527bb86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## forest

<div id="cb25" class="sourceCode">

``` r
p |> e_theme("forest")
```

</div>

<div id="htmlwidget-b25b670b028f478bf741"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## fresh-cut

<div id="cb26" class="sourceCode">

``` r
p |> e_theme("fresh-cut")
```

</div>

<div id="htmlwidget-46d1193f7ba074d981c8"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## fruit

<div id="cb27" class="sourceCode">

``` r
p |> e_theme("fruit")
```

</div>

<div id="htmlwidget-382a200f56fb8e6a1fd3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## gray

<div id="cb28" class="sourceCode">

``` r
p |> e_theme("gray")
```

</div>

<div id="htmlwidget-da403bf8187c892ade73"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## green

<div id="cb29" class="sourceCode">

``` r
p |> e_theme("green")
```

</div>

<div id="htmlwidget-756e3bf13eb93ebd21f9"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## helianthus

<div id="cb30" class="sourceCode">

``` r
p |> e_theme("helianthus")
```

</div>

<div id="htmlwidget-2931a41253ddcd61f464"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## inspired

<div id="cb31" class="sourceCode">

``` r
p |> e_theme("inspired")
```

</div>

<div id="htmlwidget-853270d7a7ddd5c78dff"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## london

<div id="cb32" class="sourceCode">

``` r
p |> e_theme("london")
```

</div>

<div id="htmlwidget-4211ee8e5b9f7bea17a6"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## macarons

<div id="cb33" class="sourceCode">

``` r
p |> e_theme("macarons")
```

</div>

<div id="htmlwidget-59344719eea48f3263a0"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## macarons2

<div id="cb34" class="sourceCode">

``` r
p |> e_theme("macarons2")
```

</div>

<div id="htmlwidget-1c18eca156cc321e99f7"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## mint

<div id="cb35" class="sourceCode">

``` r
p |> e_theme("mint")
```

</div>

<div id="htmlwidget-82903e20e82fe9e96ad4"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## red

<div id="cb36" class="sourceCode">

``` r
p |> e_theme("red")
```

</div>

<div id="htmlwidget-91e95a97e1d3447d8bab"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## red-velvet

<div id="cb37" class="sourceCode">

``` r
p |> e_theme("red-velvet")
```

</div>

<div id="htmlwidget-16ec33930352bd7ed495"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## royal

<div id="cb38" class="sourceCode">

``` r
p |> e_theme("royal")
```

</div>

<div id="htmlwidget-14ef52fbad8d1b5398fd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## sakura

<div id="cb39" class="sourceCode">

``` r
p |> e_theme("sakura")
```

</div>

<div id="htmlwidget-94457e0686f905840b07"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## tech-blue

<div id="cb40" class="sourceCode">

``` r
p |> e_theme("tech-blue")
```

</div>

<div id="htmlwidget-8a1f8f4a61c98a07d1d5"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## custom

<div id="cb41" class="sourceCode">

``` r
p |> e_theme_custom('{"color":["#ff715e","#ffaf51"]}')
```

</div>

<div id="htmlwidget-75d0c44ec49b8be5d81c"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

The above is an admittedly small theme, if you want to create a large
custom theme, download the JSON from the [theme
builder](https://echarts.apache.org/en/theme-builder.html) and use it,
`e_theme_custom` and `e_register_theme` both detect the json file and
read it in.

<div class="row">

<div class="col col-md-6">

<div id="cb42" class="sourceCode">

``` json
// theme.json
{
  "color":["#ff715e","#ffaf51"],
  "backgroundColor": "black"
}
```

</div>

</div>

<div class="col col-md-6">

<div id="cb43" class="sourceCode">

``` r
# in R
p |> e_theme_custom("theme.json")
```

</div>

</div>

</div>

The method above, however, registers the theme every time the chart is
drawn, if displaying multiple charts this can leads to large html files
or slower Shiny application. There is thus also the function
`e_theme_register` to register the custom theme once, and subsequently
use it.

<div id="cb44" class="sourceCode">

``` r
library(shiny)
library(echarts4r)

ui <- fluidPage(
  e_theme_register('{"color":["#ff715e","#ffaf51"]}', name = "myTheme"),
  echarts4rOutput("chart1"),
  echarts4rOutput("chart2")
)

server <- function(input, output){
  e <- e_charts(cars, speed) |> 
      e_scatter(dist) 

  output$chart1 <- renderEcharts4r({
    e_theme(e, "myTheme")
  })

  output$chart2 <- renderEcharts4r({
    e_theme(e, "myTheme")
  })

}

shinyApp(ui, server)
```

</div>

Note that the custom theme registered as above works with `e_common`,
e.g.: `e_common(theme = "myTheme")`.

</div>

</div>
