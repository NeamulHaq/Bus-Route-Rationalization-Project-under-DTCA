# 🚌 Bus Route Rationalization Project under DTCA

### DTCA / BRR Bus Survey Data Analysis

> **Data-driven analysis of passenger demand, occupancy, route performance, stop-level activity, peak-hour pressure, and bus operational performance for the Bus Route Rationalization (BRR) Project under the Dhaka Transport Coordination Authority (DTCA).**

---

## 📊 Project Overview

This project provides a comprehensive analytical framework for examining **bus survey data** collected for the **Bus Route Rationalization (BRR) Project under DTCA**.

The analysis uses Python-based data processing and statistical exploration to understand:

* 🧑‍🤝‍🧑 Passenger demand and movement
* 🚌 Bus occupancy and passenger loading
* 🛣️ Route-level performance
* 📍 Stop-level passenger demand
* ⏰ Peak-hour passenger pressure
* ⏱️ Travel-time performance
* 🛑 Dwell-time characteristics
* ⚠️ Data-quality and passenger-flow anomalies

The project is designed to distinguish **actual transportation patterns** from **data-quality issues**, ensuring that anomalies are identified and investigated rather than silently removed.

---

## 🎯 Analytical Objectives

The analysis is organized around five primary analytical areas:

| Priority | Analysis                            | Objective                                       |
| :------: | ----------------------------------- | ----------------------------------------------- |
|   ⭐⭐⭐⭐⭐  | 🧑‍🤝‍🧑 Passenger Flow & Occupancy | Understand passenger demand and vehicle loading |
|   ⭐⭐⭐⭐⭐  | 🚌 Route Performance                | Compare performance across bus routes           |
|   ⭐⭐⭐⭐⭐  | 📍 Stop Demand                      | Identify high-demand and critical stops         |
|   ⭐⭐⭐⭐   | ⏰ Peak-Hour Analysis                | Identify periods of high passenger pressure     |
|   ⭐⭐⭐⭐   | ⏱️ Travel & Dwell Time              | Identify operational bottlenecks                |

---

# 🔍 Data Quality Assessment

The initial dataset contains:

| Metric            |  Value |
| ----------------- | -----: |
| **Records**       | 20,496 |
| **Variables**     |     13 |
| **Unique Routes** |     98 |
| **Unique Trips**  |     20 |
| **Unique Stops**  |    311 |

### ⚠️ Initial Data-Quality Findings

The initial audit identified several important issues:

| Data-quality issue   | Records | Percentage |
| -------------------- | ------: | ---------: |
| Duplicate records    |     370 |      1.81% |
| Missing `Distance`   |  20,496 |    100.00% |
| Missing `Time`       |   5,353 |     26.12% |
| Missing `Trip_ID`    |      45 |      0.22% |
| Negative Travel Time |       7 |          — |
| Negative Dwell Time  |       3 |          — |
| Negative Occupancy   |     164 |          — |

### Data-quality principle

> **Anomalous observations are investigated before removal.**

Negative travel time, negative dwell time, negative occupancy, missing trip identifiers, missing timestamps, and duplicate observations are retained during the audit so their potential causes can be evaluated.

This prevents potentially meaningful operational or passenger-flow information from being lost through premature cleaning.

---

# 🧑‍🤝‍🧑 Passenger Flow & Occupancy Analysis

Passenger movement is analyzed using several complementary measures:

### Passenger variables

* **Boarding** — passengers entering the bus at a stop
* **Alighting** — passengers leaving the bus at a stop
* **Passenger Activity** — total boarding + alighting
* **Net Passenger Change** — boarding − alighting
* **Observed Occupancy** — recorded passenger load
* **Reconstructed Occupancy** — occupancy estimated from passenger-flow sequences
* **Occupancy Consistency** — comparison between observed and reconstructed passenger loads

### Key diagnostic analysis

The project specifically investigates:

* Negative occupancy
* Occupancy inconsistent with passenger movements
* Occupancy equal to `Boarding − Alighting`
* Passenger-flow discontinuities
* Potential trip-level inconsistencies
* Potential route-level inconsistencies
* Missing trip identifiers affecting reconstruction

The objective is to determine whether unusual occupancy values represent:

1. Genuine passenger-flow conditions,
2. Survey/data-entry issues,
3. Trip sequencing problems, or
4. Other data-processing anomalies.

