<div id="main" class="col-md-9" role="main">

# Geo 3D

<div class="ref-description section level2">

Initialise geo 3D.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_geo_3d(e, serie, color, type = "world", rm_x = TRUE, rm_y = TRUE, ...)

e_geo_3d_(
  e,
  serie = NULL,
  color = NULL,
  type = "world",
  rm_x = TRUE,
  rm_y = TRUE,
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

    Column name of serie to plot.

-   color:

    Color.

-   type:

    Map type.

-   rm_x, rm_y:

    Whether to remove x and y axis, defaults to `TRUE`.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

`e_country_names`, [Additional
arguments](https://echarts.apache.org/en/option-gl.html#geo3D)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
choropleth <- data.frame(
  countries = c(
    "France",
    "Brazil",
    "China",
    "Russia",
    "Canada",
    "India",
    "United States",
    "Argentina",
    "Australia"
  ),
  height = runif(9, 1, 5),
  color = c(
    "#F7FBFF",
    "#DEEBF7",
    "#C6DBEF",
    "#9ECAE1",
    "#6BAED6",
    "#4292C6",
    "#2171B5",
    "#08519C",
    "#08306B"
  )
)

choropleth |>
  e_charts(countries) |>
  e_geo_3d(height, color)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"geo3D":{"map":"world","regions":[{"name":"France","height":"1.286625","itemStyle":{"color":"#F7FBFF"}},{"name":"Brazil","height":"1.108587","itemStyle":{"color":"#DEEBF7"}},{"name":"China","height":"3.615370","itemStyle":{"color":"#C6DBEF"}},{"name":"Russia","height":"3.727047","itemStyle":{"color":"#9ECAE1"}},{"name":"Canada","height":"1.137167","itemStyle":{"color":"#6BAED6"}},{"name":"India","height":"1.544305","itemStyle":{"color":"#4292C6"}},{"name":"United States","height":"3.293917","itemStyle":{"color":"#2171B5"}},{"name":"Argentina","height":"3.293686","itemStyle":{"color":"#08519C"}},{"name":"Australia","height":"2.505256","itemStyle":{"color":"#08306B"}}]}},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
