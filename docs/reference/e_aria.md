<div id="main" class="col-md-9" role="main">

# Aria

<div class="ref-description section level2">

W3C defined the Accessible Rich Internet Applications Suite (WAI-ARIA)
to make Web content and Web applications more accessible to the
disabled. From ECharts 4.0, echarts4r supports ARIA by generating
description for charts automatically.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_aria(e, enabled = TRUE, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   enabled:

    Whether to enable aria helper text.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## Details

There should be an aria-label attribute on the chart DOM, which can help
the disabled understand the content of charts with the help of certain
devices.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[official documentation](https://echarts.apache.org/en/option.html#aria)

</div>

</div>

</div>
