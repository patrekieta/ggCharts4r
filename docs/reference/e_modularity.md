<div id="main" class="col-md-9" role="main">

# Modularity

<div class="ref-description section level2">

Graph modularity extension will do community detection and partian a
graph's vertices in several subsets. Each subset will be assigned a
different color.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_modularity(e, modularity = TRUE)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   modularity:

    Either set to `TRUE`, or a `list`.

</div>

<div class="section level2">

## Note

Does not work in RStudio viewer, open in browser.

</div>

<div class="section level2">

## Modularity

-   `resolution` Resolution

-   `sort` Whether to sort to comunities

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Official
documentation](https://github.com/ecomfe/echarts-graph-modularity)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
nodes <- data.frame(
  name = paste0(LETTERS, 1:100),
  value = rnorm(100, 10, 2),
  stringsAsFactors = FALSE
)

edges <- data.frame(
  source = sample(nodes$name, 200, replace = TRUE),
  target = sample(nodes$name, 200, replace = TRUE),
  stringsAsFactors = FALSE
)

e_charts() |>
  e_graph() |>
  e_graph_nodes(nodes, name, value) |>
  e_graph_edges(edges, source, target) |>
  e_modularity(
    list(
      resolution = 5,
      sort = TRUE
    )
  )

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"series":[{"name":null,"type":"graph","layout":"force","data":[{"name":"A1","value":"10.924533"},{"name":"B2","value":"10.492292"},{"name":"C3","value":"11.605491"},{"name":"D4","value":"10.663743"},{"name":"E5","value":" 9.279050"},{"name":"F6","value":"10.303126"},{"name":"G7","value":" 6.661270"},{"name":"H8","value":" 9.913019"},{"name":"I9","value":" 9.954196"},{"name":"J10","value":"14.583547"},{"name":"K11","value":" 9.933982"},{"name":"L12","value":" 5.939944"},{"name":"M13","value":"10.130221"},{"name":"N14","value":" 7.548837"},{"name":"O15","value":" 8.933618"},{"name":"P16","value":" 9.412870"},{"name":"Q17","value":"10.097074"},{"name":"R18","value":"11.859476"},{"name":"S19","value":"10.696288"},{"name":"T20","value":"11.099345"},{"name":"U21","value":"11.351420"},{"name":"V22","value":"13.862228"},{"name":"W23","value":"11.939055"},{"name":"X24","value":" 9.520270"},{"name":"Y25","value":"11.183074"},{"name":"Z26","value":" 8.728371"},{"name":"A27","value":"10.651909"},{"name":"B28","value":"12.828449"},{"name":"C29","value":"11.623017"},{"name":"D30","value":" 9.550679"},{"name":"E31","value":"11.643757"},{"name":"F32","value":" 6.774772"},{"name":"G33","value":" 8.233425"},{"name":"H34","value":"11.588828"},{"name":"I35","value":" 8.487785"},{"name":"J36","value":" 7.052675"},{"name":"K37","value":"11.398997"},{"name":"L38","value":"12.761343"},{"name":"M39","value":" 9.705234"},{"name":"N40","value":" 9.738376"},{"name":"O41","value":" 7.456301"},{"name":"P42","value":" 9.493419"},{"name":"Q43","value":"10.474307"},{"name":"R44","value":"10.923459"},{"name":"S45","value":" 6.369480"},{"name":"T46","value":" 7.175981"},{"name":"U47","value":" 8.571737"},{"name":"V48","value":" 9.281423"},{"name":"W49","value":" 5.833540"},{"name":"X50","value":"11.839735"},{"name":"Y51","value":" 6.380880"},{"name":"Z52","value":" 6.227755"},{"name":"A53","value":" 7.717340"},{"name":"B54","value":" 8.629167"},{"name":"C55","value":" 9.471238"},{"name":"D56","value":"14.358675"},{"name":"E57","value":" 8.114160"},{"name":"F58","value":" 9.647083"},{"name":"G59","value":" 7.279971"},{"name":"H60","value":"12.628318"},{"name":"I61","value":" 8.577369"},{"name":"J62","value":" 9.777033"},{"name":"K63","value":"10.546483"},{"name":"L64","value":"11.074619"},{"name":"M65","value":"10.696261"},{"name":"N66","value":" 9.826963"},{"name":"O67","value":" 6.507918"},{"name":"P68","value":"13.041395"},{"name":"Q69","value":" 7.795011"},{"name":"R70","value":" 9.874850"},{"name":"S71","value":" 8.315450"},{"name":"T72","value":" 9.554759"},{"name":"U73","value":"11.661029"},{"name":"V74","value":" 9.302661"},{"name":"W75","value":" 9.937586"},{"name":"X76","value":"10.414799"},{"name":"Y77","value":"12.003694"},{"name":"Z78","value":" 9.273211"},{"name":"A79","value":"10.222189"},{"name":"B80","value":" 6.791815"},{"name":"C81","value":"11.727860"},{"name":"D82","value":"10.728340"},{"name":"E83","value":"11.646444"},{"name":"F84","value":"11.833120"},{"name":"G85","value":"11.642581"},{"name":"H86","value":"10.687931"},{"name":"I87","value":"11.298639"},{"name":"J88","value":" 9.811688"},{"name":"K89","value":" 9.172784"},{"name":"L90","value":"10.173206"},{"name":"M91","value":" 8.190653"},{"name":"N92","value":"11.513985"},{"name":"O93","value":" 8.849902"},{"name":"P94","value":"12.396708"},{"name":"Q95","value":"10.413637"},{"name":"R96","value":"10.822163"},{"name":"S97","value":" 9.011056"},{"name":"T98","value":" 9.651957"},{"name":"U99","value":" 7.455609"},{"name":"V100","value":"10.858132"}],"links":[{"source":"U47","target":"D4"},{"source":"S19","target":"L38"},{"source":"Z78","target":"K11"},{"source":"M39","target":"H86"},{"source":"T20","target":"B2"},{"source":"G59","target":"M13"},{"source":"O15","target":"D30"},{"source":"C29","target":"X76"},{"source":"V48","target":"I35"},{"source":"V48","target":"B54"},{"source":"S19","target":"E31"},{"source":"U73","target":"C29"},{"source":"R18","target":"H34"},{"source":"H86","target":"E31"},{"source":"F32","target":"E57"},{"source":"F58","target":"B54"},{"source":"I87","target":"V74"},{"source":"X24","target":"C3"},{"source":"G59","target":"G59"},{"source":"H60","target":"S45"},{"source":"A1","target":"I87"},{"source":"G85","target":"L90"},{"source":"N14","target":"I35"},{"source":"W23","target":"X50"},{"source":"T98","target":"J62"},{"source":"K89","target":"Z26"},{"source":"K37","target":"L12"},{"source":"Q43","target":"N14"},{"source":"X50","target":"M13"},{"source":"E5","target":"R70"},{"source":"W23","target":"F6"},{"source":"T46","target":"Y25"},{"source":"Q95","target":"O41"},{"source":"K89","target":"L38"},{"source":"D82","target":"O67"},{"source":"I87","target":"T72"},{"source":"Z52","target":"L38"},{"source":"Z78","target":"K63"},{"source":"S97","target":"V22"},{"source":"N40","target":"F58"},{"source":"U47","target":"O67"},{"source":"G59","target":"X24"},{"source":"D56","target":"P42"},{"source":"I35","target":"N92"},{"source":"Q95","target":"H60"},{"source":"K63","target":"N92"},{"source":"O15","target":"V22"},{"source":"Q43","target":"S97"},{"source":"J36","target":"U73"},{"source":"C81","target":"S45"},{"source":"D4","target":"U99"},{"source":"E5","target":"U21"},{"source":"W49","target":"K89"},{"source":"O67","target":"O41"},{"source":"Z78","target":"A79"},{"source":"B28","target":"I61"},{"source":"H86","target":"A27"},{"source":"N66","target":"F58"},{"source":"M39","target":"S71"},{"source":"H86","target":"M65"},{"source":"J10","target":"Q17"},{"source":"A79","target":"W75"},{"source":"C55","target":"D4"},{"source":"A53","target":"V22"},{"source":"R44","target":"U73"},{"source":"U99","target":"P16"},{"source":"I35","target":"R70"},{"source":"I61","target":"R18"},{"source":"P16","target":"F58"},{"source":"M91","target":"I61"},{"source":"A1","target":"P68"},{"source":"U73","target":"X24"},{"source":"X50","target":"Q69"},{"source":"O15","target":"N92"},{"source":"A79","target":"I35"},{"source":"Q69","target":"D4"},{"source":"X24","target":"T98"},{"source":"I35","target":"O15"},{"source":"O41","target":"I9"},{"source":"Y51","target":"V74"},{"source":"B80","target":"W49"},{"source":"J10","target":"W75"},{"source":"S71","target":"C3"},{"source":"X24","target":"R44"},{"source":"E57","target":"C3"},{"source":"J88","target":"E5"},{"source":"G85","target":"Y51"},{"source":"J10","target":"T46"},{"source":"U99","target":"R70"},{"source":"U47","target":"C81"},{"source":"F84","target":"F58"},{"source":"R70","target":"L64"},{"source":"R96","target":"Y77"},{"source":"R70","target":"T72"},{"source":"S71","target":"E31"},{"source":"X50","target":"O15"},{"source":"L12","target":"B80"},{"source":"C81","target":"S71"},{"source":"U21","target":"Q43"},{"source":"N92","target":"R44"},{"source":"Q69","target":"Q17"},{"source":"O15","target":"O67"},{"source":"P42","target":"N40"},{"source":"U47","target":"P94"},{"source":"E31","target":"U73"},{"source":"O67","target":"Z52"},{"source":"L64","target":"I87"},{"source":"V74","target":"L90"},{"source":"D4","target":"F6"},{"source":"P68","target":"H8"},{"source":"U99","target":"P94"},{"source":"K89","target":"N14"},{"source":"O93","target":"R96"},{"source":"Z52","target":"B80"},{"source":"S71","target":"E5"},{"source":"F58","target":"E31"},{"source":"B54","target":"M91"},{"source":"I35","target":"V100"},{"source":"J88","target":"E83"},{"source":"Z78","target":"V48"},{"source":"K11","target":"I87"},{"source":"C3","target":"J88"},{"source":"K89","target":"Z26"},{"source":"L90","target":"N40"},{"source":"A27","target":"N92"},{"source":"W49","target":"S71"},{"source":"E5","target":"U73"},{"source":"V100","target":"T72"},{"source":"Q69","target":"R44"},{"source":"R70","target":"Z26"},{"source":"L64","target":"R70"},{"source":"W49","target":"M39"},{"source":"X76","target":"N92"},{"source":"G59","target":"Z26"},{"source":"K89","target":"Y77"},{"source":"O93","target":"S19"},{"source":"F32","target":"R70"},{"source":"Y77","target":"J62"},{"source":"U21","target":"X24"},{"source":"P94","target":"W49"},{"source":"K37","target":"N92"},{"source":"Y51","target":"F84"},{"source":"H86","target":"R18"},{"source":"L64","target":"C81"},{"source":"L64","target":"L38"},{"source":"E57","target":"K89"},{"source":"M13","target":"Y77"},{"source":"I35","target":"D82"},{"source":"I61","target":"B28"},{"source":"D56","target":"P68"},{"source":"D30","target":"R18"},{"source":"C29","target":"T98"},{"source":"W49","target":"I87"},{"source":"O15","target":"L38"},{"source":"S45","target":"P16"},{"source":"V74","target":"N66"},{"source":"M13","target":"N66"},{"source":"R44","target":"P16"},{"source":"L38","target":"A1"},{"source":"R44","target":"I61"},{"source":"I9","target":"X24"},{"source":"C55","target":"F6"},{"source":"Z26","target":"A53"},{"source":"H8","target":"E5"},{"source":"K89","target":"C3"},{"source":"A27","target":"V48"},{"source":"D30","target":"Y77"},{"source":"M65","target":"X24"},{"source":"B54","target":"O41"},{"source":"L64","target":"X76"},{"source":"K89","target":"E83"},{"source":"M91","target":"N40"},{"source":"A27","target":"Y25"},{"source":"F6","target":"K37"},{"source":"W49","target":"D56"},{"source":"G59","target":"E31"},{"source":"S19","target":"K37"},{"source":"T72","target":"T98"},{"source":"R96","target":"Q69"},{"source":"J10","target":"U47"},{"source":"L38","target":"L12"},{"source":"E83","target":"P68"},{"source":"G59","target":"L12"},{"source":"L12","target":"H86"},{"source":"V48","target":"K11"},{"source":"S45","target":"R96"},{"source":"B80","target":"T98"},{"source":"C81","target":"N14"},{"source":"H34","target":"H60"},{"source":"K11","target":"C29"},{"source":"Y51","target":"M65"},{"source":"H86","target":"B28"},{"source":"C55","target":"B2"},{"source":"I61","target":"O41"},{"source":"V74","target":"D56"},{"source":"U73","target":"O67"},{"source":"S19","target":"S45"},{"source":"E57","target":"G85"},{"source":"L64","target":"V22"},{"source":"Y51","target":"H8"}],"modularity":{"modularity":{"resolution":5,"sort":true}}}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
