<div id="main" role="main">

# GeoJSON data

<div class="section level2">

## Introduction

You will find *215 maps* in the companion package
[echarts4r.maps](https://echarts4r-maps.john-coene.com/). However, since
you may need different kinds of maps i.e.: at the citiy or county level
that are not included in this package, you may need to get the detailed
map data from third-party source such as [gadm.org](https://gadm.org/).
This document shows how to make your own `GeoJSON` file which can be
used in `e_map_register`.

</div>

<div class="section level2">

## Packages

These are packages to help you building such maps

-   `sp`: spatial data management package.
-   `raster`: get spatial data from [gadm.org](https://gadm.org/).
-   `geojsonio`: convert spatial data into json format.
-   `rmapshaper`: simplify the spatial data.

<div id="cb1" class="sourceCode">

``` r
library(echarts4r)
library(sp)
#> Warning: package 'sp' was built under R version 4.5.2
library(raster)
#> Warning: package 'raster' was built under R version 4.5.2
library(geojsonio)
#> Warning: package 'geojsonio' was built under R version 4.5.2
#> Registered S3 method overwritten by 'geojsonsf':
#>   method        from   
#>   print.geojson geojson
#> 
#> Attaching package: 'geojsonio'
#> The following object is masked from 'package:base':
#> 
#>     pretty
library(rmapshaper)
#> Warning: package 'rmapshaper' was built under R version 4.5.2
```

</div>

</div>

<div class="section level2">

## Example

Get India map data from gadm website, this command need network
available, it will download the rds data to the current directory.

<div id="cb2" class="sourceCode">

``` r
india_sp <- geodata::gadm(country = "INDIA", level = 2)

india_sp <- methods::as(india_sp, "Spatial")
india_sp |> 
  head() |> 
  knitr::kable()
```

</div>

| GID_2     | GID_0 | COUNTRY | GID_1   | NAME_1              | NL_NAME_1 | NAME_2                   | VARNAME_2            | NL_NAME_2 | TYPE_2   | ENGTYPE_2 | CC_2 | HASC_2   |
|:----------|:------|:--------|:--------|:--------------------|:----------|:-------------------------|:---------------------|:----------|:---------|:----------|:-----|:---------|
| IND.1.1_1 | IND   | India   | IND.1_1 | Andaman and Nicobar | NA        | Nicobar Islands          | NA                   | NA        | District | District  | NA   | IN.AN.NI |
| IND.1.2_1 | IND   | India   | IND.1_1 | Andaman and Nicobar | NA        | North and Middle Andaman | NA                   | NA        | District | District  | NA   | IN.AN.NM |
| IND.1.3_1 | IND   | India   | IND.1_1 | Andaman and Nicobar | NA        | South Andaman            | NA                   | NA        | District | District  | NA   | IN.AN.SA |
| IND.2.1_1 | IND   | India   | IND.2_1 | Andhra Pradesh      | NA        | Anantapur                | Anantpur, Ananthapur | NA        | District | District  | NA   | IN.AD.AN |
| IND.2.2_1 | IND   | India   | IND.2_1 | Andhra Pradesh      | NA        | Chittoor                 | Chitoor\|Chittor     | NA        | District | District  | NA   | IN.AD.CH |
| IND.2.3_1 | IND   | India   | IND.2_1 | Andhra Pradesh      | NA        | East Godavari            | NA                   | NA        | District | District  | NA   | IN.AD.EG |

Note that you can then combine maps with `raster::union(map1, map2)` or
with the `em_maps` function from the
[echarts4r.maps](https://echarts4r-maps.john-coene.com) package. Then
convert the `SpatialPolygonsDataFrame` into `GeoJSON` with `geojsonio`:
*this will take a long time as the map is very detailed*.

<div id="cb3" class="sourceCode">

``` r
india_json <- geojsonio::geojson_list(india_sp)

print(object.size(india_json), units = "Mb")
#> 61.2 Mb
```

</div>

Therefore we can simplify the map to make it smaller.

<div id="cb4" class="sourceCode">

``` r
india_small <- rmapshaper::ms_simplify(india_sp, keep = 0.05) 
india_json_small <- geojsonio::geojson_list(india_small)
print(object.size(india_json_small), units = "Mb") 
#> 7.1 Mb
```

</div>

The function `geodata::gadm` gives each polygon a `NAME_*` property
(where `*` is the `level` specified) rather than just `name`. The
tooltip will not display properly unless we use the `nameMap` to point
to that property, by default echarts expects the `name` property.

Now we can use the `GeoJSON` with `e_map_register`.

<div id="cb5" class="sourceCode">

``` r
# plot 
e_charts() |>
  e_map_register("India", india_json_small) |>
  e_map(map = "India", nameProperty = "NAME_2")
```

</div>

<div id="htmlwidget-ac96cb3ee4656e2e9ec3"
class="echarts4r html-widget html-fill-item"
style="width:100%;height:500px;">

</div>

</div>

</div>
