# Bus-Route-Rationalization-Project-under-DTCA
DTCA / BRR Bus Survey Data Analysis
Overview

This project analyzes bus survey data to understand passenger demand, occupancy patterns, route performance, stop-level demand, peak-hour pressure, and operational characteristics.

The analysis is implemented using Python, Pandas, NumPy, Matplotlib, and Jupyter Notebook.

Analytical Objectives

The project focuses on five primary analytical areas:

Passenger flow and occupancy
Route performance
Stop-level passenger demand
Peak-hour analysis
Travel and dwell-time performance
Data Quality Assessment

The initial dataset contains:

20,496 records
13 variables
98 unique routes
20 unique trips
311 unique stops

The initial data-quality audit identified:

370 duplicate records
100% missing values in Distance
5,353 missing Time values
45 missing Trip_ID values
7 negative travel-time values
3 negative dwell-time values
164 negative occupancy values

These issues are explicitly investigated rather than silently removed.

Passenger Flow Analysis

Passenger flow is evaluated using:

Boarding
Alighting
Net passenger change
Observed occupancy
Reconstructed occupancy
Occupancy consistency
Negative occupancy diagnostics

The purpose is to distinguish genuine passenger-flow patterns from data-quality anomalies.

Route Performance

Routes are compared using:

Passenger activity
Boarding
Alighting
Mean occupancy
Maximum occupancy
Number of stops
Number of records
Travel time
Dwell time
Negative occupancy rate
Stop Demand

Stop-level analysis identifies locations with:

High boarding demand
High alighting demand
High passenger activity
High observed occupancy
Potential operational pressure
Peak-Hour Analysis

The analysis categorizes observations into time periods such as:

Early Morning
Morning Peak
Morning
Midday
Afternoon Peak
Evening
Night

Missing time values are retained and treated separately.

Operational Performance

Travel time and dwell time are analyzed to identify potential operational bottlenecks.

Invalid negative values are retained in the audit but excluded from calculations where appropriate.

Technologies
Python
Pandas
NumPy
Matplotlib
Jupyter Notebook
Git
GitHub
Repository Structure
DTCA-BRR-Bus-Survey-Analysis/
│
├── README.md
├── notebooks/
├── data/
├── outputs/
│   ├── figures/
│   └── tables/
├── src/
└── requirements.txt
Data Availability

The underlying survey dataset is not included in this repository unless publication and redistribution have been authorized.

The notebook is structured so that an authorized user can place the dataset in the appropriate local data directory before execution.

Status

Current analytical stage:

Passenger-flow reconstruction and validation

Planned next stages:

Route performance analysis
Stop demand analysis
Peak-hour analysis
Travel/dwell-time analysis
Integrated route-stop dashboard
Author
A. T. M Neamul

License

Add an appropriate license after confirming the ownership and publication conditions of the analysis and underlying data.
