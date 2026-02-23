<div id="main" class="col-md-9" role="main">

# Connect charts

<div class="ref-description section level2">

Connect charts together.

</div>

<div class="section level2">

## Usage

<div class="sourceCode">

``` r
e_connect(e, ids)

e_group(e, group)

e_connect_group(e, group)

e_disconnect_group(e, group = NULL)

e_arrange(..., rows = NULL, cols = NULL, width = "xs", title = NULL)
```

</div>

</div>

<div class="section level2">

## Arguments

-   e:

    An `echarts4r` object as returned by `e_charts` or a proxy as
    returned by `echarts4rProxy`.

-   ids:

    Scalar, vector or list of ids of chart to connect with.

-   group:

    Group name.

-   ...:

    Any `echarts` objects.

-   rows, cols:

    Number of rows and columns.

-   width:

    Width of columns, one of `xs`, `md`, `lg`.

-   title:

    Title of charts.

</div>

<div class="section level2">

## Value

`e_arrange`: in an interactive session, returns a
`htmltools::browsable`, in `rmarkdown` returns a container
(`htmltools::div`).

</div>

<div class="section level2">

## Note

`e_arrange` may not work properly in the RStudio viewer.

</div>

<div class="section level2">

## Functions

-   `e_connect`: connects charts by `ids`, *cannot* be disconnected.

-   `e_group`: assigns a group to chart.

-   `e_connect_group`: connects chart with another group.

-   `e_disconnect_group`: diconnects chart from group.

-   `e_arrange`: arrange charts.

</div>

<div class="section level2">

## Examples

<div class="sourceCode">

``` r
# linked datazoom
e1 <- cars |>
  e_charts(
    speed,
    height = 200
  ) |>
  e_scatter(dist) |>
  e_datazoom(show = FALSE) |>
  e_group("grp") # assign group

e2 <- cars |>
  e_charts(
    dist,
    height = 200
  ) |>
  e_scatter(speed) |>
  e_datazoom() |>
  e_group("grp") |> # assign group
  e_connect_group("grp") # connect

if (interactive()) {
  e_arrange(e1, e2, title = "Linked datazoom")
}
```

</div>

</div>

</div>
