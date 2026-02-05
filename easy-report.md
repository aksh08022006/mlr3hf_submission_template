# GSoC 2026: mlr3 Integration - Easy Task

Contributor: Aksh Kaushik
GitHub: https://github.com/aksh08022006/mlr3hf
Live Report (optional): https://aksh08022006.github.io/mlr3hf/
Date: 2026-02-05

1) My Logic & Dataset Choice

- Datasets used:
  - `iris` (OpenML/`mlr3oml::otsk()` id 59) — standard benchmark to verify `otsk()` integration.
  - `pen_vs_pencil` — small handcrafted dataset to verify mixed feature handling and column role inference.

Rationale: The `iris` dataset is used as a canonical test to confirm `mlr3oml::otsk()` behavior. The small custom dataset isolates edge cases (mixed types, factors, etc.) so we can validate Task construction logic without heavy dependencies.

2) Implementation

Load libraries and create Tasks from `otsk()`:

```r
library(mlr3)
library(mlr3oml)

# as_task(otsk(id = 59)) example
task_iris <- as_task(otsk(id = 59))
print(task_iris)

# Build small handcrafted dataset and create Task
stationery_data <- data.frame(
  length_cm = c(14.5, 15.0, 13.8, 17.5, 18.2, 19.1),
  has_ink = factor(c("Yes", "Yes", "Yes", "No", "No", "No")),
  has_eraser = factor(c("No", "No", "No", "Yes", "Yes", "Yes")),
  body_material = factor(c("Plastic", "Plastic", "Metal", "Wood", "Wood", "Wood")),
  label = factor(c("Pen", "Pen", "Pencil", "Pencil", "Pen", "Pencil"))
)
task_stationery <- as_task_classif(stationery_data, target = "label", id = "pen_vs_pencil")
print(task_stationery)
```

3) Results / Output

- Paste `print()` output of the created Tasks here. Example:

```
#<TaskClassif: pen_vs_pencil (6x5)>
# Target: label
# Properties: multiclass
# Features: 4
```

4) Justification & Method

- Explain briefly why these two examples are sufficient for the easy test: they validate that `otsk()` returns `TaskClassif` objects and that task construction handles mixed column types.

5) Reproducibility

Commands to reproduce locally:

```bash
# Install dependencies
Rscript -e "install.packages(c('mlr3','mlr3oml','mlr3data','testthat'), repos='https://cloud.r-project.org')"
# Run snippets in R or knit the report
```