---

# 🚌 Route Performance Analysis

Routes are evaluated using a combination of passenger, operational, and data-quality indicators.

### Route-level indicators

* Total boarding
* Total alighting
* Passenger activity
* Mean occupancy
* Maximum occupancy
* Number of stops
* Number of records
* Travel time
* Dwell time
* Negative occupancy rate
* Occupancy variability
* Passenger demand concentration

This enables comparison between routes and identification of routes experiencing:

> **High passenger demand + high occupancy + operational pressure**

---

# 📍 Stop-Level Demand Analysis

Stop-level analysis identifies locations where passenger demand and operational pressure are concentrated.

### Stop indicators

* Total boarding
* Total alighting
* Total passenger activity
* Mean occupancy
* Maximum occupancy
* Number of observations
* Route coverage
* Passenger-flow characteristics
* Peak-period demand

This analysis can help identify:

* 🔴 Critical high-demand stops
* 🟠 High passenger-activity locations
* 🟡 Potential congestion points
* 🟢 Lower-demand locations

The results can support further investigation of **stop consolidation, route restructuring, service frequency, and operational planning**.

---

# ⏰ Peak-Hour Analysis

Available timestamp information is converted into analytical time periods.

### Time-period classification

| Period            | Time                  |
| ----------------- | --------------------- |
| 🌅 Early Morning  | Before 06:00          |
| 🚍 Morning Peak   | 06:00–08:59           |
| ☀️ Morning        | 09:00–11:59           |
| 🕛 Midday         | 12:00–14:59           |
| 🚍 Afternoon Peak | 15:00–17:59           |
| 🌆 Evening        | 18:00–20:59           |
| 🌙 Night          | 21:00 onward          |
| ❓ Unknown         | Missing/unusable time |

Missing time values are **not silently discarded**. They are retained as `Unknown` so that the impact of missing timestamps can be evaluated separately.

Peak-hour analysis examines:

* Passenger activity
* Boarding
* Alighting
* Occupancy
* Route demand
* Stop demand
* Travel time
* Dwell time

---

# ⏱️ Travel & Dwell-Time Performance

Operational performance is evaluated using:

### Travel Time

Time required for movement between surveyed observations/stops.

### Dwell Time

Time associated with passenger/service activity at the surveyed location.

The analysis investigates:

* Average travel time
* Median travel time
* Route-level travel time
* Stop-level dwell time
* Peak-period travel time
* Peak-period dwell time
* Extreme values
* Negative values
* Potential operational bottlenecks

Negative values are retained for **data-quality diagnostics** but excluded from operational calculations where they cannot represent physically meaningful durations.

---

# 🧪 Data Validation Philosophy

The project follows a staged analytical approach:

```text
Raw Survey Data
       │
       ▼
Data Quality Audit
       │
       ├── Missing Values
       ├── Duplicates
       ├── Invalid Values
       ├── Negative Values
       └── Structural Issues
       │
       ▼
Data Validation
       │
       ▼
Passenger Flow Reconstruction
       │
       ▼
Occupancy Consistency Analysis
       │
       ▼
Route Performance
       │
       ▼
Stop Demand
       │
       ▼
Peak-Hour Analysis
       │
       ▼
Travel / Dwell-Time Analysis
       │
       ▼
Integrated Route–Stop Dashboard
```

---

# 🛠️ Technologies

The project uses the following tools and technologies:

| Technology              | Purpose                           |
| ----------------------- | --------------------------------- |
| 🐍 **Python**           | Data analysis and processing      |
| 🐼 **Pandas**           | Data manipulation and analysis    |
| 🔢 **NumPy**            | Numerical computation             |
| 📊 **Matplotlib**       | Data visualization                |
| 📓 **Jupyter Notebook** | Interactive analysis              |
| 🌿 **Git**              | Version control                   |
| 🐙 **GitHub**           | Project hosting and collaboration |

---

# 📁 Repository Structure

```text
DTCA-BRR-Bus-Survey-Analysis/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   └── DTCA_BRR_Passenger_Flow_Analysis.ipynb
│
├── data/
│   └── README.md
│
├── outputs/
│   ├── figures/
│   └── tables/
│
└── src/
    └── analysis/
```

### Folder descriptions

**`notebooks/`**
Contains Jupyter notebooks used for exploratory and analytical work.

