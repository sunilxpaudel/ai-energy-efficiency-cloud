# AI Energy Efficiency in Cloud Data Centres

**MSc Dissertation — Ravensbourne University London**
**Student:** Sunil Paudel
**Start Date:** May 2026

## Research Topic
Optimising Energy Efficiency of AI Workloads in Cloud Data Centres using Machine Learning Techniques.

## Objectives
Obj 1: Characterize and preprocess erratic, real-world AI workload traces into discrete time-series resource telemetry structures.
Obj 2: Train and evaluate a high-performance machine learning regression model to accurately forecast upcoming token traffic and compute bursts.
Obj 3: Design an original, custom control heuristic to dynamically adjust hardware power scaling based on prediction confidence boundaries.
Obj 4: Quantify total data center energy savings against baseline operations while validating zero violation of Service Level Objectives (SLOs).

## Research Architecture & Milestones

### 📊 Milestone 1: Data Infrastructure & Telemetry Aggregation (Completed)
- **Target Workload Trace:** Modeled on the official Microsoft Azure LLM Inference Traces (2024).
- **Feature Engineering Pipeline:** 
  - Converted raw request streams into discrete **1-minute resource windows**.
  - Generated direct GPU-stress proxy metrics: `ArrivalRate`, `TotalInputTokens`, and `TotalOutputTokens`.
  - Extracted cyclic temporal features (`Hour`, `Minute`) to train time-series estimators.
- **Development Environment:** Configured localized Anaconda/Jupyter workspace on macOS.

### 🤖 Milestone 2: Predictor Engine Training (In Progress)
- Implementation of an **XGBoost / LightGBM Time-Series Forecaster** to predict upcoming token volume spikes 60 seconds into the future.

## Technologies
- Python
- Machine Learning
- Cloud Platforms (AWS/Azure)
