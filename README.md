# Robustness and Fairness Testing of ML Models

_______________________________________________________________________________

This repository contains the research package: 
**"Impact of Data Quality and Perturbations on the Robustness and Fairness of ML Models"**  


Author: **Dmitrii Kochetov**  
Date: **2025**

_______________________________________________________________________________

## Repository Structure
`````
test_package/
├── notebooks/
│ └── robust_fairness.ipynb # Main experiment notebook
├── metrics/
│ ├── run_results.csv # Metrics for each run
│ ├── mean_results.csv # Average metrics per scenario
│ └── metrics_summary.csv # Summary metrics table
├── figures/
│ ├── accuracy_bar.png # Accuracy comparison across scenarios
│ ├── fairness_plot.png # Fairness gaps (DPG/EOG)
│ ├── roc_curve.png # ROC curve (baseline model)
│ └── robustness_plot.png # Robustness line plot
├── table.tex # LaTeX table for manuscript
├── README.md # This file
├── HOW_TO_SCALE.md # Instructions to scale to IMDb + DistilBERT
└── requirements.txt # Dependencies
`````

_______________________________________________________________________________


## Setup Instructions

1. Install Python
Make sure you have **Python 3.10+** installed.  
Check your version:

python --version

2. Clone and Install Dependencies

git clone https://github.com/<your-username>/test_package.git
cd test_package
pip install -r requirements.txt


3. Run the Experiment

Start Jupyter Notebook:

jupyter notebook notebooks/robust_fairness.ipynb

Run all cells in the notebook to reproduce metrics and figures.

_______________________________________________________________________________

## Results

    Performance metrics: Accuracy, Macro Precision/Recall/F1, ROC-AUC

    Fairness metrics: Demographic Parity Gap (DPG), Equal Opportunity Gap (EOG)

    Test scenarios:

       - Baseline

       - Typos (character noise)

       - Noise (numerical perturbations)

       - Drift (distribution shift)

       - Bias Mitigation (debiasing via Calibrated Equalized Odds)

Figures and tables will be saved in figures/ and metrics/.
_______________________________________________________________________________

## Results (Sample)

| Scenario  | Accuracy | ROC-AUC | DPG ↓ | EOG ↓ |
|-----------|----------|---------|-------|-------|
| Baseline  | 1.000    | 1.000   | 0.153 | 0.000 |
| Noise     | 0.865    | 0.977   | 0.025 | 0.103 |
| Drift     | 0.888    | 0.981   | 0.030 | 0.103 |


_______________________________________________________________________________

## Scaling Up

For large-scale replication (IMDb + DistilBERT), see HOW_TO_SCALE.md

This includes instructions for using HuggingFace datasets and transformers.
_______________________________________________________________________________

License

Free for academic and research use with citation.
