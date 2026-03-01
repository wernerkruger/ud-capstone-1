# Module Summary — Data Workflow Capstone

## Overview

This project implements a complete, reproducible data workflow in a Jupyter notebook. The dataset used is **Titanic - Machine Learning from Disaster** (Kaggle), specifically the training set `train.csv`, available at: https://www.kaggle.com/c/titanic. The workflow covers ingestion, cleaning, exploratory analysis, visualizations, and a written summary of findings.

## Dataset Description

The Titanic dataset describes passengers aboard the RMS Titanic and whether they survived the sinking. The training set has **891 rows** (passengers) and **12 columns**. Key variables include: **Survived** (0/1 target), **Pclass** (1st, 2nd, 3rd class), **Sex**, **Age**, **SibSp** (siblings/spouses aboard), **Parch** (parents/children), **Fare**, and **Embarked** (port). There are missing values in **Age**, **Cabin**, and **Embarked**. The analysis focuses on survival patterns by class, sex, and age.

## Workflow Description (High Level)

1. **Ingestion**: Load `data/train.csv` with Pandas and display the first rows.
2. **Cleaning**: Apply two cleaning functions—(a) drop redundant columns (PassengerId, Name, Ticket, Cabin), and (b) fill missing numeric values (Age, Fare) using median imputation; fill missing Embarked with the mode.
3. **Exploratory analysis**: Run an EDA function that reports shape, dtypes, missing counts, summary statistics, and survival rates by Sex and Pclass.
4. **Visualizations**: Produce three figures—(1) survival count by Pclass, (2) survival count by Sex, (3) age distribution by survival (boxplot).
5. **Summary**: Markdown section describing insights, patterns, assumptions, and limitations.

## Key Decisions and Assumptions

- **Cleaning**: Redundant columns were dropped to focus on analyzable features and to avoid leaking identifiers; median imputation for Age and Fare was chosen for robustness to outliers (Danchev, 2022, emphasizes reproducible and documented choices). Using a single imputation (e.g., median) is a common practice when missingness is limited; for stronger inference, multiple imputation would better capture uncertainty (e.g., Pandas documentation and missing-data literature).
- **EDA focus**: We focused on survival rates by Sex and Pclass because they are the strongest known predictors and are directly interpretable.
- **Plots**: Figure 1 (Pclass) and Figure 2 (Sex) show counts by survival to compare group sizes and survival rates; Figure 3 (Age by survival) shows whether age distributions differ between survivors and non-survivors.

## Results and Interpretation

- **Figure 1 (Survival by Pclass)**: First class had a higher proportion of survivors than second and third class; third class had the most passengers and the fewest survivors.
- **Figure 2 (Survival by Sex)**: Female passengers had a much higher survival rate than male passengers, consistent with “women and children first.”
- **Figure 3 (Age by Survival)**: The distribution of age among survivors is slightly shifted toward younger ages compared with non-survivors, consistent with children being prioritized.

Overall, class and sex were the dominant factors; age added nuance (e.g., younger passengers more likely to survive).

## Responsible Practice (Bias and Data Quality)

- **Imputation bias**: Filling missing Age with the median can mask systematic missingness (e.g., if missingness depended on class or survival). We documented this and kept the analysis transparent; a next step would be to compare median imputation with stratified imputation or multiple imputation.
- **Dropping Cabin**: Cabin was mostly missing; dropping it avoids unstable estimates but loses information. We did not use “Cabin known vs unknown” as a feature; that could be explored to reduce information loss.
- **Data quality**: We did not alter the raw CSV; cleaning is done in code so that others can reproduce or modify choices (reproducibility follows the principles in Danchev, 2022).

## Reproducibility

Someone else can rerun the work as follows: (1) Clone the repository and install dependencies with `pip install -r requirements.txt`. (2) Ensure `data/train.csv` is in the `data/` folder. (3) Open `data_workflow.ipynb` in Jupyter and run all cells. The `requirements.txt` was generated with `pip freeze > requirements.txt` (or use the provided minimal list). The project uses Git with multiple commits and at least one development branch to track changes and support collaborative or iterative workflow.

## Sources and Citations

- **Danchev, V. (2022).** Reproducible Data Science with Python: An Open Learning Resource. *Journal of Open Source Education*. DOI: 10.21105/jose.00156. — Used to support the decision to document cleaning steps and to structure the workflow for reproducibility.
- **Pandas Development Team.** *Pandas documentation* (e.g., Missing data, Fillna). https://pandas.pydata.org/docs/. — Referenced for best practices on handling missing data (e.g., `fillna`, choice of fill value).

## References

Danchev, V. (2022). Reproducible Data Science with Python: An Open Learning Resource. *Journal of Open Source Education*. https://jose.theoj.org/papers/10.21105/jose.00156. DOI: 10.21105/jose.00156.

Pandas Development Team. (2024). *pandas: powerful Python data analysis toolkit*. Documentation. https://pandas.pydata.org/docs/.
