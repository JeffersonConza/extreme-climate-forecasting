# 🌍 Extreme Climate Forecasting in Ecuador

### Extreme Value Theory (EVT), Bayesian Inference & Machine Learning

> A scientific modeling framework for predicting extreme climatic events using classical EVT, Bayesian methods, and deep learning.

---

## 📌 Overview

This repository implements a **full research pipeline** for modeling and forecasting extreme climatic events across major Ecuadorian cities.

The project is based on:

* 📊 **Extreme Value Theory (EVT)**
* 📈 **Generalized Extreme Value (GEV) modeling**
* 🎯 **Maximum Likelihood Estimation (MLE)**
* 🧠 (Planned) **Bayesian EVT**
* 🤖 (Planned) **Machine Learning forecasting of block maxima**

We move from raw hourly weather data (~6.4M observations) to:

* EVT-safe preprocessing
* Block maxima modeling
* Return level estimation
* Cross-city comparative analysis
* Forecast-ready dataset construction

---

## 🧠 Research Objective

We aim to predict **future block maxima** of climatic variables such as:

* 🌡 Temperature
* 🌧 Hourly precipitation
* 🌬 Wind speed

Formally, we model:

[
M_{kl} = \max{ X_{kl}(t) }
]

and study both:

* Distributional inference (GEV fitting)
* Forecasting of future maxima

---

## 📁 Project Structure

```
extreme-climate-forecasting/
│
├── data/
│   ├── data_clima.csv
│   ├── data_clima_clean.parquet
│   ├── _tmp_evt_city_parts_final/
│   └── _tmp_evt_city_sorted_final/
│
├── EDA/
│   ├── figures/
│   └── tables/
│
├── Notebooks/
│   ├── 00_EVT_Climate_Data_Cleaning_Ecuador.ipynb
│   ├── 01_EVT_GEV_MLE_BlockMaxima_Ecuador.ipynb
│   └── 02_EVT_GEV_MLE_Batch_AllCities.ipynb
│
├── results/
│   ├── mle_quito_temp_me/
│   ├── mle_guayaquil_temp_me/
│   └── gev_mle_batch_summary.csv
│
└── Prediction of extreme events in climatic time series.pdf
```

---

## 🚀 Implemented Components

### 1️⃣ EVT-Safe Data Cleaning

Notebook:
`00_EVT_Climate_Data_Cleaning_Ecuador.ipynb`

Features:

* Chunked ingestion of 6.4M+ rows
* Local timezone handling (UTC-5 / UTC-6)
* Missingness audit
* Duplicate timestamp detection
* Temporal coverage diagnostics
* EVT tail exploration:

  * Survival plots
  * Mean excess plots
  * Block maxima (annual & monthly)

---

### 2️⃣ Classical EVT – GEV via MLE

Notebook:
`01_EVT_GEV_MLE_BlockMaxima_Ecuador.ipynb`

Implements:

* Monthly / yearly block maxima
* GEV parameter estimation via `scipy.stats.genextreme`
* Return level estimation (10, 20, 50, 100 years)
* Q–Q diagnostics
* Return level plots
* Parameter summaries exported to `/results`

Example output:

```
results/mle_quito_temp_me/
results/mle_guayaquil_temp_me/
```

---

### 3️⃣ Batch GEV Modeling Across All Cities

Notebook:
`02_EVT_GEV_MLE_Batch_AllCities.ipynb`

Features:

* Automatic city detection
* Loop over:

  * Cities
  * Variables
  * Block rules (monthly default)
* Progress bars via `tqdm`
* Automatic quality checks:

  * Minimum block count
  * Missingness thresholds
* Exported summary:

```
results/gev_mle_batch_summary.csv
```

This creates a national-level comparison of extreme value behavior.

---

## 📊 Current Status

| Component                  | Status         |
| -------------------------- | -------------- |
| Data Cleaning              | ✅ Complete     |
| EVT Diagnostics            | ✅ Complete     |
| GEV MLE (Single City)      | ✅ Complete     |
| GEV MLE (All Cities Batch) | ✅ Complete     |
| Bayesian EVT               | 🚧 In progress |
| ML Forecasting of Maxima   | 🚧 In progress |

---

## 📈 Example Outputs

* Annual and monthly block maxima plots
* Mean-excess diagnostics
* GEV parameter estimates (μ, σ, ξ)
* Return level curves
* Cross-city comparison tables

---

## 🔮 Next Steps

Planned extensions:

### 🧠 Bayesian EVT

* MCMC estimation of GEV parameters
* Posterior predictive return levels
* Credible intervals

### 🤖 ML Forecasting

* Rolling-window feature engineering
* Prediction of next-block maxima
* Baselines:

  * Persistence
  * Linear regression
  * Gradient boosting
  * LSTM networks

### 📊 Model Comparison

* MAE / RMSE on predicted maxima
* Calibration analysis
* Reliability of return level estimates

---

## ⚙️ Technologies

* Python
* Pandas
* NumPy
* SciPy
* Matplotlib
* Seaborn
* PyArrow
* tqdm
* Jupyter / Colab

---

## 📄 Research Paper

See:

```
Prediction of extreme events in climatic time series.pdf
```

This document describes:

* Theoretical EVT foundations
* Bayesian extension
* Machine learning framework
* Predictive evaluation design

---

## 🌎 Why This Matters

Extreme climatic events are increasing in frequency and intensity.

Reliable modeling of extremes is critical for:

* Climate risk assessment
* Infrastructure planning
* Insurance modeling
* Disaster preparedness

This repository builds a **statistically rigorous and extensible forecasting framework** for extreme climate behavior in Ecuador.

---

## Dataset

The notebook `init_00_ECF_Setup.ipynb` automatically loads the dataset into the directory.  
However, if you need to download it manually:

- **Full dataset (.zip):** https://drive.google.com/file/d/1xPhrvg30Ull9KqtU_3TK6ZJlBSTuaH8A/view?usp=drive_link  
- **Cleaned dataset (.parquet):** https://drive.google.com/file/d/1KPWLNozyStLxfatqiwx30DEYo0bU2zuB/view?usp=sharing

---
