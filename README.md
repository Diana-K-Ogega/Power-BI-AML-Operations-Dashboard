### AML Operations Dashboard


## Introduction

This project delivers an enterprise-ready, end-to-end Power BI data analytics solution that simulates a live Anti-Money Laundering (AML) Operations Center. 

The dashboard models, and visualizes financial intelligence data across 249 global alerts. It provides compliance management with immediate visibility into pipeline backlogs, investigator capacity, crime typologies, and global jurisdiction risks.

---

## Technologies List

* **Data Visualization & Business Intelligence:** Microsoft Power BI Desktop
* **Data Storage & Engineering Source:** Microsoft Excel (aml_alerts_data.xlsx)
* **Analytical Calculation Engine:** Data Analysis Expressions (DAX)
* **Version Control:** Git & GitHub

---

## Features

* **Executive Performance Tracking:** Interactive Key Performance Indicators (KPIs) mapping case resolution rates and investigative conversions.
* **Dynamic Investigator Metrics:** High-fidelity matrix tracking individual investigator volume, average processing speed, and file quality scores.
* **Geospatial Risk Mapping:** Dynamic map visualization plotting alert volume exposure by international country codes, instantly exposing high-volume geographic hubs.
* **Typology Risk Matrices:** Granular operational profiles cross-referencing specific financial crime methods (Structuring, Layering, and Politically Exposed Persons) with alert severity volumes.

---

## Keyboard Shortcuts

To maximize accessibility and ensure seamless executive navigation through this multi-page intelligence asset, the dashboard supports the following native Power BI navigation controls:
* **Ctrl + Click**: Used to interact with cross-filtering components, select multiple countries on the geographic map, or toggle slicers without resetting prior criteria.
* **Ctrl + Alt + Enter**: Accesses the underlying data matrix view for any focused chart component to review the raw transaction records.
* **Alt + Shift + F10**: Activates the filter focus mode on specific visualization containers to isolate specific risk parameters.

---

## Repository Dashboard Visuals

### Page 1 — Executive Summary
*Provides a high-level operational overview of total cases, open vs. closed resolution rates, critical SLA breaches, and overall SAR filing conversion performance.*
<br>
![Executive Summary](executive_summary.png)

### Page 2 — Alert Volume Trends
*Displays case distribution over time and highlights high-risk financial crime categories to assist compliance managers with resource allocation.*
<br>
![Alert Volume Trends](alert-volume-trends.png)

### Page 3 — Analyst Performance
*Monitors operational throughput, investigative capacity, and file quality scores across the enforcement team.*
<br>
![Analyst Performance](analyst_perfomance.png)

### Page 4 — Geographic Risk Assessment
*Maps operational alert density across international jurisdictions to isolate cross-border exposure risks.*
<br>
![Geographic Risk](geographic_risk.png)

### Page 5 — Case Typology Analysis
*Breaks down the operational data cube by specific crime methods and risk categories, ensuring exact legal alignment.*
<br>
![Case Typology Analysis](case_agency.png)

---

## The Process
1. **Data Sheet Ingestion:** Generated a multi-sheet operational workbook (aml_alerts_data.xlsx) simulating real-world transaction monitoring variables, including timestamps, analyst names, and risk codes.
2. **Schema Calibration:** Configured data connections within Power BI, resolving column types, identifying unique row keys, and verifying proper data alignment.
3. **DAX Architecture:** Formulated performance measures to isolate underlying data signals without introducing row-context processing drag:

    -- Suspicious Activity Report (SAR) Conversion Efficiency Rate
    SAR Rate = 
    DIVIDE(
        COUNTROWS(FILTER(Alerts, Alerts[Status] = "SAR")),
        COUNTROWS(Alerts)
    ) * 100

    -- Operational Productivity Formula (Throughput per Investigator Day)
    Productivity = 
    DIVIDE(
        COUNTROWS(Alerts), 
        DISTINCTCOUNT(Alerts[Analyst_Name]) * DISTINCTCOUNT(Alerts[Date_Created])
    )

4. **Visual Interface Optimization:** Designed a unified layout featuring an executive blue palette, tailored visual boundaries, and explicit data labels to deliver a professional client presentation.

---

## What I Learned
* **Context Overrides:** Discovered how column groupings affect chart generation, resolving rendering discrepancies where implicit data relationships obscured raw totals.
* **UI Symmetrical Balancing:** Mastered the use of space allocation and side-by-side component pairs (such as pairing maps and charts with detailed data grids) to make complex information easily scannable.
* **Deflecting Clutter:** Learned to replace default machine headers with explicit, business-ready terminology to match industry compliance standards.

---

## How It Can Be Improved
* **Direct Database Connectivity:** Migrate the underlying database architecture from static files to a live SQL Server or cloud environment to support automated, near real-time data refreshes.
* **Incremental SLA Aging Tracks:** Expand case aging views by introducing incremental alert aging ranges (e.g., 0–2 days, 3–5 days, 5+ days) to catch operational backlog build-ups earlier.
* **Predictive Risk Modeling:** Integrate Python scripts into the Power BI pipeline to execute proactive machine learning models that flag potential high-risk cases before manual reviews occur.

---

## Running the Project & Local Access

### Project Architecture & Licensing Note
Due to Microsoft Power BI licensing restrictions on standard personal accounts, hosting an active, interactive public cloud link via the Power BI Service is restricted. To ensure complete transparency and allow technical reviewers to interact with the model live, the fully configured database file (AML_Transaction_Monitoring_Dashboard..pbix) has been uploaded directly to this repository.

### Step-by-Step Local Deployment
1. Download and install Microsoft Power BI Desktop (available for free via the Microsoft Store or official site).
2. Clone this repository or download the AML_Transaction_Monitoring_Dashboard..pbix file locally.
3. Launch Power BI Desktop and open the .pbix file.
4. Expand the right-side panes to review the data structures, underlying table joins, and custom DAX measures.
