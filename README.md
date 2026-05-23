# 🏆 Vendor Performance Scorecard Dashboard

> A fully interactive, multi-page **Google Apps Script + HTML/CSS/JS** web application that delivers end-to-end visibility into logistics vendor performance, lane-level operations, commercial benchmarking, and data-driven cost optimisation.

---

## 📌 Project Overview

Managing a large logistics network means tracking dozens — sometimes hundreds — of vendors across multiple routes, months, and performance dimensions simultaneously. Manual spreadsheets fall short.

This dashboard was built to solve that problem: it pulls live data from Google Sheets, processes it entirely in the browser, and presents a comprehensive **5-page analytical cockpit** that enables procurement, operations, and vendor management teams to make faster, evidence-backed decisions.

---

## 🖥️ Dashboard Pages

### Page 1 — Category View
Classifies vendors into performance tiers (A / B / C / D) based on monthly trip volume. Provides a cross-month count and trip-volume matrix, along with auto-generated **Category Insights** highlighting concentration risk, fragmentation, and top contributors.

![Category View](screenshots/page1_category_view.png)

---

### Page 2 — Detailed Scorecard Matrix
Renders a vendor-by-vendor breakdown across **10 weighted KPIs**:

| KPI | What it measures |
|---|---|
| On-Time Placement % | Truck availability against committed schedule |
| On-Time Trips % | Delivery compliance at destination |
| Accidents + Breakdown Rate | Safety and fleet reliability index |
| GPS Adherence % | Route discipline and tracking compliance |
| Digital Lock Adherence % | Security protocol adherence |
| Cargo Net Availability % | Load safety compliance |
| Age of Fleet | Fleet freshness proxy |
| Avg. Recovery Time (mins) | Incident response speed |
| Spec Adherence | Vehicle specification compliance |
| Billing Accuracy | Invoice and documentation accuracy |

Auto-generated **Matrix Insights** surface the top-performing metric, the network's weakest KPI (blindspot), and vendor segments that need intervention.

![Detailed Matrix](screenshots/page2_detailed_matrix.png)

---

### Page 3 — Trends
Tracks performance over time with:
- **Total vs On-Time Trips** line chart (chronological trend)
- **Score & Rank Trend Table** — every vendor's score and rank across all months side-by-side
- **Vendor Rank Distribution** bar chart (Top 3 / Rank 4-10 / Rank 11-20 / Rank >20)
- **Vendor Category Status** chart showing monthly category mix shifts
- Auto-generated insights: network efficiency %, volume growth/decline, most-improved vendor

![Trends](screenshots/page3_trends.png)

---

### Page 4 — Lane Insights
The operations intelligence layer. Contains:

- **SOB (Share of Business) Allocation Proposals** — identifies prime SOB targets, at-risk vendors, and under-utilised top-tier operators
- **Lane Performance Shifts (MoM)** — flags improving, degrading, chronically underperforming, and high-volatility lanes
- **Pareto Chart** — top lanes by delayed trips with cumulative %
- **Top Lanes by Volume & OT%** — horizontal combo chart
- **Vendor Risk vs. Reward Bubble Chart** — volume × OT% scatter with colour-coded risk zones
- **Lane-Level Vendor Scorecard** — month-wise OT%, cost per trip, total cost, MoM delta
- **Vendor Consistency & Recommendations** — MoM trend sparkline + actionable recommendation (Maintain / Propose SOB Increase / Review & Decrease)
- **Cost Savings & Re-allocation Engine** — identifies shiftable trips, proposes lower-cost alternatives, and quantifies projected monthly savings

![Lane Insights](screenshots/page4_lane_insights.png)

---

### Page 5 — Commercials
The procurement and rate intelligence layer. Contains:

- **Rate vs. Rank Competitiveness** scatter plot
- **Cost vs. Performance Value Matrix** bubble chart (OT% × Premium over L1 Rate)
- **Vendors Participating per Lane** bar chart
- **Avg Rate by Vehicle Type** bar chart
- **Commercial Vendor Master Table** — lane-wise rate card with variance to L1 benchmark, ranked

![Commercials](screenshots/page5_commercials.png)

---

## ⚙️ Technical Stack

| Layer | Technology |
|---|---|
| **Backend / Data** | Google Apps Script (server-side `getScorecardData()`) |
| **Data Source** | Google Sheets (Scorecard, Lane Performance, Commercial Master tabs) |
| **Frontend** | Vanilla HTML5 + JavaScript (ES6+) |
| **Styling** | Tailwind CSS (CDN) |
| **Charts** | Chart.js + chartjs-plugin-datalabels |
| **Icons** | FontAwesome 6 |
| **Hosting** | Google Apps Script Web App |

---

## 🔑 Key Features

