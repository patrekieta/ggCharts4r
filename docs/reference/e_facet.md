<div id="main" class="col-md-9" role="main">

# Facet

<div class="ref-description section level2">

Create facets for multiple plots.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_facet(
  e,
  rows = NULL,
  cols = NULL,
  legend_pos = "top",
  legend_space = 10,
  margin_trbl = c(t = 2, r = 2, b = 5, l = 2),
  h_panel_space = NULL,
  v_panel_space = NULL
)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   rows, cols:

    Number of rows and columns. If both are \`NULL\` the number of rows
    and columns will be determined automatically.

-   legend_pos:

    Position of the legend. One of "top", "right", "bottom", "left".
    Determines to which side the \`legend_space\` argument applies.

-   legend_space:

    Space between legend and plot area. The entered number will be used
    as percentage.

-   margin_trbl:

    Adjusts the size of the outside margin around the plotting area.
    Default is \`c(t = 2, r = 2, b = 5, l = 2)\`. Numbers are used as
    percentage of total plotting area. To change only e.g. two sides
    \`c("r" = 8, "l" = 8)\` could be used, other sides will use
    defaults.

-   h_panel_space, v_panel_space:

    Horizontal and vertical spacing between the individual grid
    elements. Expects numeric input, which will be used as percentage of
    total plotting area. Default \`NULL\` will automatically add some
    panel spacing for low dimensional grids.

</div>

<div class="section level2">

## Details

Each serie, i.e.: `e_bar` will be plotted against a facet.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
group_size <- 20
n_groups <- 13
df <- data.frame("day" = rep(1:group_size, times=n_groups),
                 "temperature" = runif(group_size * n_groups, 10, 40),
                 "location" = rep(LETTERS[1:n_groups], each=group_size))

df |>
  group_by(location) |>
  e_charts(day) |>
  e_line(temperature) |>
  e_facet(rows = 4, cols=4, legend_pos = "top", legend_space = 12)

{"x":{"theme":"","tl":false,"draw":true,"renderer":"canvas","events":[],"buttons":[],"opts":{"yAxis":[{"show":true,"gridIndex":0},{"show":true,"gridIndex":1},{"show":true,"gridIndex":2},{"show":true,"gridIndex":3},{"show":true,"gridIndex":4},{"show":true,"gridIndex":5},{"show":true,"gridIndex":6},{"show":true,"gridIndex":7},{"show":true,"gridIndex":8},{"show":true,"gridIndex":9},{"show":true,"gridIndex":10},{"show":true,"gridIndex":11},{"show":true,"gridIndex":12}],"xAxis":[{"type":"value","gridIndex":0},{"type":"value","gridIndex":1},{"type":"value","gridIndex":2},{"type":"value","gridIndex":3},{"type":"value","gridIndex":4},{"type":"value","gridIndex":5},{"type":"value","gridIndex":6},{"type":"value","gridIndex":7},{"type":"value","gridIndex":8},{"type":"value","gridIndex":9},{"type":"value","gridIndex":10},{"type":"value","gridIndex":11},{"type":"value","gridIndex":12}],"legend":{"data":["A","B","C","D","E","F","G","H","I","J","K","L","M"]},"series":[{"data":[{"value":[1,22.69848759053275]},{"value":[2,10.42492271168157]},{"value":[3,29.59193035727367]},{"value":[4,38.24710458982736]},{"value":[5,24.60241358028725]},{"value":[6,24.57949170144275]},{"value":[7,18.95496854092926]},{"value":[8,38.18955352762714]},{"value":[9,39.96799923479557]},{"value":[10,17.85599790280685]},{"value":[11,12.31355614261702]},{"value":[12,14.86576966941357]},{"value":[13,28.88694797642529]},{"value":[14,10.52860125899315]},{"value":[15,11.17744263028726]},{"value":[16,24.47895033983514]},{"value":[17,14.64169699233025]},{"value":[18,34.51452808687463]},{"value":[19,35.50299767171964]},{"value":[20,10.45221270760521]}],"yAxisIndex":0,"xAxisIndex":0,"name":"A","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,25.41536253644153]},{"value":[2,15.3828228241764]},{"value":[3,11.35485923150554]},{"value":[4,26.22685116250068]},{"value":[5,20.62514831312001]},{"value":[6,25.93061953317374]},{"value":[7,13.12391068320721]},{"value":[8,18.75108233653009]},{"value":[9,18.14676118548959]},{"value":[10,39.59074386162683]},{"value":[11,12.56635919678956]},{"value":[12,28.71403175173327]},{"value":[13,15.19163444172591]},{"value":[14,25.38492257939652]},{"value":[15,33.10920520918444]},{"value":[16,26.85781276784837]},{"value":[17,25.26440967107192]},{"value":[18,11.5475012245588]},{"value":[19,31.25371109927073]},{"value":[20,29.84897248912603]}],"yAxisIndex":1,"xAxisIndex":1,"name":"B","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,12.65188280725852]},{"value":[2,10.34399112686515]},{"value":[3,17.7890836680308]},{"value":[4,13.07025248417631]},{"value":[5,35.57934769429266]},{"value":[6,32.11532003479078]},{"value":[7,21.21868461603299]},{"value":[8,28.3074565581046]},{"value":[9,25.41074053850025]},{"value":[10,35.9306134050712]},{"value":[11,35.68971860455349]},{"value":[12,32.13322405237705]},{"value":[13,11.68562442064285]},{"value":[14,33.98216797038913]},{"value":[15,11.69974159216508]},{"value":[16,20.89113681344315]},{"value":[17,26.32017988245934]},{"value":[18,35.96153979888186]},{"value":[19,27.91823631851003]},{"value":[20,21.73294046428055]}],"yAxisIndex":2,"xAxisIndex":2,"name":"C","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,25.68361331243068]},{"value":[2,26.56547104706988]},{"value":[3,14.18010599678382]},{"value":[4,32.12693759007379]},{"value":[5,27.56870436947793]},{"value":[6,31.86221315059811]},{"value":[7,16.15177395520732]},{"value":[8,38.03754788124934]},{"value":[9,12.00118559179828]},{"value":[10,29.1083446261473]},{"value":[11,36.70021946309134]},{"value":[12,21.97623057523742]},{"value":[13,22.43636606726795]},{"value":[14,19.01601066580042]},{"value":[15,38.75565592432395]},{"value":[16,17.91972253704444]},{"value":[17,12.27985854493454]},{"value":[18,31.20483862468973]},{"value":[19,22.89876527385786]},{"value":[20,34.57772513618693]}],"yAxisIndex":3,"xAxisIndex":3,"name":"D","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,33.25809333240613]},{"value":[2,31.78853573277593]},{"value":[3,14.90623469697312]},{"value":[4,21.60429408540949]},{"value":[5,20.4877359373495]},{"value":[6,23.96582934539765]},{"value":[7,29.45769669255242]},{"value":[8,37.79956379439682]},{"value":[9,37.32434239936993]},{"value":[10,23.50988460239023]},{"value":[11,35.12141350656748]},{"value":[12,25.04333137301728]},{"value":[13,26.03560280054808]},{"value":[14,15.62122752889991]},{"value":[15,30.42113698553294]},{"value":[16,38.56747268466279]},{"value":[17,15.57865953072906]},{"value":[18,18.43501554103568]},{"value":[19,25.02668473869562]},{"value":[20,11.1241763131693]}],"yAxisIndex":4,"xAxisIndex":4,"name":"E","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,26.79737854050472]},{"value":[2,31.16237484151497]},{"value":[3,18.483888853807]},{"value":[4,28.5865171183832]},{"value":[5,27.78873686445877]},{"value":[6,16.93914353614673]},{"value":[7,36.91654325928539]},{"value":[8,18.47896984312683]},{"value":[9,12.46657577576116]},{"value":[10,33.03944991435856]},{"value":[11,26.38278347905725]},{"value":[12,16.72986856428906]},{"value":[13,34.41874615848064]},{"value":[14,24.28146749036387]},{"value":[15,25.46368867857382]},{"value":[16,25.8717706380412]},{"value":[17,24.54085789620876]},{"value":[18,14.11927849054337]},{"value":[19,33.74341938411817]},{"value":[20,13.92304606037214]}],"yAxisIndex":5,"xAxisIndex":5,"name":"F","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,25.40070529095829]},{"value":[2,24.40952636767179]},{"value":[3,32.39310466684401]},{"value":[4,19.46743638953194]},{"value":[5,22.38699494628236]},{"value":[6,21.22527001891285]},{"value":[7,24.81166854035109]},{"value":[8,23.76306721009314]},{"value":[9,39.44764482555911]},{"value":[10,17.45122040389106]},{"value":[11,37.98248725710437]},{"value":[12,38.80090015241876]},{"value":[13,21.3511062390171]},{"value":[14,19.52846232336015]},{"value":[15,38.30308706266806]},{"value":[16,12.9798145708628]},{"value":[17,13.76899881288409]},{"value":[18,15.74852084508166]},{"value":[19,34.77628875523806]},{"value":[20,12.58889640914276]}],"yAxisIndex":6,"xAxisIndex":6,"name":"G","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,13.59108643606305]},{"value":[2,36.5523543022573]},{"value":[3,37.58686690358445]},{"value":[4,36.80654375115409]},{"value":[5,22.89055962115526]},{"value":[6,14.5018643559888]},{"value":[7,17.72952975705266]},{"value":[8,20.86694907862693]},{"value":[9,13.28402818180621]},{"value":[10,14.22269374132156]},{"value":[11,27.97656780574471]},{"value":[12,18.8282056315802]},{"value":[13,11.77002922166139]},{"value":[14,35.71394474245608]},{"value":[15,33.75741705764085]},{"value":[16,28.09749323641881]},{"value":[17,23.67604522267357]},{"value":[18,19.42037588683888]},{"value":[19,16.69831472914666]},{"value":[20,11.11327144317329]}],"yAxisIndex":7,"xAxisIndex":7,"name":"H","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,33.89778369804844]},{"value":[2,21.97216163622215]},{"value":[3,14.37020017765462]},{"value":[4,39.96701252413914]},{"value":[5,27.64659351203591]},{"value":[6,21.27865528920665]},{"value":[7,39.78041878668591]},{"value":[8,20.78049548901618]},{"value":[9,39.3185348296538]},{"value":[10,13.13604933442548]},{"value":[11,16.75548238214105]},{"value":[12,39.12051453953609]},{"value":[13,12.88739792769775]},{"value":[14,24.37107069185004]},{"value":[15,27.91507023619488]},{"value":[16,25.755483165849]},{"value":[17,31.25382419908419]},{"value":[18,14.75726961391047]},{"value":[19,30.5998980300501]},{"value":[20,36.34825750254095]}],"yAxisIndex":8,"xAxisIndex":8,"name":"I","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,15.86964695947245]},{"value":[2,33.31200887681916]},{"value":[3,22.51801596023142]},{"value":[4,30.33900863258168]},{"value":[5,24.73877296550199]},{"value":[6,39.47454213630408]},{"value":[7,29.34857914922759]},{"value":[8,12.91118911467493]},{"value":[9,10.32120120013133]},{"value":[10,27.51378222135827]},{"value":[11,17.38699395209551]},{"value":[12,36.72295921016484]},{"value":[13,33.85052080033347]},{"value":[14,10.5796895804815]},{"value":[15,32.47205125633627]},{"value":[16,35.79670888371766]},{"value":[17,23.3677018689923]},{"value":[18,26.35529385413975]},{"value":[19,21.17935752961785]},{"value":[20,32.04493748722598]}],"yAxisIndex":9,"xAxisIndex":9,"name":"J","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,36.34192725177854]},{"value":[2,33.8381478539668]},{"value":[3,15.49198787193745]},{"value":[4,24.73262567073107]},{"value":[5,35.1351474924013]},{"value":[6,38.72900407062843]},{"value":[7,23.49213741719723]},{"value":[8,21.54941412620246]},{"value":[9,12.23122323630378]},{"value":[10,21.06912806397304]},{"value":[11,25.38476228248328]},{"value":[12,24.79466702323407]},{"value":[13,10.51298649981618]},{"value":[14,10.61344586545601]},{"value":[15,38.56375191593543]},{"value":[16,12.9425999475643]},{"value":[17,31.52743698330596]},{"value":[18,12.94333309167996]},{"value":[19,24.9732395936735]},{"value":[20,18.70678582927212]}],"yAxisIndex":10,"xAxisIndex":10,"name":"K","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,17.05427879001945]},{"value":[2,27.40633682580665]},{"value":[3,30.19497958244756]},{"value":[4,20.5187745927833]},{"value":[5,25.61891704797745]},{"value":[6,15.1616857200861]},{"value":[7,13.14954177476466]},{"value":[8,13.26807098696008]},{"value":[9,31.35117449332029]},{"value":[10,28.4572847536765]},{"value":[11,28.52249323623255]},{"value":[12,26.40102585311979]},{"value":[13,20.16632206737995]},{"value":[14,32.81226117396727]},{"value":[15,11.56124188099056]},{"value":[16,39.26529560703784]},{"value":[17,28.53330895770341]},{"value":[18,34.23832198372111]},{"value":[19,23.2587267132476]},{"value":[20,15.41609967825934]}],"yAxisIndex":11,"xAxisIndex":11,"name":"L","type":"line","coordinateSystem":"cartesian2d"},{"data":[{"value":[1,28.88433216605335]},{"value":[2,27.64159376267344]},{"value":[3,20.95865085022524]},{"value":[4,12.80089754611254]},{"value":[5,34.41219495376572]},{"value":[6,37.16606398113072]},{"value":[7,23.37382908212021]},{"value":[8,16.98459232458845]},{"value":[9,28.32154368050396]},{"value":[10,15.27380249695852]},{"value":[11,23.67647597566247]},{"value":[12,30.92287226114422]},{"value":[13,24.56627594074234]},{"value":[14,28.33298073150218]},{"value":[15,25.29890306061134]},{"value":[16,14.35626289574429]},{"value":[17,26.56400597421452]},{"value":[18,18.47188869956881]},{"value":[19,39.85832993173972]},{"value":[20,11.98966013966128]}],"yAxisIndex":12,"xAxisIndex":12,"name":"M","type":"line","coordinateSystem":"cartesian2d"}],"grid":[{"height":"15.75%","width":"19.5%","top":"14%","left":"2%"},{"height":"15.75%","width":"19.5%","top":"14%","left":"27.5%"},{"height":"15.75%","width":"19.5%","top":"14%","left":"53%"},{"height":"15.75%","width":"19.5%","top":"14%","left":"78.5%"},{"height":"15.75%","width":"19.5%","top":"35.75%","left":"2%"},{"height":"15.75%","width":"19.5%","top":"35.75%","left":"27.5%"},{"height":"15.75%","width":"19.5%","top":"35.75%","left":"53%"},{"height":"15.75%","width":"19.5%","top":"35.75%","left":"78.5%"},{"height":"15.75%","width":"19.5%","top":"57.5%","left":"2%"},{"height":"15.75%","width":"19.5%","top":"57.5%","left":"27.5%"},{"height":"15.75%","width":"19.5%","top":"57.5%","left":"53%"},{"height":"15.75%","width":"19.5%","top":"57.5%","left":"78.5%"},{"height":"15.75%","width":"19.5%","top":"79.25%","left":"2%"}]},"dispose":true},"evals":[],"jsHooks":[]}
```

</div>

</div>

</div>
