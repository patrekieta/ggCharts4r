<div id="main" class="col-md-9" role="main">

# echarts4r

<div class="section level1">

[![R-CMD-check](https://github.com/JohnCoene/echarts4r/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/JohnCoene/echarts4r/actions/workflows/R-CMD-check.yaml)
[![Lifecycle:
stable](https://img.shields.io/badge/lifecycle-stable-brightgreen.svg)](https://www.tidyverse.org/lifecycle/#stable)
[![GitHub closed
issues](https://img.shields.io/github/issues-closed/JohnCoene/echarts4r.svg)](https://github.com/JohnCoene/echarts4r/issues)
[![code-size](https://img.shields.io/github/languages/code-size/JohnCoene/echarts4r.svg)](https://github.com/JohnCoene/echarts4r)
[![activity](https://img.shields.io/github/last-commit/JohnCoene/echarts4r.svg)](https://github.com/JohnCoene/echarts4r)
[![Coveralls test
coverage](https://coveralls.io/repos/github/JohnCoene/echarts4r/badge.svg)](https://coveralls.io/github/JohnCoene/echarts4r)

<div class="row">

<div class="col-md-4">

![](reference/figures/logo.png)

</div>

<div class="col-md-8">

Interactive visualisations for R via [Apache
ECharts](https://echarts.apache.org/)

[Get Started](http://echarts4r.john-coene.com/articles/get_started.md)
[Reference](http://echarts4r.john-coene.com/reference/)
[Timeline](http://echarts4r.john-coene.com/articles/timeline) [Shiny
Demo](http://shiny.john-coene.com/echarts4rShiny)

</div>

</div>

  
  

<div class="thumbnail" style="text-align:center;">

<div class="caption">

#### Version 6

Explore new features available on version 6 of echarts.js!

  
[Explore](http://echarts4r.john-coene.com/articles/v6)

</div>

</div>

<div class="section level2">

## Introduction

Thanks to [Sharon Machlis](https://twitter.com/sharon000) there is an
amazing video and
[article](https://www.infoworld.com/article/3607068/plot-in-r-with-echarts4r.html)
introducing echarts4r.

  

<div class="panel panel-default">

<div class="panel-body">

You can learn how to build such R packages for interactive
visualisations with the book [JavaScript for
R](https://javascript-for-r.com/).

</div>

</div>

</div>

<div class="section level2">

## Installation

The package is available on
[CRAN](https://CRAN.R-project.org/package=echarts4r). The full
installation can be obtained with:

<div id="cb1" class="sourceCode">

``` r
install.packages("echarts4r")
```

</div>

However, if you only want a *lite* version you can simply do, this is
useful for a lighter version that installs faster if you do not want to
use any of the geospatial features of the package:

<div id="cb2" class="sourceCode">

``` r
install.packages("echarts4r", dependencies = c("Depends", "Imports"))
```

</div>

You can also install the *unstable* development version of echarts4r
with `remotes` from Github, see
[changes](http://echarts4r.john-coene.com/news/index.md).

<div id="cb3" class="sourceCode">

``` r
# install.packages("remotes")
remotes::install_github("JohnCoene/echarts4r")
```

</div>

如果您位于中国，请安装:

<div id="cb4" class="sourceCode">

``` r
# install.packages("remotes")
remotes::install_git("https://gitee.com/JohnCoene/echarts4r")
```

</div>

</div>

<div class="section level2">

## Companions

Companion packages to make `echarts4r` even better. You can install and
load the whole suite with:

<div id="cb5" class="sourceCode">

``` r
remotes::install_github("JohnCoene/echarts4r.suite")
```

</div>

<div class="row">

<div class="col-md-6">

<div class="thumbnail" style="text-align:center;">

<div class="caption">

#### echarts4r.assets

Icons, and assets for globes, add visually interesting globe overlays
and background.

``` r
remotes::install_github('JohnCoene/echarts4r.assets')
```

[Website](https://echarts4r-assets.john-coene.com/)
[Github](https://github.com/JohnCoene/echarts4r.assets)

</div>

</div>

</div>

<div class="col-md-6">

<div class="thumbnail" style="text-align:center;">

<div class="caption">

#### echarts4r.maps

A collection of 215 country maps to use with geo-spatial visualisations.

``` r
remotes::install_github('JohnCoene/echarts4r.maps')
```

[Website](https://echarts4r-maps.john-coene.com/)
[Github](https://github.com/JohnCoene/echarts4r.maps)

</div>

</div>

</div>

</div>

</div>

</div>

</div>
