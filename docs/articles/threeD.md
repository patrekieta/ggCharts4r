<div id="main" role="main">

# 3D

<div class="section level2">

## Surface

<div id="cb1" class="sourceCode">

``` r
data <- expand.grid(
  x = seq(-3, 3, by = 0.05),
  y = seq(-3, 3, by = 0.05)
) |> 
  dplyr::mutate(z = sin(x * x + y * y) * x / 3.14)

data |> 
  e_charts(x) |> 
  e_surface(y, z, wireframe = list(show = FALSE)) |> 
  e_visual_map(z)
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Bar 3D

<div id="cb2" class="sourceCode">

``` r
v <- LETTERS[1:10]
matrix <- data.frame(
  x = sample(v, 300, replace = TRUE), 
  y = sample(v, 300, replace = TRUE), 
  z1 = rnorm(300, 10, 1),
  z2 = rnorm(300, 10, 1),
  stringsAsFactors = FALSE
) |> 
  dplyr::group_by(x, y) |> 
  dplyr::summarise(
    z1 = sum(z1),
    z2 = sum(z2)
  ) |> 
  dplyr::ungroup() 
#> `summarise()` has grouped output by 'x'. You can override using the `.groups`
#> argument.
  
trans <- list(opacity = 0.4) # transparency
emphasis <- list(itemStyle = list(color = "#313695"))
  
matrix |> 
  e_charts(x) |> 
  e_bar_3d(y, z1, stack = "stack", name = "Serie 1", itemStyle = trans, emphasis = emphasis) |>
  e_bar_3d(y, z2, stack = "stack", name = "Serie 2", itemStyle = trans, emphasis = emphasis) |> 
  e_legend()
```

</div>

<div id="htmlwidget-e5c8c404fe174e4c81bd"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Scatter

<div id="cb3" class="sourceCode">

``` r
v <- LETTERS[1:10]
matrix <- data.frame(
  x = sample(v, 300, replace = TRUE), 
  y = sample(v, 300, replace = TRUE), 
  z = rnorm(300, 10, 1),
  color = rnorm(300, 10, 1),
  size = rnorm(300, 10, 1),
  stringsAsFactors = FALSE
) |> 
  dplyr::group_by(x, y) |> 
  dplyr::summarise(
    z = sum(z),
    color = sum(color),
    size = sum(size)
  ) |> 
  dplyr::ungroup() 
#> `summarise()` has grouped output by 'x'. You can override using the `.groups`
#> argument.
  
matrix |> 
  e_charts(x) |> 
  e_scatter_3d(y, z, size, color) |> 
  e_visual_map(
    size,
    inRange = list(symbolSize = c(1, 30)), # scale size
    dimension = 3 # third dimension 0 = x, y = 1, z = 2, size = 3
  ) |> 
  e_visual_map(
    color,
    inRange = list(color = c('#bf444c', '#d88273', '#f6efa6')), # scale colors
    dimension = 4, # third dimension 0 = x, y = 1, z = 2, size = 3, color = 4
    bottom = 300 # padding to avoid visual maps overlap
  )
```

</div>

<div id="htmlwidget-36aa3d2a04d42bbc2145"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

<div class="section level2">

## Line

<div id="cb4" class="sourceCode">

``` r
df <- data.frame(
  x = 1:100,
  y = runif(100, 10, 25),
  z = rnorm(100, 100, 50)
)

df |> 
  e_charts(x) |> 
  e_line_3d(y, z, smooth = TRUE) |> 
  e_visual_map()
```

</div>

<div id="htmlwidget-febe03efa1a2d8d52a86"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
