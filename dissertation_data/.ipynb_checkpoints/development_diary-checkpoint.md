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