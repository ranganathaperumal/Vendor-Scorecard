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

![Category View](page1_category_view.png)

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

![Detailed Matrix](page2_detailed_matrix.png)

---

### Page 3 — Trends
Tracks performance over time with:
- **Total vs On-Time Trips** line chart (chronological trend)
- **Score & Rank Trend Table** — every vendor's score and rank across all months side-by-side
- **Vendor Rank Distribution** bar chart (Top 3 / Rank 4-10 / Rank 11-20 / Rank >20)
- **Vendor Category Status** chart showing monthly category mix shifts
- Auto-generated insights: network efficiency %, volume growth/decline, most-improved vendor

![Trends](page3_trends.png)

---

### Page 4 — Lane Insights
The operations intelligence layer. Contains:

- **SOB (Share of Business) Allocation Proposals**
- **Lane Performance Shifts (MoM)**
- **Pareto Chart** — top lanes by delayed trips
- **Vendor Risk vs. Reward Bubble Chart**
- **Lane-Level Vendor Scorecard**
- **Vendor Consistency & Recommendations**
- **Cost Savings & Re-allocation Engine**

![Lane Insights](page4_lane_insights.png)

---

### Page 5 — Commercials
The procurement and rate intelligence layer. Contains:

- **Rate vs. Rank Competitiveness** scatter plot
- **Cost vs. Performance Value Matrix** bubble chart
- **Vendors Participating per Lane** bar chart
- **Avg Rate by Vehicle Type** bar chart
- **Commercial Vendor Master Table**

![Commercials](page5_commercials.png)

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

- **Live Data Refresh** — single-click refresh pulls latest data from Google Sheets
- **Multi-Dimensional Filters** — 6–8 cascaded filters with multi-select dropdowns
- **Cross-Chart Filtering** — clicking any chart element filters the entire dashboard
- **Vendor Name Standardisation Engine** — normalises inconsistent vendor name spellings
- **Dynamic Category Assignment** — vendor categories computed from trip volume thresholds
- **Cost Savings Engine** — identifies lanes where volume can be shifted to save costs
- **MoM Trend Sparklines** — per-vendor, per-lane month-over-month OT% trend
- **Export Everything** — every table exports to Excel, every chart exports to CSV
- **Sortable Tables** — every column in every table is click-sortable

---

## 🛠️ Skills Demonstrated

- **Data Engineering** — Multi-source data ingestion, normalisation, and join logic in JavaScript
- **Business Intelligence** — KPI design, weighted scoring, vendor tiering, Pareto analysis
- **Frontend Development** — Single-page application, Chart.js integration, responsive Tailwind layout
- **Google Workspace Automation** — Apps Script backend, Sheets integration, Web App deployment
- **UX Design** — Multi-level filtering, cross-chart interactivity, export functionality

---

## 🔒 Data Privacy Note

All vendor names, route names, rates, and trip volumes are anonymised. No proprietary or confidential commercial data is included in this repository.

---

## 👤 Author

Built and maintained as part of logistics operations analytics work.

---

*Built with Google Apps Script · Chart.js · Tailwind CSS*
