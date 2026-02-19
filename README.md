# Admission Prediction

### A Hybrid Machine Learning Approach for Graduate Admission Prediction and Combined University–Program Recommendation

This repository contains the complete experimental pipeline used in the
accompanying research paper. All figures, tables, and results reported in the
paper are generated directly from the notebooks and scripts provided here.

The final versions of the figures and experimental results are available in the
corresponding zenodo paper:

🔗 https://zenodo.org/records/18702298?token=eyJhbGciOiJIUzUxMiJ9.eyJpZCI6IjY3YjI4YWM1LTMwMjktNDJlMS05NmNhLWYwZjZhNTEyOTEzNyIsImRhdGEiOnt9LCJyYW5kb20iOiJjNDhlNmI2MjY3N2U3YTc3MmY3ZGZhMjJhYTUzNmRmNCJ9.Da3Ja6IQ0DKSXywdGuWlmYHO6uWg7TCMKL3ygyaUKky55rJcN_yOEcUyx2ASF01gD4s82zlQwPKXYrvXg6yd2w

---

##  Data and Workflow Overview

The raw data file (`initial_run_cleaned.parquet`) is provided and serves as the
starting point of the pipeline. The workflow proceeds as follows:

1. **Data Enrichment**  
   Uses `initial_run_cleaned.parquet` as input and enriches the data using
   external academic sources.

2. **Data Cleaning**  
   Performs preprocessing, missing value handling, normalization, and filtering
   on the enriched data.

3. **Feature Engineering**  
   Constructs and extracts features, documents the feature logic, and produces
   a fully numeric dataset ready for modeling.

The output of these three steps is:

- `finalpaperdataset.csv`

All subsequent notebooks — **EDA**, **baseline models**, **hybrid model**, and
the **recommendation system** — use this final dataset.

> You only need to update file paths inside the notebooks to match your local
> directory structure.

---

##  Provided Files

For convenience and reproducibility, the following files are included:

- `finalpaperdataset.csv`  
  Fully processed, encoded, and scaled dataset used for all experiments.

- `freq_mappingsF.pkl`  
  Frequency mappings for decoding categorical features, useful if access to the
  clean but not fully encoded dataset is required.

- `scalerF.pkl`  
  Saved feature scaler used during model training and inference.

Utility functions are defined locally within the notebooks to keep the repository
structure compact and easy to follow.

##  Repository Structure

```text
admission-prediction/
│
├── 1.Datascrapping/
│   └── Data scraping scripts and notebooks for collecting self-reported
│       graduate admission records from GradCafe
│
├── 2.Dataenrichment.ipynb
│   └── Data enrichment using external academic sources
│       (OpenAlex API, QS World University Rankings, Wikidata)
│
├── 3.Datacleaning.ipynb
│   └── Data preprocessing, filtering, normalization, and consistency checks
│
├── 4.Feature_engineering.ipynb
│   └── Feature extraction, feature construction, and documentation of
│       the logic and rationale behind engineered variables
│
├── 5.EDA.ipynb
│   └── Exploratory data analysis and statistical visualizations
│
├── 6.Baselinemodel.ipynb
│   └── Baseline machine learning models, including:
│       Logistic Regression, Decision Tree, Random Forest,
│       K-Nearest Neighbors (KNN), Support Vector Machine (SVM),
│       and LightGBM
│
├── 7.Hybridmodel.ipynb
│   └── Proposed hybrid framework combining XGBoost as the baseline
│       model with KNN applied to model residuals
│
├── 8.Recommendationsystem.ipynb
│   └── University recommendation system based on predicted admission
│       probabilities and applicant similarity
│
├── finalpaperdataset.csv
│   └── Final processed dataset used for training and evaluation
│
├── freq_mappingsF.pkl
│   └── Saved frequency mappings for categorical feature encoding
│
├── scalerF.pkl
│   └── Saved feature scaler used for model training and inference
│
├── requirements.txt
│   └── Python dependencies required to reproduce the experiments
│
├── .gitignore
├── .gitattributes
└── README.md
```







---

## Dependencies

All required Python packages are listed in `requirements.txt`.  
Install them using:

```bash
pip install -r requirements.txt
