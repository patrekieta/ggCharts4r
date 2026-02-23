<div id="main" class="col-md-9" role="main">

# Axis Jitter

<div class="ref-description section level2">

helper function for generating jitter between points in a scatter plot.
This is only applicable to e_scatter().

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_jitter(e, axis = "x", jitter = 20, jitterOverlap = FALSE, jitterMargin = 5)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   axis:

    Axis to apply formatter to. Supports x and y axis

-   jitter:

    Pixel units indicating the amount of random noise to add to each
    data point position.

-   jitterOverlap:

    Boolean allowing overlap between data points. If false, overlap will
    not be allowed. For some cases, scatters may still overlap if there
    is no reasonable way to avoid.

-   jitterMargin:

    When you have jitter and jiterOverlap is FALSE, this is the minimum
    distance in pixels between two data points.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[Additional
arguments](https://echarts.apache.org/en/option.html#yAxis.jitter)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
df <- data.frame(
value = c(rnorm(50, mean = 5, sd = 1),
         rnorm(50, mean = 10, sd = 1),
         rnorm(50, mean = 15, sd = 1)),
         group = rep(c("Group A", "Group B", "Group C"), each = 50)
          )

df |> e_charts(group) |> e_scatter(value) |> e_jitter()

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true}],"xAxis":[{"data":["Group A","Group B","Group C"],"type":"category","boundaryGap":true,"jitter":20,"jitterOverlap":false,"jitterMargin":5}],"legend":{"data":["value"]},"series":[{"data":[{"value":["Group A"," 4.980792"]},{"value":["Group A"," 4.753274"]},{"value":["Group A"," 4.085367"]},{"value":["Group A"," 3.365296"]},{"value":["Group A"," 5.483507"]},{"value":["Group A"," 3.867878"]},{"value":["Group A"," 6.467987"]},{"value":["Group A"," 3.914459"]},{"value":["Group A"," 6.936473"]},{"value":["Group A"," 3.737384"]},{"value":["Group A"," 5.820631"]},{"value":["Group A"," 4.541324"]},{"value":["Group A"," 5.640518"]},{"value":["Group A"," 5.803171"]},{"value":["Group A"," 5.924872"]},{"value":["Group A"," 5.973124"]},{"value":["Group A"," 5.884231"]},{"value":["Group A"," 6.001913"]},{"value":["Group A"," 4.728075"]},{"value":["Group A"," 5.007279"]},{"value":["Group A"," 4.655127"]},{"value":["Group A"," 7.678972"]},{"value":["Group A"," 6.178099"]},{"value":["Group A"," 3.507570"]},{"value":["Group A"," 3.947804"]},{"value":["Group A"," 4.958333"]},{"value":["Group A"," 5.091641"]},{"value":["Group A"," 3.843153"]},{"value":["Group A"," 5.231481"]},{"value":["Group A"," 6.080537"]},{"value":["Group A"," 4.711918"]},{"value":["Group A"," 5.739446"]},{"value":["Group A"," 5.515363"]},{"value":["Group A"," 5.718761"]},{"value":["Group A"," 4.202638"]},{"value":["Group A"," 5.577435"]},{"value":["Group A"," 4.870181"]},{"value":["Group A"," 4.564488"]},{"value":["Group A"," 5.196704"]},{"value":["Group A"," 4.848295"]},{"value":["Group A"," 5.507201"]},{"value":["Group A"," 5.207262"]},{"value":["Group A"," 6.185447"]},{"value":["Group A"," 3.867294"]},{"value":["Group A"," 6.369587"]},{"value":["Group A"," 5.860264"]},{"value":["Group A"," 4.610182"]},{"value":["Group A"," 5.676682"]},{"value":["Group A"," 7.005637"]},{"value":["Group A"," 6.231579"]},{"value":["Group B"," 9.628291"]},{"value":["Group B","11.217233"]},{"value":["Group B"," 9.406835"]},{"value":["Group B"," 8.683997"]},{"value":["Group B"," 9.876741"]},{"value":["Group B","10.023648"]},{"value":["Group B"," 8.028808"]},{"value":["Group B","10.671837"]},{"value":["Group B","10.441225"]},{"value":["Group B","10.125086"]},{"value":["Group B","11.698746"]},{"value":["Group B","11.545995"]},{"value":["Group B","11.003872"]},{"value":["Group B","10.951927"]},{"value":["Group B"," 9.791081"]},{"value":["Group B","12.195649"]},{"value":["Group B","11.236540"]},{"value":["Group B"," 9.623718"]},{"value":["Group B"," 9.629521"]},{"value":["Group B","10.117668"]},{"value":["Group B","10.917012"]},{"value":["Group B"," 9.014625"]},{"value":["Group B","10.672330"]},{"value":["Group B","10.044896"]},{"value":["Group B","10.099403"]},{"value":["Group B","10.088771"]},{"value":["Group B"," 9.322110"]},{"value":["Group B","10.378883"]},{"value":["Group B","10.753935"]},{"value":["Group B"," 9.983148"]},{"value":["Group B","10.618046"]},{"value":["Group B","11.241696"]},{"value":["Group B"," 8.974727"]},{"value":["Group B"," 8.630258"]},{"value":["Group B"," 9.841296"]},{"value":["Group B"," 9.972434"]},{"value":["Group B","10.305481"]},{"value":["Group B","10.427279"]},{"value":["Group B","10.706130"]},{"value":["Group B","10.280998"]},{"value":["Group B"," 9.908202"]},{"value":["Group B","13.495025"]},{"value":["Group B","10.168048"]},{"value":["Group B","10.109086"]},{"value":["Group B"," 9.622194"]},{"value":["Group B"," 9.522415"]},{"value":["Group B","10.225441"]},{"value":["Group B"," 8.928354"]},{"value":["Group B"," 8.502014"]},{"value":["Group B","10.241261"]},{"value":["Group C","13.337051"]},{"value":["Group C","16.477793"]},{"value":["Group C","13.812484"]},{"value":["Group C","15.481595"]},{"value":["Group C","16.963298"]},{"value":["Group C","13.966568"]},{"value":["Group C","16.233458"]},{"value":["Group C","14.928763"]},{"value":["Group C","14.666386"]},{"value":["Group C","15.243681"]},{"value":["Group C","14.424696"]},{"value":["Group C","14.306534"]},{"value":["Group C","13.371277"]},{"value":["Group C","15.617877"]},{"value":["Group C","15.217225"]},{"value":["Group C","14.502568"]},{"value":["Group C","14.630990"]},{"value":["Group C","14.307476"]},{"value":["Group C","17.227895"]},{"value":["Group C","15.027544"]},{"value":["Group C","15.653096"]},{"value":["Group C","14.500280"]},{"value":["Group C","14.835835"]},{"value":["Group C","16.184923"]},{"value":["Group C","15.859388"]},{"value":["Group C","15.207790"]},{"value":["Group C","16.327257"]},{"value":["Group C","16.211692"]},{"value":["Group C","14.985063"]},{"value":["Group C","15.784285"]},{"value":["Group C","13.906632"]},{"value":["Group C","16.192498"]},{"value":["Group C","13.417150"]},{"value":["Group C","14.623423"]},{"value":["Group C","14.124308"]},{"value":["Group C","14.968651"]},{"value":["Group C","16.349976"]},{"value":["Group C","13.345363"]},{"value":["Group C","13.932146"]},{"value":["Group C","13.338767"]},{"value":["Group C","14.875828"]},{"value":["Group C","14.679381"]},{"value":["Group C","13.282127"]},{"value":["Group C","15.130683"]},{"value":["Group C","14.347936"]},{"value":["Group C","15.777683"]},{"value":["Group C","16.240743"]},{"value":["Group C","14.977015"]},{"value":["Group C","14.598260"]},{"value":["Group C","15.135133"]}],"name":"value","type":"scatter","symbol":null,"coordinateSystem":"cartesian2d","yAxisIndex":0,"xAxisIndex":0,"symbolSize":3}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
