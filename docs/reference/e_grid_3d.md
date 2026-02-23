<div id="main" class="col-md-9" role="main">

# Grid

<div class="ref-description section level2">

Customise grid.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_grid_3d(e, index = 0, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   index:

    Index of axis to customise.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option-gl.html#grid3D)

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
  e_grid_3d(splitLine = list(lineStyle = list(color = "blue")))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"xAxis3D":[{"type":"category","data":["A","B","C","D","E","F","G","H","I","J"]}],"yAxis3D":[{"type":"category","data":["A","B","C","D","E","G","H","I","J","F"]}],"zAxis3D":[{"type":"value"}],"grid3D":[{"show":true,"splitLine":{"lineStyle":{"color":"blue"}}}],"legend":{"data":["Serie 1","Serie 2"]},"series":[{"name":"Serie 1","type":"bar3D","coordinateSystem":"cartesian3D","data":[{"value":["A","A","42.927922"]},{"value":["A","B","33.376055"]},{"value":["A","C","59.031261"]},{"value":["A","D","30.384876"]},{"value":["A","E","62.335543"]},{"value":["A","G"," 9.064454"]},{"value":["A","H","38.642883"]},{"value":["A","I","40.678023"]},{"value":["A","J","10.162067"]},{"value":["B","A","56.736596"]},{"value":["B","B","19.936616"]},{"value":["B","C","46.151601"]},{"value":["B","D","20.201453"]},{"value":["B","E","31.983067"]},{"value":["B","F","11.462713"]},{"value":["B","G","47.768098"]},{"value":["B","H","31.597230"]},{"value":["B","I","19.967852"]},{"value":["B","J","30.312694"]},{"value":["C","A","11.667790"]},{"value":["C","B","10.334140"]},{"value":["C","C","48.401016"]},{"value":["C","E","19.775540"]},{"value":["C","F"," 9.567033"]},{"value":["C","G","54.435346"]},{"value":["C","H","30.278745"]},{"value":["C","I","20.495240"]},{"value":["C","J","50.903335"]},{"value":["D","A","40.824221"]},{"value":["D","B","11.186080"]},{"value":["D","C","27.352916"]},{"value":["D","D","63.300564"]},{"value":["D","E","59.855766"]},{"value":["D","F","65.231490"]},{"value":["D","G","49.011041"]},{"value":["D","H","19.800333"]},{"value":["D","J","10.990253"]},{"value":["E","A","42.612021"]},{"value":["E","B","25.701207"]},{"value":["E","C","41.854381"]},{"value":["E","D","39.131087"]},{"value":["E","E","50.037747"]},{"value":["E","G","28.696295"]},{"value":["E","H","33.299087"]},{"value":["E","I","48.218752"]},{"value":["E","J","49.550426"]},{"value":["F","A","23.037022"]},{"value":["F","B","37.512043"]},{"value":["F","C","11.466943"]},{"value":["F","D","40.164677"]},{"value":["F","E","28.806145"]},{"value":["F","F","15.605739"]},{"value":["F","G"," 9.806109"]},{"value":["F","H","37.619645"]},{"value":["F","I","31.826080"]},{"value":["F","J","70.279730"]},{"value":["G","A","18.649304"]},{"value":["G","B","62.580460"]},{"value":["G","C"," 9.699865"]},{"value":["G","D","51.132502"]},{"value":["G","E","21.109951"]},{"value":["G","G","11.085457"]},{"value":["G","H","20.839268"]},{"value":["G","I","21.395350"]},{"value":["G","J","36.620035"]},{"value":["H","A","29.986372"]},{"value":["H","B"," 8.696887"]},{"value":["H","D","39.151154"]},{"value":["H","E","19.767273"]},{"value":["H","F","58.957840"]},{"value":["H","G","17.518680"]},{"value":["H","H","20.100360"]},{"value":["H","I","28.055924"]},{"value":["H","J","20.736885"]},{"value":["I","A","42.335375"]},{"value":["I","B","30.528819"]},{"value":["I","C","42.136825"]},{"value":["I","D","28.548050"]},{"value":["I","E","29.056498"]},{"value":["I","F"," 9.053361"]},{"value":["I","G","32.802468"]},{"value":["I","H","30.705624"]},{"value":["I","I","41.751709"]},{"value":["I","J","18.719779"]},{"value":["J","A","39.321642"]},{"value":["J","C","61.971057"]},{"value":["J","D","49.084230"]},{"value":["J","E","10.510087"]},{"value":["J","F","50.500266"]},{"value":["J","G","10.314096"]},{"value":["J","H","45.750766"]},{"value":["J","I","10.606210"]},{"value":["J","J","19.813039"]}],"stack":"stack","itemStyle":{"opacity":0.4},"emphasis":{"itemStyle":{"color":"#313695"}}},{"name":"Serie 2","type":"bar3D","coordinateSystem":"cartesian3D","data":[{"value":["A","A","37.432960"]},{"value":["A","B","29.688917"]},{"value":["A","C","66.016729"]},{"value":["A","D","31.565410"]},{"value":["A","E","61.140458"]},{"value":["A","G"," 9.613569"]},{"value":["A","H","39.273960"]},{"value":["A","I","42.706211"]},{"value":["A","J","10.394936"]},{"value":["B","A","59.794242"]},{"value":["B","B","21.058722"]},{"value":["B","C","47.874950"]},{"value":["B","D","20.349546"]},{"value":["B","E","31.507527"]},{"value":["B","F","10.683231"]},{"value":["B","G","45.984629"]},{"value":["B","H","28.946240"]},{"value":["B","I","18.396630"]},{"value":["B","J","30.120657"]},{"value":["C","A","10.359922"]},{"value":["C","B","11.156383"]},{"value":["C","C","48.719308"]},{"value":["C","E","21.217805"]},{"value":["C","F","10.136820"]},{"value":["C","G","48.977745"]},{"value":["C","H","31.494661"]},{"value":["C","I","19.795281"]},{"value":["C","J","46.305745"]},{"value":["D","A","40.455872"]},{"value":["D","B","11.569251"]},{"value":["D","C","31.563766"]},{"value":["D","D","59.351254"]},{"value":["D","E","60.720743"]},{"value":["D","F","59.831047"]},{"value":["D","G","47.730017"]},{"value":["D","H","21.250588"]},{"value":["D","J","10.581832"]},{"value":["E","A","38.523957"]},{"value":["E","B","31.833327"]},{"value":["E","C","39.847957"]},{"value":["E","D","35.272519"]},{"value":["E","E","55.618086"]},{"value":["E","G","33.174384"]},{"value":["E","H","30.683493"]},{"value":["E","I","50.521324"]},{"value":["E","J","47.157632"]},{"value":["F","A","19.783900"]},{"value":["F","B","43.519186"]},{"value":["F","C"," 8.839070"]},{"value":["F","D","41.596108"]},{"value":["F","E","32.412934"]},{"value":["F","F","21.074642"]},{"value":["F","G"," 8.775483"]},{"value":["F","H","41.035963"]},{"value":["F","I","30.512233"]},{"value":["F","J","71.481585"]},{"value":["G","A","22.107454"]},{"value":["G","B","59.413977"]},{"value":["G","C"," 8.716337"]},{"value":["G","D","49.102456"]},{"value":["G","E","18.904610"]},{"value":["G","G"," 8.186400"]},{"value":["G","H","19.179034"]},{"value":["G","I","22.981494"]},{"value":["G","J","39.151749"]},{"value":["H","A","29.359891"]},{"value":["H","B","12.012778"]},{"value":["H","D","39.698382"]},{"value":["H","E","17.423513"]},{"value":["H","F","65.343939"]},{"value":["H","G","17.569592"]},{"value":["H","H","18.888483"]},{"value":["H","I","31.364402"]},{"value":["H","J","21.099042"]},{"value":["I","A","41.084820"]},{"value":["I","B","31.636005"]},{"value":["I","C","43.537927"]},{"value":["I","D","31.413345"]},{"value":["I","E","30.042700"]},{"value":["I","F"," 8.561075"]},{"value":["I","G","31.641839"]},{"value":["I","H","29.512270"]},{"value":["I","I","36.654594"]},{"value":["I","J","17.693215"]},{"value":["J","A","37.348880"]},{"value":["J","C","62.244096"]},{"value":["J","D","46.707774"]},{"value":["J","E"," 7.632201"]},{"value":["J","F","49.712600"]},{"value":["J","G"," 9.073154"]},{"value":["J","H","50.316986"]},{"value":["J","I"," 9.869677"]},{"value":["J","J","17.472848"]}],"stack":"stack","itemStyle":{"opacity":0.4},"emphasis":{"itemStyle":{"color":"#313695"}}}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
