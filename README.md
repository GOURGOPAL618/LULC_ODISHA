# 🌍 Automated LULC Classification: Odisha Coastal Zone
An advanced Remote Sensing and Machine Learning pipeline to classify Land Use Land Cover (LULC) across the ecologically sensitive coastal ecosystem of Odisha, stretching from **Chilika Lake** to **Bhitarkanika National Park**.

---

## 🚀 Project Objective
The goal of this project is to build an automated machine learning workflow that ingests multi-spectral satellite data, performs advanced feature engineering, and classifies highly complex coastal features (such as dense mangroves, brackish water lagoons, and urban concrete) with high spatial accuracy.

---

## 🗺️ Study Area & Data Architecture
* **Region:** Odisha Coast, India (Chilika Lake ➔ Puri ➔ Jagannath Highway ➔ Paradeep ➔ Bhitarkanika)
* **Satellite Sensors:** Sentinel-2 Surface Reflectance (Multi-Spectral Instrument - MSI)
* **Temporal Window:** November 2023 – February 2024 (Dry winter window optimized for cloud-free composite mapping)
* **Input Resolving Scale:** 10-meter spatial resolution

---

## 📊 Target Classes & Ground Truth Design
The model is trained on **50 pure-pixel high-altitude localized training polygons** collected across five distinct macro-classes:

| Class Code | Class Name | Target Features & Geolocation Details |
| :---: | :--- | :--- |
| **0** | **Water** | Deep Ocean blue water and brackish, shallow waters of Chilika Lake. |
| **1** | **Mangrove** | Dense, core halophytic forest patches inside Bhitarkanika National Park. |
| **2** | **Paddy Field** | Harvested rural agricultural plots and regular rectangular dry crop layouts. |
| **3** | **Urban** | Concrete rooftops, infrastructure clusters in Puri, Railway Station, and the Jagannath Highway corridor. |
| **4** | **Bare Sand** | Highly reflective coastal beach sand lines along Puri-Konark and dry riverbeds. |

---

## 🛠️ Machine Learning Pipeline Architecture
The project executes a modular end-to-end processing pipeline:
1. **Data Ingestion & Cloud Masking:** Google Earth Engine (GEE) automated median composite generation (<15% cloud score filter).
2. **Feature Engineering (Spectral Stacking):** Computing and stacking Core Bands ($B2, B3, B4, B8, B11$) with Normalized Indices:
   * **NDVI** (Normalized Difference Vegetation Index) for Mangrove separation.
   * **NDWI** (Normalized Difference Water Index) for Lagoon/Ocean extraction.
   * **NDBI** (Normalized Difference Built-up Index) for Highway and Urban targeting.
3. **Spatial Validation Split:** Vector formatting and splitting to mitigate spatial autocorrelation risks.
4. **Core Classifier Engine:** `Scikit-Learn` Random Forest Classifier ($n\_estimators=100$) executed via Google Colab.
5. **Validation Matrix:** Generating Confusion Matrix, Precision, Recall, and F1-score dashboards.

---

## 📂 Project Directory Structure
```text
LULC_Odisha_Project/
├── data/                          <-- Raw Sentinel-2 Multi-spectral GeoTIFF
├── vectors/                       <-- Training Samples / Ground Truth Tables
├── notebooks/                     <-- Core Google Colab ML Pipelines (.ipynb)
└── outputs/                       <-- Classified GeoTIFF Maps & Accuracy Reports
