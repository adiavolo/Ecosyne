
# ECOSYNE  
### AI-Powered Environmental Intelligence Platform

> *Democratizing access to satellite intelligence for land-use and environmental monitoring.*

---

## 🌍 Project Overview

**Ecosyne** is a full-stack geospatial analytics platform designed to monitor, analyze, and forecast land-use and environmental changes using satellite imagery. The system transforms complex remote sensing data into clear, actionable insights through interactive maps, time-series analytics, and composite environmental indicators.

The platform focuses on detecting changes in:
- Vegetation cover  
- Water bodies  
- Urban and built-up areas  

To summarize overall environmental health, Ecosyne computes a unified metric called the **Environmental Impact Score (EFI)** and supports trend analysis and forecasting to aid long-term sustainability planning.

---

## 🚀 Key Features

- **🛰️ Satellite Data Integration**  
  Automated ingestion and processing of **Sentinel-2 (Level-2A)** and **Landsat-8** imagery using the Google Earth Engine (GEE).

- **📊 Environmental Impact Score (EFI)**  
  A composite index that quantifies environmental condition by integrating vegetation, urbanization, and thermal indicators into a single interpretable score.

- **🧠 Predictive Trend Forecasting**  
  Time-series forecasting of vegetation health using deep learning models (LSTM) trained on historical satellite-derived indices.

- **🗺️ Interactive Geospatial Dashboard**  
  Web-based visualization with map layers, time comparison sliders, index filtering, and automated report generation.

- **🔍 Land-Use Classification**  
  Machine learning–based land-use segmentation into Vegetation, Water, Urban, and Barren categories using supervised classifiers.

---

## 🛠️ System Architecture

Ecosyne follows a modular, decoupled architecture to ensure scalability, maintainability, and clear separation of concerns.

### 1. Frontend (Visualization Layer)
- **Framework**: React.js (v18)
- **Mapping**: Interactive map layers with temporal comparison
- **Charts**: Dynamic time-series and trend visualizations
- **Styling**: Dark-mode–oriented, minimal UI for analytical clarity

### 2. Backend (Application & Analytics Layer)
- **API Framework**: FastAPI (Python 3.10)
- **Geospatial Processing**: Google Earth Engine API
- **Machine Learning**: TensorFlow / Keras (LSTM forecasting)
- **Validation**: Pydantic for strict schema enforcement

---

## 📂 Project Structure

```text
ecosyne-project/
├── backend/                  # Backend API and analytics core
│   ├── app.py                # FastAPI entry point
│   ├── gee_core.py           # Google Earth Engine processing logic
│   ├── lstm_engine.py        # Time-series forecasting module
│   ├── requirements.txt      # Python dependencies
│   └── service_account.json  # GEE credentials (ignored via .gitignore)
│
├── frontend/                 # React-based user interface
│   ├── public/assets/        # Static assets
│   ├── src/
│   │   ├── App.js            # Dashboard logic
│   │   ├── index.css         # Global styles
│   │   └── index.js          # Application entry point
│   └── package.json          # Node dependencies
│
└── README.md                 # Project documentation
````

---

## ⚙️ Installation and Setup

### Prerequisites

* **Python** 3.9 or higher
* **Node.js** 16+ and npm
* **Google Earth Engine account** with API access

---

### Backend Setup

```bash
cd backend
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Place your Google Earth Engine service account key file (`service_account.json`) inside the `backend/` directory.

Start the backend API:

```bash
uvicorn app:app --reload
```

---

### Frontend Setup

```bash
cd frontend
npm install
npm start
```

The dashboard will be available at:
**[http://localhost:3000](http://localhost:3000)**

---

## 📊 Scientific Methodology

### Satellite Data Processing Pipeline

1. **Cloud Filtering and Masking**

   * Images with excessive cloud coverage are discarded.
   * Remaining clouds and shadows are masked using quality bands (QA/SCL).

2. **Spectral Index Computation**

   * **NDVI (Vegetation Health)**
     `(NIR - Red) / (NIR + Red)`
   * **NDBI (Built-up Detection)**
     `(SWIR - NIR) / (SWIR + NIR)`
   * **MNDWI (Water Detection)**
     `(Green - SWIR) / (Green + SWIR)`

3. **Change Detection**

   * Temporal comparison of index values across user-selected periods.
   * Pixel-level and region-level aggregation of gains and losses.

4. **Environmental Impact Score (EFI)**

   EFI is computed as a normalized composite metric:

   ```
   EFI = 100 − (w₁ × Urban Expansion) + (w₂ × Vegetation Coverage) − (w₃ × Thermal Stress)
   ```

   where `w₁`, `w₂`, and `w₃` are empirically chosen weights.

---

### Forecasting Model

* **Model Type**: Stacked Bidirectional LSTM
* **Architecture**:

  * Two Bi-LSTM layers (64 and 32 units)
  * Dropout regularization (0.2)
  * Fully connected output layer
* **Input Data**: Multi-year NDVI time series derived from satellite imagery
* **Output**: Short- to medium-term vegetation trend forecasts

---

## 📦 Outputs and Deliverables

* Interactive web dashboard
* Land-use change maps
* Environmental Impact Score trends
* Time-series charts and forecasts
* Exportable CSV and PDF reports

---

## 🛡️ License and Credits

**License**: MIT License

**Developed by**:
**TEAM ECOSYNE**

Mahindra University

Capstone Project – 2025

### Acknowledgements

* European Space Agency (ESA) for Sentinel-2 data
* Google Earth Engine for large-scale geospatial processing support


*Ecosyne aims to bridge the gap between satellite data and sustainable decision-making by making environmental intelligence accessible, interpretable, and actionable.*




