## Test environments
* Local R installation (4.5.0)
* GitHub Actions: matrix on Windows, macOS, and Ubuntu (see `.github/workflows/R-CMD-check.yaml`)
* R-hub: optional platform matrix via `.github/workflows/rhub.yaml`
* win-builder (devel)



## Submission comments

- Bumped bundled `echarts.js` to 6.0.0.
- New chart types and related functions: `e_doughnut()`, `e_violin()`, `e_barRange()`, `e_contour()`, `e_lineRange()`, `e_stage()`, `e_chord()`.
- New utilities: `e_jitter()`, `e_zigzag()`, `e_annotations()`, `e_insert_data()`.
- Greatly expanded unit testing and numerous bug fixes (see `NEWS.md` for full details and issue references).
