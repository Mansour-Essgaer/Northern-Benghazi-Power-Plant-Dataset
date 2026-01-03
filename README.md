
# Northern Benghazi Electrical Load & Weather Dataset

### A Weather-Informed Electricity Load Forecasting Dataset

## 📌 Overview

The **Northern Benghazi Electrical Load & Weather Dataset** combines historical electricity consumption records with meteorological data for **Benghazi, Libya**.

This dataset was curated to develop and benchmark a **Convolutional Neural Network (CNN)** framework for short-term load forecasting. It integrates specific power plant measurements with external weather data to address the challenges of predicting electricity demand in arid climates where temperature and humidity fluctuations significantly impact grid stability.

## 📊 Dataset Specifications

| Attribute | Value |
| --- | --- |
| **Time Period** | January 1, 2019 – December 31, 2019 |
| **Location** | Benghazi, Libya (Northern Benghazi Power Plant) |
| **Resolution** | Daily |
| **Target Variable** | Electrical Load (MW) |
| **Peak Load** | ~1,600 MW (Summer) |
| **Minimum Load** | ~1,200 MW (Winter) |
| **Key Insight** | Strong correlation between summer temperature spikes and peak load (AC demand). |

---

## 📁 Data Features

The dataset consists of two primary sources: internal measurements from the power plant and external historical weather data.

### 1. Power Plant Data (NBPP)

Collected directly from the Northern Benghazi Power Plant (NBPP).

| Feature | Description | Unit |
| --- | --- | --- |
| **`Load`** | Electrical load at time *t* | Megawatt (MW) |
| **`Temperature`** | Ambient temperature recorded at the plant | Celsius (°C) |
| **`Humidity`** | Relative humidity recorded at the plant | Percentage (%) |

### 2. External Weather Data

Sourced from historical weather and climate archives.

| Feature | Description | Unit |
| --- | --- | --- |
| **`Temperature`** | Regional ambient temperature | Celsius (°C) |
| **`Dew Point`** | Dew point temperature | Celsius (°C) |
| **`Humidity`** | Regional relative humidity | Percentage (%) |
| **`Wind Speed`** | Wind speed | km/h |
| **`Pressure`** | Atmospheric pressure | Inches of Hg |
| **`Precipitation`** | Precipitation level | Millimeters (mm) |

---

## 🧹 Preprocessing Pipeline

To ensure data quality for machine learning tasks, the following preprocessing steps were applied:

* **Humidity Correction:** Normalized erroneous humidity entries to ensure values .
* **Imputation:**
* **Temperature:** Missing values replaced with the mode of observed values.
* **Humidity:** Missing values assumed to be zero.


* **Feature Engineering:** Added a `Day-of-Year` () feature to capture seasonal variations.
* **Normalization:** Features were normalized to address scale variance between MW loads and weather units.

---

## 🧪 Benchmark Results

The dataset was used to train a **CNN model** optimized with the **Hyperband** algorithm and interpreted using **SHAP (SHapley Additive exPlanations)**.

| Metric | Score |
| --- | --- |
| **Test  (Coefficient of Determination)** | **0.93** |
| **Test RMSE (Root Mean Squared Error)** | **12.4 MW** |
| **Validation Loss** | 1.146 MW |

### Key Findings

* **Temperature** was identified as the dominant predictor for load demand.
* **Humidity** showed nonlinear interactions with load demand, particularly distinguishable when using SHAP analysis.
* The optimized CNN outperformed baseline statistical methods and standard machine learning configurations.

---

## 📚 Citation

If you use this dataset or the methodology in your research, please cite the original paper:

```bibtex
@InProceedings{10.1007/978-3-032-00232-7_11,
author="Essgaer, Mansour
and Agaal, Asma
and Matoug, Mohamed",
title="Integrating SHapley Additive ExPlanations and Hyperparameter Tuning in Weather-Informed Electricity Load Forecasting: A Case Study of Northern Benghazi Power Plant",
booktitle="Selected Papers from the International Conference on Artificial Intelligence",
year="2026",
publisher="Springer Nature Switzerland",
address="Cham",
pages="166--187",
isbn="978-3-032-00232-7"
}

```
---

## 📄 License

This data is associated with the research presented in the paper. Please refer to the original authors for specific usage rights and licensing information.
