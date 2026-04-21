# 🚦 TrafficMine — Traffic Violation Analysis & Risk Prediction

**Data Mining & Data Warehousing — College Project**

**Developed By-** Shriwayanta Maiti, Harshal Nanekar

---

## 📁 Project Structure

```
DMWproject/
├── app.py                  # Main Streamlit entry point
├── requirements.txt        # Python dependencies
├── data/
│   └── violations.csv      # Auto-generated warehouse (CSV)
├── modules/
│   ├── data_store.py       # CSV-backed Data Warehouse simulation
│   ├── preprocessing.py    # Data cleaning & encoding
│   ├── clustering.py       # K-Means clustering engine
│   ├── insights.py         # Insight generator
│   ├── charts.py           # Plotly chart builders
│   └── styles.py           # CSS dark theme injection
└── pages/
    ├── dashboard.py        # Home dashboard with KPIs
    ├── add_violation.py    # Data input form
    ├── analytics.py        # Deep-dive analytics
    ├── mining.py           # Mining engine (K-Means)
    └── warehouse.py        # Star schema explorer
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

## 🧩 Features (MVP Complete)

| Feature | Status |
|---|---|
| Data Input Form (Area, Type, Time) | ✅ |
| CSV-backed warehouse (Star Schema) | ✅ |
| Data Preprocessing & Encoding | ✅ |
| K-Means Clustering (k=2-5) | ✅ |
| High / Medium / Low Risk zones | ✅ |
| Bar chart — violations per area | ✅ |
| Pie chart — violation distribution | ✅ |
| Hourly / Daily / Monthly trends | ✅ |
| Heatmap — Area × Violation type | ✅ |
| Insight: High risk area, peak time | ✅ |
| Star Schema explorer | ✅ |
| OLAP Aggregations | ✅ |
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

### Data Mining

- **Algorithm:** K-Means Clustering (scikit-learn)
- **Input Features:** total_violations, avg_severity, avg_hour, unique_types
- **Output:** 3 risk clusters → High / Medium / Low Risk

---

## 📌 Pages

1. **🏠 Dashboard** — KPI cards + area/type/hour charts + insight summary
2. **📝 Add Violation** — Form with area, type, date & hour selector
3. **📊 Analytics** — Filtered charts + heatmap + top-5 table
4. **🔬 Mining Engine** — K-Means scatter, risk gauges, preprocessed data
5. **🗄️ Data Warehouse** — Star schema diagram + Fact/Dim tables + OLAP queries
