# Fetal-Weight-Prediction-Accuracy-Project

This repository contains a set of Jupyter notebooks that evaluate the accuracy and bias patterns of fetal-weight prediction (EFW) from ultrasound measurements, with a focus on clinically relevant error decomposition and subgroup comparisons.  
The work is designed to be **method-focused and reproducible in structure**, while **excluding any real patient-level data**.

## What this project covers
- **Error metrics** for fetal-weight prediction (e.g., absolute/relative error, signed error, overestimation vs underestimation)
- **Bias patterns** across clinically meaningful subgroups (e.g., gestational age windows, size categories such as LGA)
- **Replicable analysis workflow** with clear preprocessing assumptions and step-by-step notebooks
- **Indication text cleaning + categorization** (public-safe version) to make downstream utilization/accuracy analyses feasible

> **Note on data**: The dataset used in the original research is not included in this public repository due to privacy/IRB constraints.  
> The notebooks are shared to demonstrate the analysis logic, feature engineering approach, and modeling/validation workflow.

---

## Repo contents (notebooks)
### 1) `Data Cleaning Indication-Public .ipynb`
Public-safe version of the data cleaning pipeline for ultrasound *indication* free-text:
- standardizes common variants/abbreviations
- maps raw text into structured categories for analysis
- supports downstream trend and cohort characterization

### 2) `Indication Analysis .ipynb`
Exploratory analysis using the structured indication variables:
- distribution and trends of indications
- co-occurrence patterns / category summaries (where applicable)
- quality checks for category coverage and stability

### 3) `weight_error_analysis.ipynb`
Core notebook for fetal-weight prediction error analysis:
- defines error metrics (absolute, relative, signed)
- summarizes error distributions
- produces key plots/tables for model performance interpretation

### 4) `overestimate_analysis.ipynb`
Focused analysis on **overestimation** behavior:
- identifies contexts where EFW systematically overestimates birth weight
- compares error magnitude and frequency across groups

### 5) `overestimate_analysis-replicate .ipynb`
A replication/verification notebook to:
- confirm key findings using the same methodology
- ensure results are consistent under alternative filtering/definitions

---

## How to use (public version)
Because raw data is not included, you have two options:
- Open any notebook directly in GitHub to view the workflow and methodology.

If you want to execute the notebooks locally, provide your own dataset that matches the expected schema.  
At minimum, most notebooks assume variables like:
- gestational age at ultrasound / delivery (or equivalent)
- estimated fetal weight (EFW) at ultrasound
- birth weight at delivery (or outcome proxy)
- optional covariates for subgrouping (e.g., sex, indication category, etc.)

Install dependencies:
```bash
pip install pandas numpy scipy statsmodels matplotlib
