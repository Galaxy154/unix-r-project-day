# Build a Reproducible Project: Unix + R

A one-day, hands-on workshop page. Students build a small research project from scratch: make directories, download data with `curl`, combine files in the shell, summarize and plot in R, and generate an HTML report. Eight bugs are planted in the scripts for students to find and fix.

**Live site:** see the GitHub Pages link in this repo's About section.

## What's here

| Path | What it is |
|---|---|
| `index.html` | Home page: overview, setup, AI tips, links |
| `day1.html` | The step-by-step walkthrough (Steps 1–10, bugs with hints and solutions) |
| `data/bird_surveys.tar.gz` | The dataset students download with `curl` |
| `img/` | Expected figures and a screenshot of the finished report |
| `style.css`, `scripts.js` | Site styling and copy buttons, adapted from JT Van Leuven's [Git, R, and Unix course site](https://jtvanleuven.github.io/Git-R-and-Unix-for-Reproducible-Scientific-Analysis/) |

## The dataset

Simulated bird point-count surveys, 2023–2025, at 12 Palouse sites (4 forest, 4 grassland, 4 wetland), each visited in spring, summer, and fall.

- `sites.csv`: `site_id, site_name, habitat, elevation_m`
- `survey_2023.csv`, `survey_2024.csv`, `survey_2025.csv`: `date, site_id, season, observer, species, count`

Two data problems are included on purpose: the 2024 file capitalizes season names (`Spring`), and 9 counts in 2025 are `NA`.

## The 8 planted bugs

| # | Script | Bug |
|---|---|---|
| 1 | `01_download.sh` | Filename typo (`bird_survey` vs `bird_surveys`); curl saves a 404 page, tar fails |
| 2 | `02_combine.sh` | `cat` keeps every file's header line (silent) |
| 3 | `03_summarize.R` | `left_join(by = "site")` but the column is `site_id` |
| 4 | `03_summarize.R` | `sum()` without `na.rm = TRUE` gives `NA` (silent) |
| 5 | `03_summarize.R` | `Spring` vs `spring` doubles the seasons (silent) |
| 6 | `04_figures.R` | ggplot `+` at the start of a line |
| 7 | `04_figures.R` | Saves to `figure/` instead of `figures/` |
| 8 | `05_report.R` | Image paths missing `../` so the report shows broken images (silent) |
