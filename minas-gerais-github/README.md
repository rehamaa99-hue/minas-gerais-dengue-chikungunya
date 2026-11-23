# Minas Gerais dengue and chikungunya analysis

This R Markdown report reproduces the pooled 2021–2025 municipal analysis. Keep `analysis.Rmd` and `inputs.zip` together in a writable folder. The archive contains the study snapshot for all 853 municipalities, including 1,706 weekly InfoDengue files, the 2020 boundaries, population and covariate tables.

## Run the report

Use R with Pandoc available. RStudio includes Pandoc. Install the analysis packages once in R.

```r
install.packages(c("rmarkdown", "knitr", "geobr", "sf", "spdep", "leaflet",
                   "htmlwidgets", "htmltools", "ggplot2", "readxl", "combinat"))
install.packages("INLA", repos = c(CRAN = "https://cloud.r-project.org",
                                  INLA = "https://inla.r-inla-download.org/R/stable"))
```

Open `analysis.Rmd` in RStudio and choose **Knit to HTML**. From a terminal in the downloaded folder, the equivalent command is:

```sh
Rscript --vanilla -e 'rmarkdown::render("analysis.Rmd")'
```

The report extracts the snapshot to `data/raw/`, writes derived tables and the adjacency graph to `data/processed/`, and fits all six ten-covariate prior scenarios under `results/`. It also refits the five-covariate model for posterior risk estimates and joint exceedance probabilities. Each render regenerates these outputs. The HTML maps use OpenStreetMap tiles when viewed online.

The exploratory model-selection and poster-export chunks are optional and skipped when knitting. The poster exports require the R packages `webshot2` and `png` and a Chrome installation.

## Software used for the replication run

R 4.6.0, INLA 25.10.19, fmesher 0.8.0, sf 1.1.1, spdep 1.4.2, geobr 2.0.1, leaflet 2.2.3, ggplot2 4.0.3, readxl 1.5.0, combinat 0.0.8, rmarkdown 2.31, knitr 1.51, htmlwidgets 1.6.4 and htmltools 0.5.9. The installation commands use the package repositories' available versions. Numerical results may vary with the INLA build.
