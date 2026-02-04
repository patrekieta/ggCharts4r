<div id="main" class="col-md-9" role="main">

# Locale

<div class="ref-description section level2">

Change the locale to auto-translate days of the week, etc.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_locale(e, locale)

e_locale_manual(e, locale, path)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   locale:

    Locale to set to.

-   path:

    Path to the local file to use.

</div>

<div class="section level2">

## Details

The "manual" function expects a file to use for translations. You can
browse the \`.js\` files
\[here\](https://github.com/apache/echarts/tree/master/i18n) to have an
idea of what they should look like.

</div>

<div class="section level2">

## Locales

\- AR - CS - DE - EN - ES - FA - FI - FR - HU - IT - JA - KO - NL - PL -
PT (brazil) - RO - RU - SI - SV - TH - TR - UK - VI - ZH

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
# top right corner zoom is in
# French
cars |>
 e_charts(speed) |>
 e_scatter(dist) |>
 e_datazoom() |>
 e_locale("FR")

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"type":"value"}],"legend":{"data":["dist"]},"series":[{"data":[{"value":[4,2]},{"value":[4,10]},{"value":[7,4]},{"value":[7,22]},{"value":[8,16]},{"value":[9,10]},{"value":[10,18]},{"value":[10,26]},{"value":[10,34]},{"value":[11,17]},{"value":[11,28]},{"value":[12,14]},{"value":[12,20]},{"value":[12,24]},{"value":[12,28]},{"value":[13,26]},{"value":[13,34]},{"value":[13,34]},{"value":[13,46]},{"value":[14,26]},{"value":[14,36]},{"value":[14,60]},{"value":[14,80]},{"value":[15,20]},{"value":[15,26]},{"value":[15,54]},{"value":[16,32]},{"value":[16,40]},{"value":[17,32]},{"value":[17,40]},{"value":[17,50]},{"value":[18,42]},{"value":[18,56]},{"value":[18,76]},{"value":[18,84]},{"value":[19,36]},{"value":[19,46]},{"value":[19,68]},{"value":[20,32]},{"value":[20,48]},{"value":[20,52]},{"value":[20,56]},{"value":[20,64]},{"value":[22,66]},{"value":[23,54]},{"value":[24,70]},{"value":[24,92]},{"value":[24,93]},{"value":[24,120]},{"value":[25,85]}],"name":"dist","type":"scatter","symbol":null,"coordinateSystem":"cartesian2d","yAxisIndex":0,"xAxisIndex":0,"symbolSize":3}],"dataZoom":[[]],"toolbox":{"feature":{"dataZoom":[]}}},"dispose":true,"mainOpts":{"locale":"FR"}},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
