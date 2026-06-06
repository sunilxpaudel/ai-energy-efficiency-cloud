# DISSERTATION DEVELOPMENT DIARY & RESEARCH LOG
MSc Student: Sunil Paudel

## ENTRY 1: JUNE 2026 - DATA INFRASTRUCTURE & ENVIROMENT SETUP
- Architecture Setup: Configured Anaconda and local Jupyter Notebook server on a Unix-based macOS machine.
- Workload Selection: Selected the Microsoft Azure LLM Inference Traces (2024), originally sourced from ISCA '24 and HPCA '25 literature.
- Critical Ingestion Bug encountered: 
  * Error Text: `gaierror: [Errno 8] nodename nor servname provided, or not known`
  * Root Cause: Local macOS network DNS resolution faults/network proxy limitations blocked connection to remote Git/Azure servers.
  * Architectural Resolution: Developed a high-fidelity data emulation script locally to structurally mimic the target Azure telemetry columns, ensuring project continuity without remote dependencies.
- Feature Engineering: Resampled raw transaction logs into discrete 1-minute tracking blocks. Built target feature matrix including: 'ArrivalRate', 'TotalInputTokens', 'TotalOutputTokens', 'Hour', and 'Minute'.
## ENTRY 2: JUNE 2026 - DATA MATRIX & MODEL TRAINING

### Data Generation Fix
- Initial emulator produced constant 21,000 J energy output
- Root Cause: Token volumes too high — active_seconds always 
  clipped at 60 seconds maximum
- Fix Applied: Reduced token density and added sine wave pattern 
  combined with hour-based multipliers
- Result: Energy now varies realistically between 3,405 J (night) 
  and 21,000 J (peak hours)

### Energy Model Parameters
- P_ACTIVE = 350W (NVIDIA GPU active state)
- P_IDLE = 50W (NVIDIA GPU idle state)  
- T_INPUT = 0.001 seconds per input token
- T_OUTPUT = 0.025 seconds per output token
- Energy calculated in both Joules and kWh per minute window

### Dataset Finalised
- Total rows: 10,080 (one full week, minute-level)
- Saved to: dissertation_data/energy_matrix.csv
- Hourly pattern validated — matches enterprise traffic expectations

### XGBoost Model Trained
- Features: Hour, Minute, ArrivalRate, 
  TotalInputTokens, TotalOutputTokens
- Train/Test split: 80/20 (8,064 / 2,016 rows)
- Noise added: std=300J for realistic variance
- R² Score: 0.9951
- MAE: 247.26 J
- Charts saved: dissertation_data/xgboost_results.png

### CBIS Algorithm — In Progress
- Logic built: SCALE_DOWN, STAY_ACTIVE, SAFETY_BUFFER
- Bug found: STAY_ACTIVE assigned flat 21,000J incorrectly
- Fix applied: STAY_ACTIVE now uses predicted energy value
- Final results pending next session

### Datasets Identified For Supervisor Review
- Primary: Azure LLM Inference Traces 2024 (emulated)
  Source: Stojkovic et al. HPCA 2025
- Backup: BurstGPT — 10.31M traces, 213 days
  Source: Wang et al. KDD 2025
  URL: github.com/HPMLL/BurstGPT

## ENTRY 2: JUNE 2026 - XGBOOST & CBIS

- Fixed flat 21,000J energy bug using sine wave + hour multipliers
- Energy now ranges 3,405J to 21,000J realistically  
- XGBoost trained: R2=0.9951, MAE=247J
- CBIS algorithm written — results to confirm next session
- BurstGPT identified as backup dataset (213 days, KDD 2025)
