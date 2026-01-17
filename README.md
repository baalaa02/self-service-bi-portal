# Self-Service Business Intelligence Portal

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Streamlit](https://img.shields.io/badge/Framework-Streamlit-red)
![Status](https://img.shields.io/badge/Status-Internal%20Tool-success)

## 📖 Overview
The **Self-Service BI Portal** is a full-stack internal tool designed to decouple non-technical stakeholders from data engineering dependencies. 

In many organizations, business teams rely on ad-hoc SQL queries from engineering teams to generate simple reports. This tool democratizes data access by allowing stakeholders to upload raw datasets (CSV/Excel), perform automated schema validation, and generate instant interactive insights without writing a single line of code.

## 🚀 Key Features
* **Automated Validation Pipeline:** Uses `Pandas` to detect schema anomalies, missing values, and type mismatches pre-processing, preventing downstream reporting failures.
* **Instant Visualization:** Generates interactive dashboards automatically based on data types (Time-series for dates, Bar charts for categorical data).
* **SQL Reduction:** Estimated to reduce dependency on ad-hoc engineering queries by **5+ hours/week**.
* **Secure Uploads:** Local-session handling ensures sensitive data is processed in-memory and not persisted unnecessarily.

## 🛠️ Tech Stack
* **Core Logic:** Python 3.9+
* **Frontend/UI:** Streamlit
* **Data Processing:** Pandas, NumPy
* **Visualization:** Plotly Express, Altair

## 📂 Project Structure
```bash
├── app.py               # Main application entry point
├── modules/
│   ├── validator.py     # Schema validation logic
│   └── visualizer.py    # Automated plotting logic
├── requirements.txt     # Project dependencies
└── README.md            # Documentation