- **Live Data Refresh** — single-click refresh pulls the latest data from Google Sheets without page reload
- **Multi-Dimensional Filters** — 6–8 cascaded filters (Vendor, Year, Asset Type, Vendor Category, Month, Lane, Trip Type, Rank) with multi-select dropdowns that persist state across tab switches
- **Cross-Chart Filtering** — clicking a bar, bubble, or data point on any chart instantly filters the entire dashboard
- **Vendor Name Standardisation Engine** — normalises inconsistent vendor name spellings and abbreviations across all three data sources before rendering
- **Dynamic Category Assignment** — vendor categories are computed from trip volume thresholds; then locked to the most recent month's category for historical consistency
- **Commercial Rank Re-computation** — true dense-ranking is computed in-browser from rate data, overriding any stale sheet-level ranks
- **Cost Savings Engine** — automatically identifies lanes where volume can be shifted to a higher-OT, lower-rate vendor, and quantifies the projected monthly saving
- **MoM Trend Sparklines** — per-vendor, per-lane month-over-month OT% trend rendered inline in the consistency table
- **Export Everything** — every table exports to Excel (.xls with preserved formatting and colours); every chart exports to CSV
- **Sortable Tables** — every column in every table is click-sortable (asc/desc) with visual sort indicators
- **Graceful Fallback** — if the Apps Script connection times out, the dashboard auto-loads a structured mock dataset so the UI is never blank

---

## 📂 Repository Structure

```
vendor-scorecard/
│
├── Code.gs                  # Google Apps Script backend
│   └── getScorecardData()   # Fetches scorecard, lane & commercial data from Sheets
│
├── index.html               # Complete frontend (single-file HTML/JS/CSS)
│
├── screenshots/
│   ├── page1_category_view.png
│   ├── page2_detailed_matrix.png
│   ├── page3_trends.png
│   ├── page4_lane_insights.png
│   └── page5_commercials.png
│
└── README.md
```

---

## 🚀 Setup & Deployment

### Prerequisites
- A Google account with access to Google Sheets and Google Apps Script

### Steps

1. **Create a Google Sheets workbook** with the following sheets:
   - `Scorecard` — monthly vendor KPI data (one row per vendor per month)
   - `Lane Data` — lane-level trip and OT% data
   - `Commercial Master` — vendor rate cards per lane and vehicle type

2. **Open Apps Script** from the Sheet (`Extensions → Apps Script`) and paste the contents of `Code.gs`

3. **Create a new HTML file** in Apps Script named `index` and paste the contents of `index.html`

4. **Deploy as Web App**:
   - Click `Deploy → New Deployment`
   - Type: `Web App`
   - Execute as: `Me`
   - Who has access: `Anyone in your organisation` (or as appropriate)
   - Click `Deploy`

5. Open the generated Web App URL. The dashboard will load and fetch data automatically.

### Column Mapping
The script uses a flexible key-matching system that recognises common column name variants (e.g. `On Time Trips` / `Ontime Trips` / `On-time`). Refer to `colMap` in `index.html` for the full list of recognised aliases.

---

## 📊 Sample Insights Generated

> *All values below are illustrative and do not represent any real organisation's data.*

- **Category Concentration**: Top-tier vendors (≥500 trips/month) drive ~36% of total network volume despite being only 3 vendors
- **Network Blindspot**: Billing Accuracy averaging 0.0% of potential score — a network-wide process gap
- **Cost Savings Identified**: Shifting ~8% of network volume to better-ranked, lower-rate vendors projects ₹X+ in monthly savings
- **High Volatility Lane**: One lane swung ±100% MoM in OT% — flagged for daily tracking
- **Most Improved Vendor**: One vendor raised its score by +23 points over the 4-month window

---

## 🛠️ Skills Demonstrated

- **Data Engineering**: Multi-source data ingestion, normalisation, deduplication, and join logic entirely in JavaScript
- **Business Intelligence**: KPI design, weighted scoring, vendor tiering, Pareto analysis, MoM trend detection
- **Frontend Development**: Single-page application architecture, dynamic DOM rendering, Chart.js integration, responsive Tailwind layout
- **Google Workspace Automation**: Apps Script backend, Sheets integration, Web App deployment
- **UX Design**: Multi-level filtering, cross-chart interactivity, progressive disclosure, export functionality

---

## 🔒 Data Privacy Note

All vendor names, route names, rates, and trip volumes visible in the screenshots have been anonymised or are illustrative only. No proprietary or confidential commercial data is included in this repository.

---

## 👤 Author

Built and maintained as part of logistics operations analytics work.  
Feel free to connect on [LinkedIn](#) or raise an issue for questions.

---

*Built with Google Apps Script · Chart.js · Tailwind CSS*
