<div id="main" role="main">

# Graphics

With `echarts4r` comes a small but powerful low level API to graphic
elements.

<div class="section level2">

## Functions

Graphic functions end in `_g`

-   `g_graphic_g` (initialisation)
-   `g_group_g`
-   `g_image_g`
-   `g_text_g`
-   `g_rect_g`
-   `g_circle_g`
-   `g_ring_g`
-   `g_sector_g`
-   `g_arc_g`
-   `g_polygon_g`
-   `g_polyline_g`
-   `g_line_g`
-   `g_bezier_curve_g`

</div>

<div class="section level2">

## Draft

The `e_draft` helper function is a very simple wrapper aroudn the
graphics API and thus a good example of what can be achieved.

<div id="cb1" class="sourceCode">

``` r
cars |> 
  e_charts(speed) |> 
  e_scatter(dist) |>
  e_draft()
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Image

You can add an image for instance.

<div id="cb2" class="sourceCode">

``` r
cars |> 
  e_charts(speed) |> 
  e_scatter(dist) |>
  e_image_g(
    right = 20,
    top = 20,
    z = -999,
    style = list(
      image = "https://www.r-project.org/logo/Rlogo.png",
      width = 150,
      height = 150,
      opacity = .6
    )
  )
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
