<div id="main" class="col-md-9" role="main">

# Wordcloud

<div class="ref-description section level2">

Draw a wordcloud.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_cloud(e, word, freq, color, rm_x = TRUE, rm_y = TRUE, ...)

e_cloud_(e, word, freq, color = NULL, rm_x = TRUE, rm_y = TRUE, ...)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   word, freq:

    Terms and their frequencies.

-   color:

    Word color.

-   rm_x, rm_y:

    Whether to remove x and y axis, defaults to `TRUE`.

-   ...:

    Any other option to pass, check See Also section.

</div>

<div class="section level2">

## See also

<div class="dont-index">

[official documentation](https://github.com/ecomfe/echarts-wordcloud)

</div>

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
words <- function(n = 5000) {
  a <- do.call(paste0, replicate(5, sample(LETTERS, n, TRUE), FALSE))
  paste0(a, sprintf("%04d", sample(9999, n, TRUE)), sample(LETTERS, n, TRUE))
}

tf <- data.frame(
  terms = words(100),
  freq = rnorm(100, 55, 10)
) |>
  dplyr::arrange(-freq)

tf |>
  e_color_range(freq, color) |>
  e_charts() |>
  e_cloud(terms, freq, color, shape = "circle", sizeRange = c(3, 15))

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"series":[{"type":"wordCloud","data":[{"value":78.15849301450461,"name":"CSXSE1473V","textStyle":{"color":"#F6EFA6"}},{"value":76.38995234899991,"name":"HQSQM6567A","textStyle":{"color":"#F4E7A2"}},{"value":76.16530742830059,"name":"RYUXZ2124I","textStyle":{"color":"#F4E6A2"}},{"value":74.60755930712961,"name":"OYNUM4609K","textStyle":{"color":"#F3DF9E"}},{"value":74.26606504714965,"name":"PPBMN0192A","textStyle":{"color":"#F2DD9E"}},{"value":71.36540567141225,"name":"QWFUR4928N","textStyle":{"color":"#EFD097"}},{"value":70.39376495155655,"name":"ERCJS0458X","textStyle":{"color":"#EECC95"}},{"value":70.26737997181787,"name":"DJAKA4662T","textStyle":{"color":"#EECC95"}},{"value":70.16556529445093,"name":"CWWSG1954N","textStyle":{"color":"#EECB95"}},{"value":69.62425734368152,"name":"QGWGE6230H","textStyle":{"color":"#EDC994"}},{"value":69.54354815506861,"name":"LWCZH9743W","textStyle":{"color":"#EDC893"}},{"value":69.30290161460823,"name":"HOVGR5416H","textStyle":{"color":"#EDC793"}},{"value":69.28358850255424,"name":"UQMLT7209K","textStyle":{"color":"#EDC793"}},{"value":68.19700102947753,"name":"PYXXE1895E","textStyle":{"color":"#ECC291"}},{"value":67.23164016185305,"name":"NVHJR6599L","textStyle":{"color":"#EABE8F"}},{"value":66.58752180474988,"name":"FXQKA3351Z","textStyle":{"color":"#EABB8D"}},{"value":66.37045938520943,"name":"XQGBJ6600A","textStyle":{"color":"#E9BA8D"}},{"value":66.23909321821517,"name":"VUIFW7712Z","textStyle":{"color":"#E9BA8C"}},{"value":65.74657121924588,"name":"ENNUJ6799X","textStyle":{"color":"#E9B78B"}},{"value":65.59842218849339,"name":"YCXYJ8781A","textStyle":{"color":"#E8B78B"}},{"value":65.13571835374846,"name":"TNTGB6963R","textStyle":{"color":"#E8B58A"}},{"value":65.12532538218048,"name":"FYVQX8690S","textStyle":{"color":"#E8B58A"}},{"value":63.62710826554081,"name":"XEZSQ0239K","textStyle":{"color":"#E6AE87"}},{"value":63.52173584584716,"name":"NRAFB4660Z","textStyle":{"color":"#E6AD87"}},{"value":63.40522625855864,"name":"NJSUF3788C","textStyle":{"color":"#E6AD87"}},{"value":63.27869297615099,"name":"JIUNP3635I","textStyle":{"color":"#E5AC86"}},{"value":62.7662539998112,"name":"QWVJT8746Y","textStyle":{"color":"#E5AA85"}},{"value":62.64001921059872,"name":"SDIJM2546B","textStyle":{"color":"#E5A985"}},{"value":62.62012389019607,"name":"HUZHN0662H","textStyle":{"color":"#E5A985"}},{"value":62.22232422667251,"name":"OAWPP4871I","textStyle":{"color":"#E4A884"}},{"value":62.02411712708128,"name":"WFNUE8012K","textStyle":{"color":"#E4A784"}},{"value":61.58526506382546,"name":"WJDQW0953R","textStyle":{"color":"#E3A583"}},{"value":61.5505667154527,"name":"TABJE1660D","textStyle":{"color":"#E3A583"}},{"value":61.45142724550194,"name":"WGNXZ0711K","textStyle":{"color":"#E3A482"}},{"value":61.23653457997048,"name":"JLQEZ2999G","textStyle":{"color":"#E3A382"}},{"value":61.06232667538287,"name":"BIDHX8378D","textStyle":{"color":"#E2A282"}},{"value":60.7440044408287,"name":"VJXHN0391P","textStyle":{"color":"#E2A181"}},{"value":60.60050140634962,"name":"QYVYT6102V","textStyle":{"color":"#E2A081"}},{"value":60.2272117886162,"name":"RCYDH4825G","textStyle":{"color":"#E19F80"}},{"value":60.07828230589266,"name":"JLEKJ3034W","textStyle":{"color":"#E19E80"}},{"value":60.05599115347081,"name":"DPLNZ8651V","textStyle":{"color":"#E19E80"}},{"value":59.7380131019073,"name":"NRYZB4311U","textStyle":{"color":"#E19C7F"}},{"value":59.57817316762233,"name":"GDRSB1486V","textStyle":{"color":"#E09C7F"}},{"value":58.7769313348623,"name":"UZCHA1944Z","textStyle":{"color":"#DF987D"}},{"value":57.95561895272746,"name":"HYYKA1951N","textStyle":{"color":"#DE947B"}},{"value":57.47350267997651,"name":"MOWVD0774I","textStyle":{"color":"#DD927A"}},{"value":57.38889683387322,"name":"XHLVF3929L","textStyle":{"color":"#DD927A"}},{"value":57.1799654886131,"name":"QKVGQ8173I","textStyle":{"color":"#DD917A"}},{"value":56.89759677003288,"name":"PKOQS7358L","textStyle":{"color":"#DC9079"}},{"value":56.18178060520712,"name":"QLYZZ3038C","textStyle":{"color":"#DB8C78"}},{"value":56.12995340582098,"name":"SVWKR7454I","textStyle":{"color":"#DB8C77"}},{"value":55.91607576535964,"name":"KBSMH3359T","textStyle":{"color":"#DB8B77"}},{"value":55.3168816397411,"name":"EPMXL8249P","textStyle":{"color":"#DA8876"}},{"value":54.94553289947044,"name":"QNRES3261P","textStyle":{"color":"#DA8775"}},{"value":54.23207041475527,"name":"RVDFQ7607X","textStyle":{"color":"#D88374"}},{"value":54.22789137552483,"name":"UPJBE9234Z","textStyle":{"color":"#D88374"}},{"value":54.1848914892975,"name":"HWKSX3351Y","textStyle":{"color":"#D88373"}},{"value":53.76866341939589,"name":"JLFFJ6581F","textStyle":{"color":"#D88273"}},{"value":53.58602547317883,"name":"CYAYI6693Q","textStyle":{"color":"#D88172"}},{"value":53.57261607255158,"name":"JNASB2777J","textStyle":{"color":"#D88172"}},{"value":53.50710299882288,"name":"ZFDFI7601T","textStyle":{"color":"#D88172"}},{"value":53.49559644680315,"name":"JVAJR9251A","textStyle":{"color":"#D88172"}},{"value":53.08438058988433,"name":"WFEHU5752B","textStyle":{"color":"#D78072"}},{"value":53.03662775619896,"name":"WOLMJ1180X","textStyle":{"color":"#D78071"}},{"value":52.63434334929794,"name":"JVHZL6034V","textStyle":{"color":"#D77F71"}},{"value":51.8552183355044,"name":"CAYVD7968P","textStyle":{"color":"#D67D70"}},{"value":51.76656544010935,"name":"ZYBNJ7692O","textStyle":{"color":"#D67D6F"}},{"value":51.31238391679513,"name":"YIOMZ2800Q","textStyle":{"color":"#D67C6F"}},{"value":51.30208064507134,"name":"DPVAG0769R","textStyle":{"color":"#D67C6F"}},{"value":51.18401123226504,"name":"DEFSX8630Y","textStyle":{"color":"#D57B6E"}},{"value":51.05287956315304,"name":"GPOJT7974A","textStyle":{"color":"#D57B6E"}},{"value":50.1595739275641,"name":"DSSNG0315A","textStyle":{"color":"#D4796D"}},{"value":50.04620989542276,"name":"JFWML9855X","textStyle":{"color":"#D4796D"}},{"value":50.04198249112882,"name":"MZUXE2179C","textStyle":{"color":"#D4796D"}},{"value":49.84030626299101,"name":"UOXVL3917S","textStyle":{"color":"#D4786C"}},{"value":49.52282528022572,"name":"KXTIU9289L","textStyle":{"color":"#D4776C"}},{"value":48.65642188228362,"name":"VWJPX0062O","textStyle":{"color":"#D3756A"}},{"value":48.23422173201202,"name":"EESQK5653O","textStyle":{"color":"#D3746A"}},{"value":47.99331327014117,"name":"QAIKA5561Q","textStyle":{"color":"#D27469"}},{"value":47.72005632395989,"name":"DQIEY5316O","textStyle":{"color":"#D27369"}},{"value":47.61737638964851,"name":"GJFIL8866D","textStyle":{"color":"#D27369"}},{"value":47.35779977388535,"name":"NBJXW8461R","textStyle":{"color":"#D27268"}},{"value":46.93982284802495,"name":"GVBVL5976J","textStyle":{"color":"#D17167"}},{"value":46.74479488843058,"name":"TRPOI8093W","textStyle":{"color":"#D17067"}},{"value":45.97897632207801,"name":"SSSKK6969R","textStyle":{"color":"#D06F66"}},{"value":45.70278195429547,"name":"SVSRR1735E","textStyle":{"color":"#D06E65"}},{"value":45.11751047275926,"name":"CDEBY8154D","textStyle":{"color":"#CF6C64"}},{"value":43.94783256467942,"name":"SEQPN4573L","textStyle":{"color":"#CE6A63"}},{"value":42.96008650037564,"name":"FRRPE8309T","textStyle":{"color":"#CD6761"}},{"value":41.99469069084387,"name":"IRTNY2753K","textStyle":{"color":"#CC655F"}},{"value":41.98715994953304,"name":"MRSUU9144Z","textStyle":{"color":"#CC655F"}},{"value":41.31887189558029,"name":"OYGAG6007C","textStyle":{"color":"#CC635E"}},{"value":40.38831414519948,"name":"JPBJB1877G","textStyle":{"color":"#CB615D"}},{"value":39.45434167038693,"name":"MFWQF6313Y","textStyle":{"color":"#CA5E5B"}},{"value":38.63207881042331,"name":"ULUCL0621T","textStyle":{"color":"#C95C5A"}},{"value":38.18426973970691,"name":"MGGEH4522P","textStyle":{"color":"#C85B59"}},{"value":36.86181578008797,"name":"MPERM6195T","textStyle":{"color":"#C75757"}},{"value":36.04030819074579,"name":"MKGIJ9804T","textStyle":{"color":"#C65556"}},{"value":35.16952168903823,"name":"TSOTX7992Q","textStyle":{"color":"#C55354"}},{"value":29.72247072391995,"name":"DJKUG9997W","textStyle":{"color":"#BF444C"}}],"shape":"circle","sizeRange":[3,15]}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
