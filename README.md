# 🚌 Transit Ridership Analysis — Summer 2025 Bus Network

![Data](https://img.shields.io/badge/Records-18%2C088-blue)
![Routes](https://img.shields.io/badge/Routes-127-green)
![Weekly Riders](https://img.shields.io/badge/Weekly%20Riders-4.29M-orange)
![Tool](https://img.shields.io/badge/Built%20With-Excel%20%2B%20APC%20Data-purple)

&gt; A strategic, C-level analysis of **Summer 2025 APC stop-summary data** covering **127 bus and trackless trolley routes**, **18,088 stop-direction records**, and **4,293,991 weekly riders** — answering four executive questions on revenue, efficiency, growth, and resource allocation.

---

## 📋 Table of Contents

- [Project Goal](#-project-goal)
- [Key Findings at a Glance](#-key-findings-at-a-glance)
- [Key Metrics](#-key-metrics)
- [Dataset Overview](#-dataset-overview)
- [Workbook Guide](#-workbook-guide)
- [Methodology](#-methodology)
- [Validation Numbers](#-validation-numbers)
- [Assumptions & Notes](#-assumptions--notes)
- [Suggested Screenshots](#-suggested-screenshots)
- [How to Use This Workbook](#-how-to-use-this-workbook)

---

## 🎯 Project Goal

Analyze APC stop-level bus activity to identify high-volume routes and stops, service-day patterns, directional imbalances, revenue/cost performance, and network-design opportunities — translating raw stop-summary data into executive-ready answers to four strategic questions:

1. **Revenue & Profitability** — Which routes are our 'Stars,' and which lose money?
2. **Operational Efficiency** — Optimal stop spacing? How concentrated is demand?
3. **Strategic Growth** — Where are transfer hubs? What do commute patterns tell us?
4. **Resource Allocation** — Where should we reallocate buses from low to high demand?

---

## 🔍 Key Findings at a Glance

### 1️⃣ Revenue & Profitability
- 💰 **64 routes (50%) operate below break-even** on the cost proxy ($2.25 fare per boarding; cost = $50/stop + $0.10 per weekly rider)
- ⭐ **Route 47 is the star performer** with **167,195 weekly riders** — the clear #1 route in the network
- 📉 Only 20 of 127 routes (Premier + High tiers) average above ~80K weekly riders; the bottom 26 routes form the underperforming tail

### 2️⃣ Operational Efficiency
- 📏 **Routes with &lt;200m stop spacing perform best** (~37K average weekly ridership) — tighter spacing correlates with higher demand capture
- 📊 **Pareto concentration: the top 10% of stops carry 55.4% of all ridership**
- 🛑 Network averages: 199m stop spacing, 43 boardings per stop

### 3️⃣ Strategic Growth & Network Design
- 🔄 **Frankford Transit Center is the #1 hub** — 12 routes, 36,797 combined weekly riders — followed by the 69th St Transit Center complex (~95K combined weekly riders)
- 🚇 **39 routes are commuter-heavy** (&lt;15% weekend usage); only 1 route is weekend-heavy (&gt;30%), confirming a weekday-commuter-dominated network

### 4️⃣ Resource Allocation
- 🏙️ **34.5% of ridership occurs within 5km of the city center**, decaying sharply with distance (543 avg riders/stop at 0–2km vs. 38 beyond 30km)
- ↔️ **Routes 47 and 23 show massive directional imbalances**, suggesting schedule-optimization opportunities by direction and day type

---

## 📈 Key Metrics

| Metric | Value |
|---|---|
| Total weekly ridership (all routes) | **4,293,991** |
| Routes analyzed | 127 |
| Stops analyzed | 18,088 |
| Avg weekly ridership per route | 33,811 |
| 🥇 Top performing route | Route 47 (167,195 weekly) |
| ⚠️ Routes below break-even (proxy) | 64 |
| Weekend revenue as % of total | 18.6% |
| Avg boardings per stop | 43 |
| Top 10% stops carry % of ridership | 55.4% |
| Major transfer hubs (2+ routes) | 20 |
| Commuter-heavy routes (&lt;15% weekend) | 39 |
| Weekend-heavy routes (&gt;30%) | 1 |
| Avg stop spacing | 199m |
| Ridership within 5km of center | 34.5% |

### Route Tier Distribution

| Tier | Routes | % of Network | Avg Weekly Ridership |
|---|---|---|---|
| 🟣 Premier | 9 | 7.1% | 122,637 |
| 🔵 High | 11 | 8.7% | 79,758 |
| 🟢 Medium | 33 | 26.0% | 45,947 |
| 🔴 Low | 74 | 58.3% | 10,766 |

---

## 🗄️ Dataset Overview

| Attribute | Detail |
|---|---|
| **Source sheet** | `Summer_2025_StopSummary_(Bus)` |
| **Grain** | One row per route × direction × stop × stop code |
| **Records** | 18,088 data rows (+1 header), columns A:Q |
| **Routes** | 127 |
| **Directions** | Eastbound, Westbound, Northbound, Southbound, Loop |
| **Source system** | APC (Automated Passenger Counter) |
| **Core ridership fields** | `Weekdays_O`, `Weekdays_1`, `Saturdays_`, `Saturdays1`, `Sundays_On`, `Sundays_Of` |
| **Geography** | Latitude/longitude retained as numeric fields for map-ready analysis |

---

## 📑 Workbook Guide

| Sheet | Contents |
|---|---|
| `4_Strategic_Exec_Questions` | The four strategic question categories with key findings |
| `Executive Summary` | C-level overview: key questions, metrics, and workbook contents |
| `Route Rankings` | Top 15 routes by weekly ridership, with tier classification |
| `Day Type Breakdown` | Weekday vs. Saturday vs. Sunday ridership by route |
| `Performance Matrix` | Scatter chart: Stars vs. Workhorses vs. Question Marks vs. Dogs |
| `Tier Distribution` | Pie chart: Premier / High / Medium / Low route tiers |
| `Top Busiest Stops` | Top 20 individual stops by total weekly activity |
| `Directional Imbalance` | Net flow (boardings − alightings) analysis + bar chart |
| `Revenue vs Cost` | Scatter chart with break-even line; ROI by route |
| `Distance Analysis` | Ridership density decay by distance band from city center |
| `Transfer Hubs` | Multi-route stops ranked by combined weekly ridership |
| `Route Direction Performance` | Top/bottom route-direction combinations by day type |
| `Summer_2025_StopSummary_(Bus)` | Raw APC source data (preserved as source of truth) |
| `Pivot_Table_1` | Supporting pivot aggregation |
| `Readme Documentation` | In-workbook documentation of cleaning and build steps |

---

## ⚙️ Methodology

### 1. Data Cleaning
1. Preserved the raw worksheet as the source of truth for audit and rework
2. Verified dataset boundaries: columns A:Q, rows 1:18,089
3. Validated headers and identified key fields: route, direction, stop code, stop name, latitude, longitude, and day-type ons/offs
4. Standardized field interpretation: `_O`/`On`-style columns = **boardings**; `_1`/`Off`-style columns = **alightings**
5. Treated route values as labels (not pure numbers) so mixed identifiers (e.g., `B1 OWL`, `BLVDDIR`) stay stable in summaries and charts
6. Confirmed ridership columns are numeric and aggregation-ready
7. Retained zero-ridership rows — they can represent valid directional stops, terminals, or stops with no observed activity on a given service day
8. Left stop names unaltered so every summary traces back to the original stop label

### 2. Feature Engineering
1. Service-day totals combining ons and offs per day type
2. Total boardings (weekday + Saturday + Sunday ons) and total alightings (offs)
3. Total activity = all ons + offs across all day types
4. Day-of-week activity shares for weekday/weekend comparison
5. Route-level, direction-level, and stop-level aggregations for rankings and imbalance detection
6. **Cost proxy:** $2.25 fare per boarding; cost = $50/stop + $0.10 per weekly rider — used for break-even and ROI analysis

### 3. Dashboard Build Process
1. Built summary KPIs first so dashboards answer key questions before showing detail
2. Route-ranking and stop-ranking views to surface top performers
3. Day-type and direction comparisons for demand-pattern evaluation
4. Charts for high-level comparison (11 embedded charts); tables for drill-down
5. Consistent number formatting (thousands separators) and standalone titles/labels so screenshots work directly in this README
6. Verified all summaries use the full 18,088 records — no sampling

---

## ✅ Validation Numbers

| Measure | Value |
|---|---|
| Weekday boardings | 350,708 |
| Weekday alightings | 348,452 |
| Saturday boardings | 229,764 |
| Saturday alightings | 228,381 |
| Sunday boardings | 170,482 |
| Sunday alightings | 169,564 |
| Top route by total activity | Route 47 (59,183 combined daily ons/offs) |

---

## 📝 Assumptions & Notes

- `Weekdays_1`, `Saturdays1`, and `Sundays_Of` are treated as alighting fields based on their pairing with boarding fields
- Revenue/cost figures use the proxy assumptions above and are **directional, not accounting-grade**
- Break-even classification depends on the cost proxy; sensitivity to fare and per-stop cost assumptions should be considered before operational decisions
- Weekday figures in the source are per-day averages; weekly totals use weekday × 5

---

## 📸 Suggested Screenshots

&gt; Drop these images into a `/screenshots` folder and embed them above each section for maximum impact.

1. **Executive Summary** — KPI cards and key metrics overview
2. **Performance Matrix** — Stars vs. Dogs quadrant scatter chart
3. **Revenue vs Cost** — scatter with break-even line (64 routes below)
4. **Tier Distribution** — Premier/High/Medium/Low pie chart
5. **Day Type Breakdown** — weekday vs. weekend ridership comparison
6. **Transfer Hubs** — top multi-route stops table/map
7. **Distance Analysis** — ridership decay from city center
8. **Directional Imbalance** — net flow bar chart

**Example embed:**
```markdown
![Executive Summary Dashboard](screenshots/executive_summary.png)
