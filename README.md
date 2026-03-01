# AI Programming Foundations — Data Workflow Project

This project implements a reproducible data workflow using the Titanic dataset. It loads the data, cleans it with documented functions, runs exploratory analysis, and produces three labeled visualizations. The workflow is intended as a foundation for future machine learning and AI work.

## What You Built

- **Jupyter Notebook** (`data_workflow.ipynb`): End-to-end workflow with setup, ingestion, cleaning (two functions with docstrings), one EDA function, three visualizations (Survival by Pclass, by Sex, Age by Survival), and a written summary.
- **Dataset**: [Titanic - Machine Learning from Disaster](https://www.kaggle.com/c/titanic) — `data/train.csv` (891 rows, 12 columns).
- **Written summary**: `module_summary.md` contains the report with academic citations. Export this to **module_summary.pdf** for submission (e.g. open in VS Code and “Print” to PDF, or use `pandoc module_summary.md -o module_summary.pdf`).

## How to Run the Project

1. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```
2. **Create `requirements.txt` from your environment (if needed)**
   ```bash
   pip freeze > requirements.txt
   ```
3. **Open and run the notebook**
   - From the project root, start Jupyter: `jupyter notebook`
   - Open `data_workflow.ipynb` and run all cells (Cell → Run All), or run cells in order.

The notebook reads `data/train.csv` from the `data/` folder; ensure the CSV is in that location.

## Version Control

Use multiple commits as you complete tasks. Create at least one additional branch (e.g. `git checkout -b develop`) for development work. Before submitting, ensure the repo has at least two branches and a clear commit history.

## Bias and Data Quality (README reflection)

Poor cleaning can introduce bias in several ways: (1) **Imputing missing values** (e.g., Age with median) can hide systematic missingness (e.g., if survival or class affected who had age recorded). (2) **Dropping columns** (e.g., Cabin) removes information that might correlate with outcome. (3) **Using only one imputation strategy** (median/mean) can understate uncertainty. To reduce risk, we used median for Age (robust to outliers), documented choices in the notebook, and kept the analysis transparent so future work can try multiple imputation or sensitivity analyses.

## Future Integration

- **ML workflow**: This pipeline (load → clean → EDA → viz) is the same structure used before training models; next steps would be feature engineering, train/test split, and model training.
- **Neural networks / DL**: The same cleaned dataset and features can feed into neural nets; additional steps include scaling/normalization and encoding categoricals.
- **Agentic automation**: Scripts or agents could run this notebook (e.g., via `papermill` or `nbconvert`), re-run on new data versions, and trigger alerts when summary stats or distributions change beyond a threshold.
