<div id="main" class="col-md-9" role="main">

# Visual Map

<div class="ref-description section level2">

Visual Map

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_visual_map(
  e,
  serie,
  calculable = TRUE,
  type = c("continuous", "piecewise"),
  scale = NULL,
  ...
)

e_visual_map_(
  e,
  serie = NULL,
  calculable = TRUE,
  type = c("continuous", "piecewise"),
  scale = NULL,
  ...
)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   serie:

    Column name of serie to scale against.

-   calculable:

    Whether show handles, which can be dragged to adjust "selected
    range".

-   type:

    One of `continuous` or `piecewise`.

-   scale:

    A function that takes a vector of `numeric` and returns a vector of
    `numeric` of the same length.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## Scaling function

defaults to `e_scale` which is a basic function that rescales `size`
between 1 and 20 for that makes for decent sized points on the chart.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#visualMap)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
# scaled data
mtcars |>
  e_charts(mpg) |>
  e_scatter(wt, qsec, scale = e_scale) |>
  e_visual_map(qsec, scale = e_scale)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"type":"value"}],"legend":{"data":["wt"]},"series":[{"data":[{"value":[10.4,5.25,17.98,8.871428571428574]},{"value":[10.4,5.424,17.82,8.509523809523811]},{"value":[13.3,3.84,15.41,3.058333333333334]},{"value":[14.3,3.57,15.84,4.030952380952382]},{"value":[14.7,5.345,17.42,7.60476190476191]},{"value":[15,3.57,14.6,1.226190476190475]},{"value":[15.2,3.78,18,8.916666666666668]},{"value":[15.2,3.435,17.3,7.333333333333336]},{"value":[15.5,3.52,16.87,6.360714285714288]},{"value":[15.8,3.17,14.5,1]},{"value":[16.4,4.07,17.4,7.559523809523808]},{"value":[17.3,3.73,17.6,8.011904761904766]},{"value":[17.8,3.44,18.9,10.95238095238095]},{"value":[18.1,3.46,20.22,13.93809523809524]},{"value":[18.7,3.44,17.02,6.7]},{"value":[19.2,3.44,18.3,9.595238095238098]},{"value":[19.2,3.845,17.05,6.767857142857146]},{"value":[19.7,2.77,15.5,3.261904761904762]},{"value":[21,2.62,16.46,5.433333333333336]},{"value":[21,2.875,17.02,6.7]},{"value":[21.4,3.215,19.44,12.17380952380953]},{"value":[21.4,2.78,18.6,10.27380952380953]},{"value":[21.5,2.465,20.01,13.46309523809524]},{"value":[22.8,2.32,18.61,10.29642857142857]},{"value":[22.8,3.15,22.9,20]},{"value":[24.4,3.19,20,13.44047619047619]},{"value":[26,2.14,16.7,5.976190476190475]},{"value":[27.3,1.935,18.9,10.95238095238095]},{"value":[30.4,1.615,18.52,10.09285714285714]},{"value":[30.4,1.513,16.9,6.428571428571426]},{"value":[32.4,2.2,19.47,12.24166666666667]},{"value":[33.9,1.835,19.9,13.21428571428571]}],"name":"wt","type":"scatter","symbol":null,"coordinateSystem":"cartesian2d","yAxisIndex":0,"xAxisIndex":0,"symbolSize":"function(data){ return data[3];}"}],"visualMap":[{"calculable":true,"type":"continuous","min":1,"max":20}]},"dispose":true},"evals":["opts.series.0.symbolSize"],"jsHooks":[]}
# dimension
# color according to y axis
mtcars |>
  e_charts(mpg) |>
  e_scatter(wt) |>
  e_visual_map(wt, dimension = 1)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"type":"value"}],"legend":{"data":["wt"]},"series":[{"data":[{"value":[10.4,5.25]},{"value":[10.4,5.424]},{"value":[13.3,3.84]},{"value":[14.3,3.57]},{"value":[14.7,5.345]},{"value":[15,3.57]},{"value":[15.2,3.78]},{"value":[15.2,3.435]},{"value":[15.5,3.52]},{"value":[15.8,3.17]},{"value":[16.4,4.07]},{"value":[17.3,3.73]},{"value":[17.8,3.44]},{"value":[18.1,3.46]},{"value":[18.7,3.44]},{"value":[19.2,3.44]},{"value":[19.2,3.845]},{"value":[19.7,2.77]},{"value":[21,2.62]},{"value":[21,2.875]},{"value":[21.4,3.215]},{"value":[21.4,2.78]},{"value":[21.5,2.465]},{"value":[22.8,2.32]},{"value":[22.8,3.15]},{"value":[24.4,3.19]},{"value":[26,2.14]},{"value":[27.3,1.935]},{"value":[30.4,1.615]},{"value":[30.4,1.513]},{"value":[32.4,2.2]},{"value":[33.9,1.835]}],"name":"wt","type":"scatter","symbol":null,"coordinateSystem":"cartesian2d","yAxisIndex":0,"xAxisIndex":0,"symbolSize":3}],"visualMap":[{"dimension":1,"calculable":true,"type":"continuous","min":1.513,"max":5.424}]},"dispose":true},"evals":[],"jsHooks":[]}
