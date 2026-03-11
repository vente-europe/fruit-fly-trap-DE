# Dashboard Fruit Fly Trap - DE

> **Living document** — Update after every bug fix or new pattern found. No permission needed for additions. Ask before removing.

---

## Project Overview

- **Purpose:** Amazon DE market analysis dashboard — fruit fly trap category
- **Active file:** `index.html` (single-file HTML, lives in project root)
- **Git repo:** root of this folder (branch: `master`)
- **Tech stack:** Chart.js 4.4.0 + chartjs-plugin-datalabels 2.2.0, vanilla JS, no build step

---

## Tab Structure

| ID | Label | Key content |
|----|-------|-------------|
| `ti` | 1 — Main Segments (Total Market) | Total KPI, segment KPI blocks, 2 pie charts (units + revenue share), summary table |
| `tb` | 2 — Market Structure | Lure segment: KPIs (top ASIN concentration, top brand), Pack Size pies (units + revenue), Brand pies (units + revenue) |
| `tl` | 3 — Reviews | Under construction |

---

## Source Data

| Path | Description |
|------|-------------|
| `Data/x-ray/` | Full X-Ray export — not git tracked |
| `Data/sales-units/` | Per-ASIN sales CSVs (3y history) — not git tracked |
| `Data/reviews/` | Amazon review scraper JSONs — not git tracked |

---

## Data Conventions

- **12M sales** = sum of `Sales` column for dates within last 12 months (from export date)
- **12M revenue** = 12M units × listed price from X-Ray
- **Never use** X-Ray ASIN Sales/Revenue columns for 12M — they are 30-day figures
- All chart titles must include **(12M)** where applicable
- **Extrapolation rule:** ASINs with < 6 months of sales data in the 12M window → `12M estimate = avg_monthly × 18` (9 off-peak months ×1 + 3 summer months Jun/Jul/Aug ×3 = multiplier 18). Applied to KPI totals only; monthly breakdown arrays stay as actual observed values. 17 ASINs affected in current build.

---

## Known Bugs & Fixes

*(none yet — add as discovered)*

---

## Editing Conventions

- **Python scripts** for large HTML section replacements
- **Edit tool** for targeted JS changes and small HTML edits
- **Always verify** canvas IDs in HTML match JS after structural changes
- **Never remove** canvas from HTML without null guard in JS or removing JS entirely

---

## Self-Update Rules

**Update this file when:**
- New bug discovered and fixed → add to Known Bugs
- New canvas/chart added → add Canvas IDs table
- Tab structure defined/changed → update Tab Structure table

**Ask first before:**
- Removing existing bug entries
- Changing canvas ID naming conventions
