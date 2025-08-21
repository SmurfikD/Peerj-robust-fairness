## Scaling the Experiment: From Demo to Real-World Data

This document explains how to move from the demo experiment (UCI Adult + Logistic Regression)  
to a large-scale experiment with **IMDb Movie Reviews + DistilBERT**.

_______________________________________________________________________________

## 1. Dataset: IMDb Movie Reviews

- Source: [HuggingFace Datasets](https://huggingface.co/datasets/imdb)  
- 50,000 reviews labeled as **positive** / **negative**.  
- Balanced dataset, widely used for sentiment classification benchmarks.

```python
from datasets import load_dataset
imdb = load_dataset("imdb")

_______________________________________________________________________________

## 2. Model: DistilBERT for Sentiment Analysis

    Use the pre-trained distilbert-base-uncased model.

    Fine-tune on IMDb for 2–3 epochs.

from transformers import AutoTokenizer, AutoModelForSequenceClassification, Trainer, TrainingArguments

tokenizer = AutoTokenizer.from_pretrained("distilbert-base-uncased")
model = AutoModelForSequenceClassification.from_pretrained("distilbert-base-uncased", num_labels=2)

_______________________________________________________________________________

## 3. Perturbation Scenarios

Reuse the same perturbations:

    Typos: inject random character noise into tokens.

    Noise: add irrelevant tokens (e.g., "lorem", "noise").

    Drift: simulate distribution shift by subsampling reviews from a specific decade.

    Bias Mitigation: apply debiasing methods (e.g., reweighting or post-processing).

_______________________________________________________________________________

## 4. Metrics

    Performance: Accuracy, Precision, Recall, F1, ROC-AUC

    Fairness: Demographic Parity Gap, Equal Opportunity Gap

    Add Brier Score for calibration if needed.

_______________________________________________________________________________

## 5. Running the Pipeline

    Adapt existing notebook (peerj_robust_fairness.ipynb)

    Replace preprocessing and model training with HuggingFace pipeline

    Log results into CSV (mean_results.csv, metrics_summary.csv)


