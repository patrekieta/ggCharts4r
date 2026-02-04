<div id="main" class="col-md-9" role="main">

# Dimensions

<div class="ref-description section level2">

Sets the dimensions of the chart \_internally.\_ This will only affect
the dimensions of the chart within its parent container. Use the
\`height\` and \`width\` arguments of \[e_charts\] if you want to change
the dimensions of said parent (recommended).

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_dims(e, height = "auto", width = "auto")
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   height, width:

    Dimensions in pixels, percentage or string.

</div>

</div>