**`data/`**
Reserved for authorized local copies of the survey dataset.

**`outputs/figures/`**
Contains generated charts and visualizations.

**`outputs/tables/`**
Contains analytical summary tables and exported results.

**`src/`**
Reserved for reusable Python analysis modules and processing functions.

---

# 🔐 Data Availability

The underlying survey dataset is **not included in this public repository** unless publication and redistribution have been explicitly authorized.

The analysis notebook is structured so that an authorized user can place the dataset in the appropriate local data directory before execution.

### Privacy & reproducibility

Local machine-specific paths should not be embedded in the notebook.

For example, instead of using:

```python
E:\DTCA Project\BRR Project\Survey Data\...
```

the project should use a relative project path such as:

```python
from pathlib import Path

DATA_PATH = Path("../data/All_Processed_Survey_Data_Conda.csv")
```

This makes the notebook portable across computers and suitable for GitHub.

---

# 📈 Current Analytical Status

### ✅ Completed

* [x] Dataset loading
* [x] Dataset structure assessment
* [x] Missing-value audit
* [x] Duplicate-record audit
* [x] Unique-value analysis
* [x] Numeric-variable profiling
* [x] Negative-value diagnostics
* [x] Zero-value analysis
* [x] Coordinate validation
* [x] Passenger-variable assessment
* [x] Route and trip assessment
* [x] Time-variable assessment
* [x] Negative occupancy investigation
* [x] Occupancy consistency analysis

### 🔄 Current Stage

* [x] Passenger-flow reconstruction
* [x] Passenger-flow validation
* [ ] Route performance analysis
* [ ] Stop-demand analysis
* [ ] Peak-hour analysis
* [ ] Travel/dwell-time performance analysis
* [ ] Integrated route–stop dashboard

---

# 🗺️ Analytical Roadmap

The next stages of the project are:

### Phase 1 — Passenger Flow

Reconstruct passenger movement through stop sequences and validate observed occupancy.

### Phase 2 — Route Performance

Rank and compare routes using passenger demand, occupancy, travel time, dwell time, and data-quality indicators.

### Phase 3 — Stop Demand

Identify critical passenger-demand locations and high-pressure stops.

### Phase 4 — Temporal Demand

Examine passenger activity and occupancy by time of day and peak periods.

### Phase 5 — Operational Performance

Identify potential travel-time and dwell-time bottlenecks.

### Phase 6 — Integrated Dashboard

Develop a route–stop analytical dashboard combining:

```text
Route
  +
Stop
  +
Passenger Demand
  +
Occupancy
  +
Time
  +
Operational Performance
  +
Data Quality
```

---

# 📊 Expected Analytical Outputs

The completed project is intended to produce:

* 📈 Passenger-flow visualizations
* 🚌 Route performance rankings
* 📍 Stop-demand rankings
* ⏰ Peak-hour demand profiles
* 👥 Occupancy distributions
* ⏱️ Travel-time analysis
* 🛑 Dwell-time analysis
* 🗺️ Spatial passenger-demand analysis
* ⚠️ Data-quality diagnostics
* 📊 Route–stop performance dashboard

---

# 💡 Potential Applications

The analytical results may support further investigation into:

* Bus route restructuring
* Passenger-demand concentration
* Service frequency planning
* High-demand stop identification
* Route performance comparison
* Peak-period service planning
* Operational bottleneck identification
* Passenger-flow balancing
* Bus network rationalization

> **Important:** Analytical findings should be interpreted alongside survey methodology, operational context, field observations, and relevant transport-planning criteria before being used for policy or network-design decisions.

---

# 👤 Author

**A. T. M. Neamul**

---

# 📜 License

An appropriate license should be added after confirming:

1. Ownership of the analytical code,
2. Publication rights,
3. Redistribution conditions for derived outputs, and
4. Any restrictions associated with the underlying survey data.

---

## ⭐ Project Status

**🚧 Active Development**

This repository documents an ongoing analytical workflow for the **DTCA / BRR Bus Survey Data Analysis Project**.

The analysis will continue to evolve as passenger-flow validation, route performance, stop-demand, temporal, operational, and dashboard analyses are completed.

---

### 🚌 DTCA / BRR Bus Survey Analysis

**Turning survey observations into evidence for understanding passenger demand, route performance, and bus network operations.**