# color according to x axis
mtcars |>
  e_charts(mpg) |>
  e_scatter(wt) |>
  e_visual_map(mpg, dimension = 0)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"type":"value"}],"legend":{"data":["wt"]},"series":[{"data":[{"value":[10.4,5.25]},{"value":[10.4,5.424]},{"value":[13.3,3.84]},{"value":[14.3,3.57]},{"value":[14.7,5.345]},{"value":[15,3.57]},{"value":[15.2,3.78]},{"value":[15.2,3.435]},{"value":[15.5,3.52]},{"value":[15.8,3.17]},{"value":[16.4,4.07]},{"value":[17.3,3.73]},{"value":[17.8,3.44]},{"value":[18.1,3.46]},{"value":[18.7,3.44]},{"value":[19.2,3.44]},{"value":[19.2,3.845]},{"value":[19.7,2.77]},{"value":[21,2.62]},{"value":[21,2.875]},{"value":[21.4,3.215]},{"value":[21.4,2.78]},{"value":[21.5,2.465]},{"value":[22.8,2.32]},{"value":[22.8,3.15]},{"value":[24.4,3.19]},{"value":[26,2.14]},{"value":[27.3,1.935]},{"value":[30.4,1.615]},{"value":[30.4,1.513]},{"value":[32.4,2.2]},{"value":[33.9,1.835]}],"name":"wt","type":"scatter","symbol":null,"coordinateSystem":"cartesian2d","yAxisIndex":0,"xAxisIndex":0,"symbolSize":3}],"visualMap":[{"dimension":0,"calculable":true,"type":"continuous","min":10.4,"max":33.9}]},"dispose":true},"evals":[],"jsHooks":[]}
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
  e_scatter_3d(y, z, color, size) |>
  e_visual_map(
    z,
    # scale to z
    inRange = list(symbolSize = c(1, 30)),
    # scale size
    dimension = 3 # third dimension 0 = x, y = 1, z = 2, size = 3
  ) |>
  e_visual_map(
    z,
    # scale to z
    inRange = list(color = c("#bf444c", "#d88273", "#f6efa6")),
    # scale colors
    dimension = 4,
    # third dimension 0 = x, y = 1, z = 2, size = 3, color = 4
    bottom = 300 # padding to avoid visual maps overlap
  )

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"zAxis3D":[{"show":true}],"grid3D":[{"show":true}],"xAxis3D":[{"type":"category","data":["A","B","C","D","E","F","G","H","I","J"]}],"yAxis3D":[{"type":"category","data":["A","C","D","E","F","G","H","I","J","B"]}],"series":[{"type":"scatter3D","coordinateSystem":"cartesian3D","data":[{"value":["A","A"," 9.796386"," 8.530292","10.735648"]},{"value":["A","C","17.967108","20.643017","16.205364"]},{"value":["A","D","27.125454","31.318845","31.020407"]},{"value":["A","E","37.409726","33.907586","42.784637"]},{"value":["A","F","28.641779","33.306711","29.828340"]},{"value":["A","G","37.113430","38.354232","38.180628"]},{"value":["A","H","28.934821","27.144888","29.247252"]},{"value":["A","I","51.895056","49.383035","45.911246"]},{"value":["A","J","11.212176"," 7.396841","10.751126"]},{"value":["B","A","41.607397","42.685224","38.141451"]},{"value":["B","B","10.049744"," 9.823549"," 9.987884"]},{"value":["B","C","91.061280","91.269289","90.288251"]},{"value":["B","D","10.871016","10.793766"," 9.854695"]},{"value":["B","E","11.412644","10.054241","10.938060"]},{"value":["B","F","40.586125","38.929110","36.860515"]},{"value":["B","G","11.925793","10.091799","10.182873"]},{"value":["B","H","39.564996","41.594998","40.958549"]},{"value":["B","I","20.490935","22.121480","20.298666"]},{"value":["B","J","30.582272","25.933367","34.999625"]},{"value":["C","A","41.468511","37.234347","41.256159"]},{"value":["C","B","26.756752","26.284448","32.768294"]},{"value":["C","C","28.108856","32.023652","29.904584"]},{"value":["C","D","27.951851","28.681495","28.848211"]},{"value":["C","E","38.657074","42.977783","41.055098"]},{"value":["C","F","18.554739","16.881477","19.998416"]},{"value":["C","G","57.422246","56.955297","60.132167"]},{"value":["C","H","49.906958","54.118718","50.939842"]},{"value":["C","I","48.199349","52.022698","54.637014"]},{"value":["C","J","51.143948","46.380152","45.855050"]},{"value":["D","A","31.801199","28.366870","29.299061"]},{"value":["D","B"," 8.531454","10.562416","10.207061"]},{"value":["D","C","29.106259","28.567823","30.271114"]},{"value":["D","D","39.466785","44.674709","38.549382"]},{"value":["D","E","29.226934","30.103440","30.667760"]},{"value":["D","F","39.325485","38.793583","40.154362"]},{"value":["D","G","20.463183","19.508709","20.617201"]},{"value":["D","H","18.051986","16.642945","19.276539"]},{"value":["D","I","38.182333","41.580393","42.495730"]},{"value":["D","J","42.891554","41.965146","36.156754"]},{"value":["E","A","55.115225","56.590596","57.887930"]},{"value":["E","B","20.784695","20.009195","17.168711"]},{"value":["E","C","10.275828"," 9.119457","10.316468"]},{"value":["E","D","26.940436","27.108109","31.206347"]},{"value":["E","E","21.302984","21.593966","20.638074"]},{"value":["E","F","60.581770","60.109819","60.068547"]},{"value":["E","G","19.449617","20.629850","20.724486"]},{"value":["E","H","55.177662","46.996133","50.292527"]},{"value":["E","I","48.165836","55.440600","47.798414"]},{"value":["E","J","39.456877","40.661264","39.417061"]},{"value":["F","A","29.721893","28.063468","27.185033"]},{"value":["F","B","19.943730","19.497975","20.977655"]},{"value":["F","C","28.574965","31.445015","32.011261"]},{"value":["F","E","30.817969","31.133746","29.825092"]},{"value":["F","F","38.573871","38.584304","43.753816"]},{"value":["F","H","49.637015","50.933994","50.323031"]},{"value":["F","I","47.811612","48.747261","47.542880"]},{"value":["F","J","18.168454","17.833540","20.691919"]},{"value":["G","A"," 9.728482","10.633625","11.126324"]},{"value":["G","B","37.098054","38.920498","37.846735"]},{"value":["G","D","20.861627","19.361680","20.434962"]},{"value":["G","E","30.462941","30.519625","32.117276"]},{"value":["G","F","30.650440","31.404013","31.645698"]},{"value":["G","G","74.706430","69.922007","69.894416"]},{"value":["G","H"," 9.927951"," 9.841626"," 9.386462"]},{"value":["G","I","28.099598","30.926963","32.354450"]},{"value":["G","J","18.667216","21.357616","20.939627"]},{"value":["H","A","30.802586","29.350768","30.562175"]},{"value":["H","B","11.672767","11.409822","10.682768"]},{"value":["H","C","39.993580","40.881986","41.905413"]},{"value":["H","D","31.851047","33.519773","29.126802"]},{"value":["H","E","20.573265","18.471462","20.556063"]},{"value":["H","F","54.735147","50.269152","49.273166"]},{"value":["H","G","17.731769","23.806955","23.441252"]},{"value":["H","H"," 9.682304","10.305548","11.272065"]},{"value":["H","I","10.848286"," 9.341075"," 9.085804"]},{"value":["H","J","20.279905","19.829046","20.805039"]},{"value":["I","A","22.484992","19.459056","18.320195"]},{"value":["I","B","30.495218","33.759467","28.742343"]},{"value":["I","C","19.949865","20.515367","21.352628"]},{"value":["I","D","40.985199","40.413392","40.631200"]},{"value":["I","E","29.883602","24.683005","27.501358"]},{"value":["I","F","20.591546","21.820271","18.290701"]},{"value":["I","G","53.238817","49.064895","53.532112"]},{"value":["I","H","51.022410","51.667062","49.425986"]},{"value":["I","I","11.451657"," 9.519939","10.679134"]},{"value":["I","J","37.986124","39.381306","40.635635"]},{"value":["J","A","20.277514","19.749850","22.058614"]},{"value":["J","B","38.325879","40.634436","37.156508"]},{"value":["J","C","53.200047","52.982593","48.550722"]},{"value":["J","D","38.645234","39.398771","42.524648"]},{"value":["J","E","19.417601","19.720409","17.843671"]},{"value":["J","F"," 9.600565"," 8.421685","10.739455"]},{"value":["J","G","12.400586","10.373669"," 9.066045"]},{"value":["J","H","38.784925","39.044494","39.848596"]},{"value":["J","I","17.701642","19.685793","18.694502"]},{"value":["J","J","49.927721","51.760459","53.199023"]}]}],"visualMap":[{"inRange":{"symbolSize":[1,30]},"dimension":3,"calculable":true,"type":"continuous","min":8.531453788981327,"max":91.06127994265182},{"inRange":{"color":["#bf444c","#d88273","#f6efa6"]},"dimension":4,"bottom":300,"calculable":true,"type":"continuous","min":8.531453788981327,"max":91.06127994265182}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
