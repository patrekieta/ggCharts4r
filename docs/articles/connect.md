<div id="main" role="main">

# Arrange & Connect

<div class="section level2">

## Basics

Since version `0.1.2` you can connect multiple two charts together which
might make it even easier. Below we create two charts, with
`e_datazoom`, hiding one of the latter. On the second chart we run
`e_connect` to connect it with the other; sliders are now linked.

You can link charts together in two different ways, one with `e_connect`
by refering other charts’s id (`elementId`)

<div id="cb1" class="sourceCode">

``` r
e1 <- mtcars |> 
  e_charts(
    mpg,
    height = 200,
    elementId = "chart1" # specify id
  ) |> 
  e_scatter(wt) |> 
  e_datazoom(show = FALSE) # hide

e2 <- mtcars |> 
  e_charts(
    wt,
    height = 200,
    elementId = "chart2" # specify id
  ) |> 
  e_scatter(qsec) |> 
  e_datazoom(show = FALSE) # hide
  
e3 <- mtcars |> 
  e_charts(
    qsec,
    height = 200
  ) |> 
  e_scatter(hp) |> 
  e_datazoom() |> 
  e_connect(c("chart1", "chart2")) # connect
```

</div>

You can browse the above from your console like so.

<div id="cb2" class="sourceCode">

``` r
e_arrange(e1, e2, e3)
```

</div>

<div class="row">

<div class="col-xs-12">

<div id="chart1" class="echarts4r html-widget"
style="width:100%;height:200px;">

</div>

</div>

</div>

<div class="row">

<div class="col-xs-12">

<div id="chart2" class="echarts4r html-widget"
style="width:100%;height:200px;">

</div>

</div>

</div>

<div class="row">

<div class="col-xs-12">

<div id="htmlwidget-ac96cb3ee4656e2e9ec3" class="echarts4r html-widget"
style="width:100%;height:200px;">

</div>

</div>

</div>

The package natively links interactions, therefore, in the following the
legend is acutally unique, one legend will trigger on both charts
because they bear the same name.

<div id="cb3" class="sourceCode">

``` r
create_chart <- function(data, var){
  data |> 
    e_charts_(
        "mpg",
        height = 200
    ) |> 
    e_scatter_(var, name = "Click me!") |> 
    e_group("4charts") # all charts in the same group
}
e4 <- create_chart(mtcars, "hp")
e5 <- create_chart(mtcars, "wt")
e6 <- create_chart(mtcars, "drat")
e7 <- create_chart(mtcars, "qsec") |> 
  e_connect_group("4charts") # connect charts

e_arrange(e4, e5, e6, e7, rows = 2, cols = 2)
```

</div>

<div class="row">

<div class="col-xs-6">

<div id="htmlwidget-e5c8c404fe174e4c81bd" class="echarts4r html-widget"
style="width:100%;height:200px;">

</div>

</div>

<div class="col-xs-6">

<div id="htmlwidget-36aa3d2a04d42bbc2145" class="echarts4r html-widget"
style="width:100%;height:200px;">

</div>

</div>

</div>

<div class="row">

<div class="col-xs-6">

<div id="htmlwidget-febe03efa1a2d8d52a86" class="echarts4r html-widget"
style="width:100%;height:200px;">

</div>

</div>

<div class="col-xs-6">

<div id="htmlwidget-1fb4450895fe099f74a1" class="echarts4r html-widget"
style="width:100%;height:200px;">

</div>

</div>

</div>

You can connect pretty much anything, including geospatial
visualisations, it’ll work as long as they share one or more thing in
common (i.e.: serie `name`).

<div id="cb4" class="sourceCode">

``` r
library(echarts4r.maps)

USArrests$state <- row.names(USArrests)

e8 <- USArrests |> 
  e_charts(state, elementId = "US") |>
  em_map("USA") |> 
  e_map_3d(Murder, map = "USA", name = "Murder", boxWidth = 70) |> 
  e_visual_map(Murder)

# this is made up
UK <- data.frame(
  kingdoms = c("England", "Wales", "Nothern Ireland", "Scotland"),
  murder = c(.8, 5, 13.2, 17.4)
)

e9 <- UK |> 
  e_charts(kingdoms) |>
  em_map("United_Kingdom") |> 
  e_map_3d(murder, map = "United_Kingdom", name = "Murder", boxWidth = 50) |> 
  e_visual_map(murder, show = FALSE) |> 
  e_connect("US")

e_arrange(e8, e9, cols = 2, rows = 1)
```

</div>

<div class="row">

<div class="col-xs-6">

<div id="US" class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="col-xs-6">

<div id="htmlwidget-10b3b7155e8045a1b2ad"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>

On the geo-spatial visualisations above you can slide the visual map to
filter states/kingdoms (because `e_visual_map` defaults to
`calculable = TRUE`).

</div>

<div class="section level2">

## Shiny

There is no need for `e_arrange` in Shiny, though `e_connect` and
`e_arrange` work hand in hand you can use one without the other. In fact
you don’t truly have to use `e_arrange` in R markdown either.

Once the charts are connected they don’t need to be side by side.

<div id="cb5" class="sourceCode">

``` r
library(shiny)
library(echarts4r)

ui <- fluidPage(
  fluidRow(
  column(5, echarts4rOutput("plot1")),
  column(2, "Charts are connected, no need for", code("e_arrange")),
  column(5, echarts4rOutput("plot2"))
  )
)

server <- function(input, output, session) {
  
  output$plot1 <- renderEcharts4r({
    cars |> 
      e_charts(
        speed,
        height = 200
      ) |> 
      e_scatter(dist, name = "legend") |> 
      e_datazoom(show = FALSE, y_index = 0) |> 
      e_group("grp")
  })
  
  output$plot2 <- renderEcharts4r({
    cars |> 
      e_charts(
        dist,
        height = 200
      ) |> 
      e_scatter(speed, name = "legend") |> 
      e_datazoom(y_index = 0) |> 
      e_group("grp") |>  # assign group
      e_connect_group("grp")
  })
  
}

shinyApp(ui, server)
```

</div>

</div>

</div>
