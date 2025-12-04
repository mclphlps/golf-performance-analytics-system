# 🏌️‍♂️ Golf Performance Analytics System
> A consulting-grade analytics pipeline that transforms 15 years of personal GolfShot performance data into governed, reproducible insights.

**Author:** Mike Phillips  
**Program:** [NewForce WV Data Analytics Bootcamp](https://generationwv.org/our-work/newforce/) — *July–December 2025*  
**Environment:** `golfcapstone` (Conda)  
**Languages / Tools:** Python · pandas · GeoPandas · Folium · Matplotlib · Power BI · JupyterLab  

---

## 📘 Overview

This project demonstrates how a professional analytics team would design, document, and deliver a **governed data-engineering pipeline** for sports performance.  
It applies **Six Sigma DMAIC** and **CRISP-DM** methodologies to model a reproducible end-to-end process — from raw GolfShot exports to validated, analysis-ready datasets enriched with geospatial and temporal intelligence.

The resulting workflow is:

- **Transparent** – every transformation is logged and auditable  
- **Reproducible** – environment and data lineage fully captured  
- **Secure** – raw and private data never leaves the local machine  
- **Actionable** – outputs ready for dashboards and modeling  

---

## 🧭 Project Objectives

- Quantify **distance, dispersion, and scoring trends** using 15 years of GolfShot data  
- Identify **consistency patterns** and practice priorities through statistical profiling  
- Integrate **geospatial and temporal context** (facility, time-zone, seasonality)  
- Build a **governed pipeline** with explicit validation, logging, and assumptions  
- Deliver **analysis-ready datasets** for Phase 4 (Visualization) and Phase 5 (Improvement)

---

## ⚙️ Environment Setup

This project runs inside a reproducible Conda environment.

```bash
conda env create -f environment.yml
conda activate golfcapstone
jupyter lab
```

Required libraries:  
`pandas`, `geopandas`, `matplotlib`, `folium`, `timezonefinder`, `python-dotenv`, `requests`

---

## 🔐 API Key Configuration

The project enriches facility data using the **Golf Course API**.

```bash
cp .env.example .env
```

Edit `.env`:

```
GOLF_API_KEY=YOUR_KEY_HERE
```

The `.env` file is excluded from version control to protect secrets.

---

## 🧩 Project Structure

```
golf-capstone/
│
├─ environment.yml
├─ .env.example
├─ .env                 # local key (ignored)
├─ .gitignore
│
├─ notebooks/
│   ├─ golf-capstone.ipynb     # governed analysis notebook
│   └─ private/                # exploratory work (ignored)
│
├─ deliverables/               # governed exports
│
├─ data/
│   ├─ raw/                    # GolfShot exports (ignored)
│   └─ private/                # interim artifacts (ignored)
│   └─ processed/              # final artifacts (ignored)
│
└─ src/
    └─ golfcourseapi_openapi.yml   # API reference schema
```

---

## 🧱 Governance & Data Integrity

This repository treats data governance as a **first-class deliverable**.

| Governance Tool | Purpose |
|-----------------|----------|
| `validate_columns()` | Enforces schema consistency at every step |
| `log_step()` | Records process metadata and outputs |
| `track_transform()` | Captures before/after deltas in rows and columns |
| `record_assumption()` | Documents all business rules and logic choices |
| `generate_data_dictionary()` | Registers every derived feature |
| `export_artifacts()` | Packages data + governance logs for deployment |

Every major phase produces auditable logs — **STEP_LOG**, **VALIDATION_LOG**, **ASSUMPTIONS_LOG**, **TRANSFORM_LOG**, and a **Data Dictionary** — consolidated into a governed Excel close-out file.

---

## 🧠 Methodology Mapping — CRISP-DM × Six Sigma DMAIC

| Phase | CRISP-DM Equivalent | Key Deliverables |
|:--|:--|:--|
| **1️⃣ Define** | Business Understanding | Problem statement · Success metrics · Data inventory |
| **2️⃣ Acquire** | Data Understanding | Raw GolfShot data · Initial profiling · Completeness checks |
| **3️⃣ Prepare** | Data Preparation | Validated round, hole, shot, club, and facility tables |
| **4️⃣ Analyze** | Modeling / Evaluation | Tableau dashboards · performance trends |
| **5️⃣ Improve** | Deployment | Scenario analysis · Practice recommendations · On-course strategy recommendations |
| **6️⃣ Control** | Maintenance | Governance package · Versioned exports · Documentation |

Each notebook cell begins with a standardized metadata header:

```
#### ACTION
- Summarizes the intent of the step

#### INPUTS
- Lists dataframes or parameters used

#### WHAT THIS STEP DOES
- Plain-language description of transformations

#### WHY IT MATTERS
- Links technical work to the analytical goal

#### OUTPUTS
- Defines the exported dataset or logged artifact
```

---

## 📊 Current Phase 3 Deliverables

| Artifact | Description |
|:--|:--|
| **`rounds.csv`**, **`holes.csv`**, **`shots.csv`** | Fact tables with validated data |
| **`clubs.csv`** | Player × club statistics (distance & dispersion) |
| **`facilities.csv`** | Geocoded facility dimension |
| **`phase3_delverables`** | Governance close-out folder: all logs + data dictionary |

---

## 🧭 Notebook Workflow

1. **Setup & Configuration** – Environment initialization and governance setup  
2. **Data Import & Cleaning** – Raw GolfShot ingestion, schema validation, completeness profiling  
3. **Feature Engineering & Enrichment** – Time features; GPS validation; club & facility metrics; and round-, hole-, and shot-level data analysis

---

## ✅ Reproducibility Checklist

- [x] All secrets managed via `.env`  
- [x] All raw and processed governed outputs stored in `data/` (ignored)  
- [x] Governance logs and data dictionary export automatically to `deliverables/` 
- [x] Tableau and Project WBS located in `deliverables/`  
- [x] Conda environment pinned via `environment.yml`  

---

## 🪶 Future Enhancements

- Integrate **weather and wind** context for environmental correlation  
- Cross-verify course data with **USGA Slope & Rating** datasets  
- Implement **predictive shot-outcome modeling**    

---

## 📚 Data Sources

- [**GolfShot (golfshot.com)**](https://golfshot.com) — personal historical performance data  
- [**Golf Course API (golfcourseapi.com)**](https://golfcourseapi.com) — facility metadata and geocodes  
- OpenStreetMap / ArcGIS — fallback geocoding for facility validation  

All third-party data are used solely for educational, non-commercial analysis.

---

## 🏁 Credits

Developed by **Mike Phillips** as part of the **NewForce WV Data Analytics Bootcamp (2025)**.  
Special thanks to mentors for reinforcing *reproducibility, governance, and storytelling in analytics.*

> *“Most of the professional projects I’ve worked on in the past are at the intersection of data, people, and improving business processes. I believe that in both my professional and personal life, “what gets measured gets managed.” — Mike Phillips*
