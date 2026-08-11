# AI Energy Efficiency in Cloud Data Centres

MSc Dissertation — Ravensbourne University London
Student: Sunil Paudel
Supervisor: Dr M. Rehan Usman
Submission Date: August 2026

## Research Topic

Optimising Energy Efficiency of AI Workloads in Cloud 
Data Centres using Machine Learning Techniques.

## Project Status: COMPLETE

This dissertation project has been completed and submitted.

## Key Results

- CBIS (Confidence-Bounded Idle Scaling) algorithm achieved 
  8.06% energy reduction on real production data
- XGBoost model achieved R² of 1.0000, MAE of 17.38 Joules
- Confusion matrix validation: 99.94% precision, 99.88% recall
- Zero SLO violations recorded across evaluation period

## Dataset

Primary dataset: BurstGPT (Wang et al., 2025) — 1,404,294 
real Microsoft Azure GPT-3.5/GPT-4 requests over 60 
continuous days, aggregated into 87,833 minute-level records.

## Repository Structure
notebooks/ - Jupyter notebooks (data pipeline, model
training, CBIS implementation)
data/ - Processed datasets and results (CSV, JSON)
outputs/ - Generated charts and visualisations

## Objectives (All Completed)

- Characterise real-world LLM inference workload patterns 
  using production trace data
- Train and evaluate machine learning models for short-term 
  energy consumption forecasting
- Design the CBIS algorithm using prediction confidence to 
  guide power scaling decisions
- Evaluate energy savings and service reliability against 
  baseline operations

## Technologies

- Python (pandas, numpy, scikit-learn)
- XGBoost, LightGBM
- Jupyter Notebook
