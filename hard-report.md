# GSoC 2026: mlr3 Integration - Hard Task

Contributor: Aksh Kaushik
GitHub: https://github.com/aksh08022006/mlr3hf
Live Report (optional): https://aksh08022006.github.io/mlr3hf-hard/
Date: 2026-02-05

Goal

Connect `mlr3` to Hugging Face datasets and convert a HF dataset to an `mlr3::Task`.

Summary of approach

- Option A (prototype): Use a simple CSV download approach for HF repos with CSV files. This is implemented in the prototype function `htsk()` which accepts a shorthand `hf:owner/repo/path/to/file.csv` and downloads the resolved file from `https://huggingface.co/datasets/<owner/repo>/resolve/main/<path>`.
- Option B (recommended for full support): Use `reticulate` to call Python's `datasets` or the `hfhub` client to support multiple dataset formats and streaming. This avoids loading whole datasets into R memory.

Implementation (prototype `htsk()`)

```r
library(mlr3)
library(mlr3hf) # your package

# Example: simple hf: shorthand
task <- htsk('hf:username/repo/path/to/file.csv', target = 'label')
print(task)
```

Example using reticulate + Python `datasets` (sketch)

```r
library(reticulate)
datasets <- import('datasets')
ds <- datasets$load_dataset('your_dataset_name')
# convert to data.frame in chunks or filter columns, then to mlr3 Task
```

Results

- Paste the `print()` output of the created `mlr3::Task` here.
- If you used a streaming bridge, describe how you validated that only needed rows are loaded.

Justification & methods

- Explain design choices: memory-safety via streaming, use of `reticulate` for robust HF access, fallback prototype for CSV-hosted datasets.

Reproducibility

Commands and environment notes:

```bash
# Install reticulate / setup conda
Rscript -e "install.packages('reticulate', repos='https://cloud.r-project.org'); reticulate::install_miniconda()"
# Install Python package datasets
python -m pip install datasets
# Run R script that uses reticulate to load dataset and call htsk bridge
```
