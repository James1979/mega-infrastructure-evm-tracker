cat > README.md << 'EOF'
# Mega-Infrastructure EVM Tracker

[![Streamlit](https://img.shields.io/badge/Framework-Streamlit-red.svg)](https://streamlit.io/)
![Python](https://img.shields.io/badge/Python-3.11-blue.svg)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Made with Plotly](https://img.shields.io/badge/Charts-Plotly-informational.svg)](https://plotly.com/python/)

A professional, production-ready **Earned Value Management (EVM)** dashboard for large capital programs.  
Designed for **Project Controls Analysts**, **PMOs**, and **Executives** who need **CPI/SPI trends, PV/EV/AC burn, CV/SV variance, EAC/ETC forecasts**, and portfolio-level KPIs in minutes.

> Live App: _(add your Streamlit Cloud URL after you deploy)_  
> Repo: `James1979/mega-infrastructure-evm-tracker`

---

## Why this exists

Large programs (utilities, infrastructure, energy) often lack **real-time, unified visibility** across cost and schedule. This app pulls core EVM signals into a single view so leaders can **detect overruns early**, **prioritize recovery**, and **communicate status** with confidence.

---

## Features

- **Portfolio KPIs**: CPI, SPI, Total EV/AC, EAC/ETC, VAC (weighted/aggregated)
- **Trends**:  
  - CPI/SPI over time  
  - PV/EV/AC burn (portfolio)  
  - CV/SV variance (portfolio)
- **Data options**: Upload your CSV or use realistic sample data
- **Filters**: Project selection and date range
- **Downloadable CSV template** for fast onboarding
- **Zero-install deployment** to Streamlit Cloud

---

## EVM Formulas (implemented)

- **CPI** = EV / AC  
- **SPI** = EV / PV  
- **CV**  = EV − AC  
- **SV**  = EV − PV  
- **EAC** = AC + (BAC − EV) / CPI  _(default CPI-based model)_  
- **ETC** = EAC − AC  
- **VAC** = BAC − EAC

> Notes:
> - CPI/SPI guard against divide-by-zero and missing values.
> - Portfolio CPI, SPI are **weighted** (CPI by AC, SPI by PV).

---

## Data Schema

Required columns (case-insensitive):
- `Date` (YYYY-MM-DD or any parseable date)
- `Project` (string)
- `PV` (float) – Planned Value (cumulative)
- `EV` (float) – Earned Value (cumulative)
- `AC` (float) – Actual Cost (cumulative)
- `BAC` (float) – Budget At Completion (constant per project)

Optional:
- `WBS` (string)

**Sample CSV**

```csv
Date,Project,WBS,PV,EV,AC,BAC
2025-07-01,Project-1,Overall,1200000,1100000,1300000,50000000
2025-07-02,Project-1,Overall,2400000,2200000,2600000,50000000
2025-07-03,Project-1,Overall,3600000,3200000,4000000,50000000
