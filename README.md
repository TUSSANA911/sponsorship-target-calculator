# Sponsorship Target Calculator

**A data-driven sponsorship planning and ROI tool for Exness Partner Relationship Managers (PRMs).**

The Sponsorship Target Calculator standardises how PRMs set targets, define payout mechanics, and justify partner sponsorships. Every proposal follows the same structure, so BD Operations can review and validate tasks faster and more consistently.

It combines historical partner performance, statistical analysis, KPI target setting, scenario forecasting, payout calculation, and ROI justification in a single browser-based interface.

### Live Application

- **GitHub Pages:** [tussana911.github.io/sponsorship-target-calculator](https://tussana911.github.io/sponsorship-target-calculator/)

---

## What's New in This Version

- **Duration first.** Sponsorship Duration and Rounding now sit inside Section 1, before metric selection, so the time frame is set before any target is calculated.
- **Simplified layout.** The tool now has 6 sections instead of 7.
- **Focused metric list.** The metric selector is limited to the 9 KPIs used in sponsorship tasks.
- **Month label auto-fill.** Set the data year and month range, and the data table labels itself (for example `Jun/2025` to `May/2026`), including ranges that cross year-end.
- **BD Ops validation flow.** PRMs export a timestamped JSON file, and BD Ops imports it in Section 6 to see exactly what was submitted.

---

## Application Structure

| Section | Name | Purpose |
| ------- | ---- | ------- |
| 1 | Metric Target Setup | Partner details, sponsorship duration, rounding, and up to 3 metric cards |
| 2 | Payout Structure | Upfront payment, payout logic, and combined payout projection |
| 3 | ROI and Business Justification | Estimated incremental revenue, sponsorship cost, and ROI |
| 4 | Live Summary | Real-time overview of all metrics, targets, scenarios, and payouts |
| 5 | Export Summary | Proposal summary generator, JSON export, and JIRA request link |
| 6 | BD Ops Validation | JSON import for independent review of submitted proposals |

---

## Key Features

### 1. Sponsorship Duration and Rounding

Set once in Section 1 and shared across all metrics.

- Duration: 1, 3, 6, 12 months, or custom
- Rounding: none, round up, round down, nearest integer, nearest 5, nearest 10

When rounding is active, targets and scenario figures display as whole numbers.

### 2. Multi-Metric KPI Target Setting

Configure up to **3 independent metrics** per sponsorship proposal. Supported metrics:

| Metric | Description |
| ------ | ----------- |
| FTD | First Time Deposits within the month |
| Active Traders | Clients who opened and closed at least 1 trade in the month |
| FTT | Clients placing their first trade within the month |
| UFTT | Unique First Time Trade |
| LMAU | Loyal Monthly Active Users |
| LMAU High Value | Loyal Monthly Active Users, high value segment |
| Trading Volume - Lots | Closed traded lots |
| Trading Volume - USD | Trading volume in USD |
| Sub-partners | New sub-partners registered under the partner |

**Metric guidance:** use Active Traders for retention objectives, and FTD or FTT for new client acquisition.

Each metric card has its own historical data, statistics, baseline, uplift, scenarios, payout configuration, and validation report link.

### 3. Historical Performance Input

- Manual data table (12 rows by default, editable)
- Paste parser for comma, tab, or line-separated values copied from MetaBase
- Screenshot upload for visual reference
- Data year and month range selector that auto-fills month labels in `MMM/YYYY` format

### 4. Statistical Analysis and Baseline Guidance

Each metric calculates mean, median, standard deviation, coefficient of variation (CV), minimum, maximum, latest value, and data count.

A distribution chart (histogram with a smoothed curve) shows the shape of the data and highlights the suggested baseline:

- **Yellow:** suggested baseline
- **Grey:** not suggested

Median is recommended when CV is above 25% or the mean and median differ significantly. Otherwise, mean is recommended.

### 5. Target Calculation

Baseline options: Mean, Median, Latest Month, Best Month, Worst Month, or Custom.

```
Total Target   = Monthly Baseline x Sponsorship Duration x (1 + Growth Uplift %)
Monthly Target = Total Target / Sponsorship Duration
```

Growth uplift options: 0%, 10%, 20%, 30%, 50%, or custom.

### 6. Scenario Planning

Each metric has its own scenario percentages:

| Scenario | Default Achievement |
| -------- | ------------------- |
| Worst Case | 50% |
| Base Case | 100% |
| Best Case | 200% |

Each scenario shows the projected total and monthly achievement.

### 7. Payout Structures

Each metric can use one of four payout models:

| Model | How It Works |
| ----- | ------------ |
| Per Unit | Fixed reward for each achieved unit |
| Fixed Budget | Lump sum when the target is met, optionally prorated |
| Tiered | Cumulative reward rate across performance tiers |
| Milestone | Flat reward for the highest threshold reached in the month |

Rewards are evaluated monthly and multiplied by the sponsorship duration.

### 8. Payout Logic and Upfront Payment

How multiple metric payouts combine:

| Logic | Behaviour |
| ----- | --------- |
| Independent | Each metric pays separately. Total equals the sum of all metric payouts. |
| All-or-Nothing | All metrics must reach 100% of target. If any metric misses, performance payout is $0. A warning is shown. |
| Manager Discretion | Payout is calculated from achievement % and marked as pending CD/RD approval. |

An optional monthly **upfront payment** is paid regardless of performance. It is added only to the Combined Payout Projection, not to individual metric payouts.

### 9. ROI and Business Justification

```
ROI (%) = (Estimated Incremental Revenue - Sponsorship Cost) / Sponsorship Cost x 100
```

- Total Sponsorship Cost auto-fills from the Best Case combined payout, including upfront
- PRMs enter estimated revenue and explain the calculation logic
- Revenue should be based on **incremental SR only**, excluding baseline SR from the partner's existing business

### 10. Proposal Summary Generator

Generates a structured summary in the Exness Partner Sponsorship Request format:

- WHAT, WHY, and HOW
- Targets, baselines, and uplift per metric
- Payout logic
- Expected results and payouts per scenario
- ROI calculation logic
- Supporting files, including MetaBase or Tableau validation links

The **Partner Sponsorship Request** button opens the JIRA service desk form directly.

### 11. JSON Export and BD Ops Validation

**PRM workflow**

1. Complete the calculator
2. Generate and copy the summary into JIRA
3. Click **Export JSON** in Section 5
4. Attach the JSON file to the Partner Sponsorship Request

The file name includes the partner UID, sponsorship name, and export time, for example:

```
sponsorship_123456789_TH_FTD_Booster_2026-06-11_14-35-22.json
```

**BD Ops workflow**

1. Download the JSON file from the JIRA task
2. Open the calculator and go to Section 6
3. Click **Import JSON (BD Ops validation)**
4. Review the PRM's exact inputs, targets, scenarios, and payouts

---

## How to Use

1. Enter partner name, UID, PRM name, sponsorship name, and notes.
2. Set the sponsorship duration and rounding.
3. Add up to 3 metrics and select each KPI.
4. Add the validation report link and the data year and month range.
5. Enter or paste historical monthly data.
6. Review statistics and the distribution chart, then select a baseline.
7. Set growth uplift and scenario percentages.
8. Configure the payout type for each metric.
9. Set upfront payment and payout logic in Section 2.
10. Enter estimated revenue and revenue logic in Section 3.
11. Review the Live Summary in Section 4.
12. Generate the summary, export the JSON file, and submit the JIRA request.

---

## Technology Stack

| Technology | Purpose |
| ---------- | ------- |
| HTML5 | Application structure |
| CSS3 | Responsive layout and Exness brand styling |
| Vanilla JavaScript | Calculation engine and interactivity |
| Canvas API | Distribution chart |
| JSON | Export and import of saved state |
| GitHub Pages / Netlify | Static hosting |

The application is a single `index.html` file and runs entirely in the browser. No backend or build step is required.

---

## Deployment

**GitHub Pages**

1. Make sure the application file is named `index.html`.
2. Open **Settings**, then **Pages**.
3. Choose **Deploy from a branch**, select `main` and `/ (root)`, and save.

GitHub Pages redeploys automatically after each commit to `main`.

**Netlify**

If the Netlify site is linked to this repository, it redeploys automatically after each commit. If it was created by drag and drop, upload the new `index.html` in the site's **Deploys** tab.

---

## Data Handling and Security

- All calculations run locally in the browser.
- No database, server, or user accounts.
- JSON export creates a local file. JSON import reads only the file the user selects.

**Important:** This tool supports internal sponsorship analysis. Public GitHub repositories and public websites are not private environments. Do not commit partner data or confidential company information to this repository.

---

## Disclaimer

This is a decision-support tool. Targets, payouts, and ROI figures are estimates based on user inputs and assumptions. Results do not constitute sponsorship approval and must be reviewed against applicable company policies and approval procedures.

---

## Version

| Field | Value |
| ----- | ----- |
| Version | 2.1 |
| Application | Sponsorship Target Calculator |
| Owner | ARM Tussananakajit, Partner Relationship Manager, Exness |
| Category | Partnership Management / Business Development |

### Changelog

**2.1**
- Moved Sponsorship Duration and Rounding into Section 1, before metric selection
- Reduced the application from 7 sections to 6
- Limited the metric list to 9 sponsorship KPIs
- Added month label auto-fill with cross-year support
- Added Section 6 BD Ops Validation with JSON import
- Added timestamp to JSON export file names

**2.0**
- Multi-metric support (up to 3 metrics)
- Payout logic: Independent, All-or-Nothing, Manager Discretion
- Per-metric scenario planning
- Combined payout projection with shared upfront payment
- Milestone payout model

---

*Built to make sponsorship decisions structured, transparent, and data-driven.*
