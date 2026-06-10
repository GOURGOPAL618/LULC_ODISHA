# 📡 Earth Observation Data Governance & Sensor Metadata Registry

---

## 📌 1. Data Provenance & Sensor Attribution
The multispectral imagery array utilized in this analytical execution framework is sourced directly from the European Space Agency (ESA) Copernicus Data Space Ecosystem. 

* **Spacecraft Platform:** Sentinel-2A / Sentinel-2B
* **Instrument Payload:** Multi-Spectral Instrument (MSI)
* **Processing Level:** Level-2A (Bottom-of-Atmosphere / Surface Reflectance)
* **Geometric Reference Frame:** UTM Zone 45N / EPSG:32645 (WGS 84 coordinate baseline)

---

## 🔍 2. Radiometric & Spatial Resolution Matrix
The feature space configuration ($X$) ingested into the machine learning ensemble isolates the target electromagnetic spectrum bands under strict spatial pixel limits:

| Sensor Band ID | Central Wavelength (nm) | Spatial Resolution | Spectrum Classification |
| :--- | :--- | :--- | :--- |
| **B02** | 490 nm | 10 Meters | Visible Blue |
| **B03** | 560 nm | 10 Meters | Visible Green |
| **B04** | 665 nm | 10 Meters | Visible Red |
| **B08** | 842 nm | 10 Meters | Near-Infrared (NIR) |
| **B11** | 1610 nm | 20 Meters (Upsampled) | Shortwave Infrared (SWIR-1) |

---

## 🛑 3. Cloud Cover Masking & QA Protocols
* **Max Cloud Threshold:** Grid frame scenes were filtered at `< 5.0%` absolute cloud density limits to minimize atmospheric scattering.
* **Pixel Quality Assurance:** SCL (Scene Classification Layer) masks were applied to decouple shadow matrices, heavy water vapor bands, and high-altitude cirrus interference before pipeline deployment.
