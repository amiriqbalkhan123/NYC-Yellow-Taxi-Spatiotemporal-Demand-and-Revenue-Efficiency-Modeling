# NYC Yellow Taxi Spatiotemporal Demand and Revenue Efficiency Modeling

📌 **Project Overview**

This project analyzes one full year of NYC Yellow Taxi trip data (Dec 2024 – Nov 2025) sourced from the official New York City Taxi and Limousine Commission.

The objective is to quantify:

- Temporal demand dynamics  
- Geographic revenue concentration  
- Operational efficiency patterns  
- Determinants of driver earnings  

The final dataset contains 30+ million validated trips, processed through a structured and reproducible data pipeline.

---

🗂 **Data Engineering & Preparation**

Each monthly dataset was:

- Schema-aligned and datatype standardized  
- Timestamp validated (pickup & dropoff integrity)  
- Financial attributes precision-checked  
- Invalid trips removed (negative duration, unrealistic distances, inconsistent fares)  
- Duplicate and null density validated  

Derived performance metrics include:

- `trip_duration_min`  
- `revenue_per_trip`  
- `revenue_per_mile`  
- `revenue_per_minute`  

After validation, monthly files were consolidated into a unified master dataset for large-scale modeling.

---

🏗 **Aggregation Architecture**

To ensure computational efficiency at scale, a multi-layer aggregation framework was implemented:

- Hourly Summary  
- Daily Summary  
- Monthly Summary  
- Borough & Zone Summary (5 boroughs, 260 zones)  

Each aggregation layer includes:

- Total trips  
- Total revenue  
- Average & median duration  
- Revenue share %  
- Trip share %  
- Revenue per trip  
- Revenue per minute  

This structure enables hierarchical temporal and geographic analysis while maintaining economic interpretability.

---

🌍 **Geographic & Revenue Insights**

The analysis reveals clear spatial revenue asymmetry across New York City:

- Revenue share is not proportional to trip share.  
- Some boroughs generate higher revenue relative to demand volume.  
- High-volume zones are not always high-efficiency zones.  
- Revenue density is geographically concentrated in specific clusters.  

These findings demonstrate measurable spatial inequality in earnings potential across the taxi ecosystem.

---

⏱ **Temporal & Efficiency Findings**

Efficiency was measured using:

- Revenue per trip  
- Revenue per minute  

Key findings:

- Peak demand hours are not necessarily peak efficiency hours.  
- Congestion reduces revenue intensity despite high trip volume.  
- Certain lower-volume periods yield stronger earnings per minute.  
- Efficiency is governed by time-location interaction effects.  

Taxi earnings depend heavily on where and when drivers operate, not solely on demand volume.

---

📈 **Modeling Framework**

To quantify determinants of efficiency, multiple modeling approaches were applied:

**Linear Modeling**
- OLS regression (baseline)  
- Ridge regression (regularization)  
- Lasso regression (feature selection)  

Regularization improved out-of-sample performance and stabilized coefficient estimates.

**Ensemble Modeling**
- Random Forest regression for nonlinear interaction capture  
- Feature importance analysis  
- Hierarchical dependency modeling  

Results show that efficiency outcomes are driven by nonlinear interactions between time, geography, and demand intensity.

---

🧠 **Clustering & Operational Regimes**

Clustering techniques were applied to borough-hour efficiency profiles, identifying distinct earning regimes characterized by:

- High-demand / low-efficiency  
- Moderate-demand / high-efficiency  
- Revenue-dense spatial clusters  

These regimes represent structurally differentiated operating environments within the NYC taxi system.

---

🏛 **Business Implications**

This analysis provides evidence-based insights for:

- Driver location strategy optimization  
- Fleet allocation planning  
- Congestion impact assessment  
- Revenue concentration analysis  
- Urban mobility performance evaluation  

The results demonstrate that taxi system performance is shaped by structural temporal patterns, spatial revenue concentration, and nonlinear efficiency dynamics.

---

🛠 **Technical Stack**

- Python  
- Pandas / NumPy  
- Scikit-learn  
- Parquet data architecture  
- GeoJSON spatial analysis  
- Jupyter Notebook workflow  

---

📊 **Project Structure**

The repository is organized into:

- `data/` – intermediate and modeling-ready datasets  
- `notebooks/` – cleaning, aggregation, feature engineering, analytics, and modeling  

Structured monthly pipelines with validation checkpoints.  
Designed for reproducibility, scalability, and modular analysis.

---

📂 **Raw Datasets**

The original NYC Yellow Taxi trip records can be downloaded directly from the official NYC Taxi & Limousine Commission portal:  
👉 [NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
