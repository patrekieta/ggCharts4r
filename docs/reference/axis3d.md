<div id="main" class="col-md-9" role="main">

# Axis 3D

<div class="ref-description section level2">

Customise 3D axis.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_axis_3d(e, axis = c("x", "y", "z"), index = 0, ...)

e_x_axis_3d(e, index = 0, ...)

e_y_axis_3d(e, index = 0, ...)

e_z_axis_3d(e, index = 0, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   axis:

    Axis to customise.

-   index:

    Index of axis to customise.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional x
arguments](https://echarts.apache.org/en/option-gl.html#xAxis3D),
[Additional y
arguments](https://echarts.apache.org/en/option-gl.html#yAxis3D),
[Additional z
arguments](https://echarts.apache.org/en/option-gl.html#zAxis3D)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
# phony data
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
  e_x_axis_3d(axisLine = list(lineStyle = list(color = "blue")))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"xAxis3D":[{"type":"category","data":["A","B","C","D","E","F","G","H","I","J"],"axisLine":{"lineStyle":{"color":"blue"}}}],"yAxis3D":[{"type":"category","data":["A","B","C","D","F","G","H","I","J","E"]}],"zAxis3D":[{"type":"value"}],"grid3D":[{"show":true}],"legend":{"data":["Serie 1","Serie 2"]},"series":[{"name":"Serie 1","type":"bar3D","coordinateSystem":"cartesian3D","data":[{"value":["A","A"," 60.305504"]},{"value":["A","B"," 50.115865"]},{"value":["A","C"," 41.170632"]},{"value":["A","D"," 30.706813"]},{"value":["A","F"," 29.447792"]},{"value":["A","G"," 39.087371"]},{"value":["A","H","  9.053693"]},{"value":["A","I"," 28.880299"]},{"value":["A","J"," 28.890699"]},{"value":["B","A"," 41.364915"]},{"value":["B","B"," 10.941699"]},{"value":["B","C"," 77.481616"]},{"value":["B","D"," 20.882622"]},{"value":["B","F"," 53.163899"]},{"value":["B","G"," 42.009088"]},{"value":["B","H","  8.482680"]},{"value":["B","I"," 30.010300"]},{"value":["B","J"," 69.505725"]},{"value":["C","A"," 41.857142"]},{"value":["C","B"," 40.453958"]},{"value":["C","C"," 10.252451"]},{"value":["C","D"," 52.420101"]},{"value":["C","E"," 20.468964"]},{"value":["C","F"," 20.676385"]},{"value":["C","G"," 31.019735"]},{"value":["C","H","  9.481143"]},{"value":["C","I"," 19.690338"]},{"value":["C","J"," 41.453069"]},{"value":["D","A"," 18.525964"]},{"value":["D","B"," 10.416763"]},{"value":["D","C"," 30.707041"]},{"value":["D","D"," 10.298087"]},{"value":["D","E"," 19.813112"]},{"value":["D","F"," 26.590180"]},{"value":["D","G"," 28.407949"]},{"value":["D","H"," 41.615859"]},{"value":["D","J"," 49.963103"]},{"value":["E","A"," 30.132899"]},{"value":["E","B"," 29.892598"]},{"value":["E","D"," 19.956015"]},{"value":["E","E"," 28.967994"]},{"value":["E","F"," 28.987695"]},{"value":["E","G"," 30.760969"]},{"value":["E","H"," 60.293704"]},{"value":["E","I"," 38.219733"]},{"value":["E","J"," 29.435246"]},{"value":["F","A"," 20.110939"]},{"value":["F","B"," 31.947463"]},{"value":["F","C"," 19.344995"]},{"value":["F","D"," 64.981246"]},{"value":["F","E"," 26.615125"]},{"value":["F","F"," 21.762324"]},{"value":["F","G"," 49.485639"]},{"value":["F","H"," 17.858002"]},{"value":["F","I"," 22.560246"]},{"value":["F","J"," 39.788569"]},{"value":["G","A"," 39.694926"]},{"value":["G","B"," 21.544664"]},{"value":["G","C"," 19.815555"]},{"value":["G","D"," 20.945689"]},{"value":["G","E"," 27.880918"]},{"value":["G","F"," 31.251887"]},{"value":["G","H"," 40.613522"]},{"value":["G","I"," 53.325375"]},{"value":["G","J"," 56.233879"]},{"value":["H","A"," 49.737321"]},{"value":["H","B"," 20.459656"]},{"value":["H","C"," 60.843544"]},{"value":["H","D"," 17.569331"]},{"value":["H","E"," 10.914607"]},{"value":["H","F","  9.687534"]},{"value":["H","G"," 21.040179"]},{"value":["H","H","  9.616827"]},{"value":["H","I"," 42.246212"]},{"value":["H","J"," 10.598055"]},{"value":["I","A"," 18.125133"]},{"value":["I","B"," 46.674598"]},{"value":["I","C"," 16.999850"]},{"value":["I","D"," 39.375934"]},{"value":["I","E"," 11.053655"]},{"value":["I","F"," 43.025267"]},{"value":["I","G"," 20.909934"]},{"value":["I","H"," 37.852167"]},{"value":["I","I"," 10.392023"]},{"value":["I","J"," 41.627045"]},{"value":["J","A","  8.951542"]},{"value":["J","B"," 41.561237"]},{"value":["J","C"," 26.945619"]},{"value":["J","D"," 38.106903"]},{"value":["J","E","106.049994"]},{"value":["J","G"," 25.312526"]},{"value":["J","H"," 19.936005"]},{"value":["J","I"," 40.336948"]},{"value":["J","J"," 39.815264"]}],"stack":"stack","itemStyle":{"opacity":0.4},"emphasis":{"itemStyle":{"color":"#313695"}}},{"name":"Serie 2","type":"bar3D","coordinateSystem":"cartesian3D","data":[{"value":["A","A","60.810849"]},{"value":["A","B","51.672764"]},{"value":["A","C","36.986437"]},{"value":["A","D","32.485120"]},{"value":["A","F","29.106461"]},{"value":["A","G","40.338767"]},{"value":["A","H"," 9.068480"]},{"value":["A","I","31.492357"]},{"value":["A","J","30.156471"]},{"value":["B","A","42.542768"]},{"value":["B","B"," 8.605536"]},{"value":["B","C","78.082687"]},{"value":["B","D","20.223783"]},{"value":["B","F","49.231150"]},{"value":["B","G","39.324664"]},{"value":["B","H","10.577854"]},{"value":["B","I","30.584493"]},{"value":["B","J","71.156695"]},{"value":["C","A","37.129502"]},{"value":["C","B","43.988312"]},{"value":["C","C","11.209732"]},{"value":["C","D","47.538905"]},{"value":["C","E","19.634988"]},{"value":["C","F","19.129996"]},{"value":["C","G","33.741378"]},{"value":["C","H","11.011451"]},{"value":["C","I","22.367739"]},{"value":["C","J","39.141935"]},{"value":["D","A","22.434755"]},{"value":["D","B"," 8.595985"]},{"value":["D","C","29.227856"]},{"value":["D","D","11.773852"]},{"value":["D","E","18.784083"]},{"value":["D","F","30.390350"]},{"value":["D","G","29.212188"]},{"value":["D","H","39.826484"]},{"value":["D","J","46.336546"]},{"value":["E","A","29.099559"]},{"value":["E","B","28.789530"]},{"value":["E","D","18.921832"]},{"value":["E","E","30.918201"]},{"value":["E","F","32.369095"]},{"value":["E","G","30.195156"]},{"value":["E","H","57.082447"]},{"value":["E","I","39.861246"]},{"value":["E","J","29.746820"]},{"value":["F","A","18.761253"]},{"value":["F","B","30.014744"]},{"value":["F","C","17.909948"]},{"value":["F","D","61.625227"]},{"value":["F","E","28.617280"]},{"value":["F","F","21.235332"]},{"value":["F","G","49.675824"]},{"value":["F","H","21.432411"]},{"value":["F","I","19.616452"]},{"value":["F","J","39.501161"]},{"value":["G","A","43.996368"]},{"value":["G","B","17.658457"]},{"value":["G","C","20.628929"]},{"value":["G","D","19.731141"]},{"value":["G","E","31.999471"]},{"value":["G","F","28.174880"]},{"value":["G","H","36.686611"]},{"value":["G","I","46.126778"]},{"value":["G","J","59.923579"]},{"value":["H","A","50.510178"]},{"value":["H","B","20.714749"]},{"value":["H","C","62.731343"]},{"value":["H","D","20.356817"]},{"value":["H","E","12.648916"]},{"value":["H","F","10.311709"]},{"value":["H","G","19.726537"]},{"value":["H","H","10.516876"]},{"value":["H","I","39.614491"]},{"value":["H","J"," 9.663411"]},{"value":["I","A","20.286025"]},{"value":["I","B","51.598292"]},{"value":["I","C","20.459518"]},{"value":["I","D","45.970725"]},{"value":["I","E","10.510437"]},{"value":["I","F","38.777393"]},{"value":["I","G","18.383967"]},{"value":["I","H","39.156358"]},{"value":["I","I","10.342697"]},{"value":["I","J","41.550019"]},{"value":["J","A"," 8.900160"]},{"value":["J","B","40.236069"]},{"value":["J","C","28.001781"]},{"value":["J","D","38.926428"]},{"value":["J","E","98.954968"]},{"value":["J","G","30.283394"]},{"value":["J","H","19.472131"]},{"value":["J","I","38.779245"]},{"value":["J","J","40.633979"]}],"stack":"stack","itemStyle":{"opacity":0.4},"emphasis":{"itemStyle":{"color":"#313695"}}}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
