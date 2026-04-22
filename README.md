# 🚦 TrafficMine — Traffic Violation Analysis & Risk Prediction

**Data Mining & Data Warehousing — College Project**

**Developed By-** Shriwayanta Maiti, Harshal Nanekar

---

## 📁 Project Structure

```
TrafficMine/
├── app.py                    # Main Streamlit entry point & page router
├── requirements.txt          # Python dependencies
├── data/
│   └── violations.csv        # Auto-generated warehouse (CSV)
├── modules/
│   ├── data_store.py         # CSV-backed Data Warehouse simulation
│   ├── preprocessing.py      # Data cleaning & encoding
│   ├── clustering.py         # K-Means clustering engine
│   ├── association.py        # Apriori association rule mining (mlxtend)
│   ├── anomaly.py            # Z-Score anomaly detection
│   ├── insights.py           # Insight generator
│   ├── charts.py             # Plotly chart builders
│   └── styles.py             # CSS dark theme injection
└── pages/
    ├── dashboard.py          # Home dashboard with KPIs
    ├── add_violation.py      # Data input form
    ├── analytics.py          # Deep-dive analytics
    ├── mining.py             # Mining engine (K-Means)
    ├── association.py        # Association Rules Mining page
    ├── anomaly.py            # Anomaly Detection page
    ├── olap.py               # OLAP Operations page
    └── warehouse.py          # Star schema explorer
```

---

## 🚀 How to Run

### Step 1 — Install dependencies

```bash
pip install -r requirements.txt
```

### Step 2 — Launch the app

```bash
streamlit run app.py
```

Then open **http://localhost:8501** in your browser.

---

## 🧩 Features

| Feature | Status |
|---|---|
| Data Input Form (Area, Type, Time) | ✅ |
| CSV-backed warehouse (Star Schema) | ✅ |
| Data Preprocessing & Encoding | ✅ |
| K-Means Clustering (k=2–5) | ✅ |
| High / Medium / Low Risk zones | ✅ |
| Bar chart — violations per area | ✅ |
| Pie chart — violation distribution | ✅ |
| Hourly / Daily / Monthly trends | ✅ |
| Heatmap — Area × Violation type | ✅ |
| Insight: High risk area, peak time | ✅ |
| Star Schema explorer | ✅ |
| **Association Rule Mining (Apriori)** | ✅ |
| **Anomaly Detection (Z-Score)** | ✅ |
| **OLAP Operations (Roll-up, Drill-down, Slice, Dice, Pivot)** | ✅ |
| Dark premium UI | ✅ |
| Pre-seeded with 320 sample records | ✅ |

---

## 🏗️ Architecture

### Data Warehousing (Star Schema)

```
         DIM_AREA
            ↑
DIM_TIME → FACT_VIOLATIONS ← DIM_VIOLATION
```

**Fact Table:** violations — stores area_id, time_id, violation_type_id, severity

**Dimension Tables:**
- `DIM_AREA` — area name, coordinates
- `DIM_TIME` — date, hour, day, month
- `DIM_VIOLATION` — type name, category, severity score

---

### Data Mining — K-Means Clustering

- **Algorithm:** K-Means Clustering (scikit-learn)
- **Input Features:** total_violations, avg_severity, avg_hour, unique_types
- **Output:** 3 risk clusters → High / Medium / Low Risk

---

### Association Rule Mining — Apriori

- **Algorithm:** Apriori (mlxtend library)
- **Transaction Definition:** All violation types occurring on the same day in the same area form one transaction
- **Mining Modes:** By violation type co-occurrence **or** by area co-occurrence
- **Tunable Parameters:** Min Support, Min Confidence, Min Lift
- **Output:**
  - Frequent itemsets with support values
  - Association rules with Support, Confidence & Lift metrics
  - Confidence vs Lift scatter plot
  - Top discovered rules with human-readable IF → THEN format

---

### Anomaly Detection — Z-Score

- **Method:** Z-Score statistical analysis
- **Formula:** `Z = (X − μ) / σ`
- **Adjustable Threshold:** 1.0 – 3.5 (default 2.0, flags ~top/bottom 2.5%)
- **Detection Dimensions:**

| Dimension | What it detects |
|---|---|
| **By Area** | Areas with abnormally high or low violation counts |
| **By Date** | Days with unusual spikes or drops in violations |
| **By Hour** | Hours of the day with anomalous activity |
| **By Violation Type** | Violation categories occurring far above/below average |

- **Output:**
  - Colour-coded bar charts (🔴 High Anomaly / 🔵 Low Anomaly / ✅ Normal)
  - Z-Score bar charts with threshold lines (±σ)
  - Time-series line charts with anomaly markers
  - KPI cards (anomalous count, max |Z-Score|, anomaly rate)
  - Detailed anomaly summary tables

---

### OLAP Operations

Five core OLAP operations on the data warehouse:

| Operation | Description | Example |
|---|---|---|
| **Roll-up** | Aggregate to a higher granularity level | Hour → Time Period → Day → Month → Quarter → Year |
| **Drill-down** | Expand to a lower granularity level | Year → Quarter → Month → Hourly breakdown |
| **Slice** | Fix ONE dimension to a single value | Only `violation_type = 'Drunk Driving'` |
| **Dice** | Filter on MULTIPLE dimensions simultaneously | Area + Month + Violation Type + Time Period |
| **Pivot** | Rotate dimensions (rows ↔ columns) | Rows = Area, Columns = Violation Type |

- **Aggregations available:** Count, Mean Severity, Sum Severity
- **Visualisations:** Bar charts, line charts, pie charts, stacked bars, heatmaps, pivot tables

---

## 📌 Pages

1. **🏠 Dashboard** — KPI cards + area/type/hour charts + insight summary
2. **📝 Add Violation** — Form with area, type, date & hour selector
3. **📊 Analytics** — Filtered charts + heatmap + top-5 table
4. **🔬 Mining Engine** — K-Means scatter, risk gauges, preprocessed data
5. **🔗 Association Rules** — Apriori mining, frequent itemsets, confidence vs lift, top rules
6. **🚨 Anomaly Detection** — Z-Score analysis across area, date, hour & violation type
7. **📦 OLAP Operations** — Roll-up, Drill-down, Slice, Dice & Pivot with interactive controls
8. **🗄️ Data Warehouse** — Star schema diagram + Fact/Dim tables + OLAP queries

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Streamlit |
| Visualisation | Plotly |
| Clustering | scikit-learn (K-Means) |
| Association Rules | mlxtend (Apriori) |
| Anomaly Detection | NumPy / Pandas (Z-Score) |
| Data Storage | CSV (star-schema simulation) |
| Styling | Custom CSS (dark theme) |
