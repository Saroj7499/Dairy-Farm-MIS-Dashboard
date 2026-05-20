# Dairy-Farm-MIS-Dashboard
End-to-end Dairy Farm MIS System — Excel reporting + Power BI dashboard for 100-cow farm operations

# Dairy Farm MIS Dashboard — Modasa Operations

## Project Overview
End-to-end MIS system built for a 100-cow dairy farm covering daily operations across milk production, veterinary health, breeding, and feed cost tracking — directly aligned with real farm management reporting requirements.

**Tools:** Excel (Advanced) · Power BI · Power Query · DAX

---

## What This Project Covers

| Department | Coverage |
|------------|----------|
| Milk Production | Cow-wise daily morning/evening tracking, low yield flags, breed & section analysis |
| Veterinary | Health cases, treatment records, recovery status, follow-up tracking |
| Breeding | AI & natural insemination events, conception rate, next check dates |
| Feed | Daily consumption per item, unit cost, total cost tracking |

---

## Data Scale
- **100 cows** across 4 farm sections (A, B, C, D)
- **5 breeds:** Gir, HF Cross, Jersey Cross, Sahiwal, Kankrej
- **30 days** of operational data — April 2025
- **1,650+ daily milk records** | 60 vet cases | 25 breeding events | 150 feed entries

---

## Excel Workbook Structure

| Sheet | Purpose |
|-------|---------|
| Cow Master | 100-cow register — breed, age, section, status, lactation number |
| Daily Milk Log | Morning/evening production per cow, low yield rows flagged in red |
| Veterinary Log | Health cases, treatment given, recovery status, follow-up required |
| Breeding Log | AI/natural breeding events, results, next check dates |
| Feed Log | Daily feed items, quantity, unit cost, total cost |
| Pivot Analysis | Breed-wise, section-wise, date-wise pivot tables |
| Daily MIS Report | Dynamic single-day report — change date in B2, entire report updates |
| Weekly MIS Report | Week-wise production, vet, breeding, feed summary using SUMPRODUCT |
| Monthly MIS Report | Full April summary across all 5 departments |
| MIS Summary | Single-sheet KPI overview using COUNTA, COUNTIF, SUMIF, AVERAGEIF |

---

## Key Numbers — April 2025

### Milk Production
| Metric | Value |
|--------|-------|
| Total Monthly Production | 23,579.6 L |
| Avg Daily Farm Production | 786 L/day |
| Avg Yield Per Cow Per Day | 14.3 L |
| Low Yield Cows (<8L/day) | 7 cows |
| Lactating Cows | 55 out of 100 |

### Breed-wise Performance
| Breed | Cows | Total (L) | Avg/Cow/Day (L) |
|-------|------|-----------|-----------------|
| HF Cross | 25 | 8,401.1 | 11.2 |
| Gir | 34 | 7,624.7 | 7.5 |
| Jersey Cross | 15 | 3,792.8 | 8.4 |
| Sahiwal | 17 | 2,433.2 | 4.8 |
| Kankrej | 9 | 1,327.8 | 4.9 |

### Veterinary
| Metric | Value |
|--------|-------|
| Total Vet Cases | 60 |
| Cases Recovered | 47 |
| Recovery Rate | 78.3% |
| Follow Ups Pending | 10 |
| Most Common Condition | Routine Checkup |

### Breeding
| Metric | Value |
|--------|-------|
| Total Breeding Events | 25 |
| AI Inseminations | 16 |
| Confirmed Pregnant | 8 |
| Conception Rate | 32% |

### Feed Cost
| Metric | Value |
|--------|-------|
| Total Feed Cost (April) | ₹2,86,154.6 |
| Avg Daily Feed Cost | ₹9,538.5 |
| Cost Per Cow Per Day | ₹95.4 |
| Highest Cost Item | Concentrate Feed |

---

## Power BI Dashboard — Operations Overview

**8 Visuals on one page:**
- KPI Cards — Total Production, Avg Yield/Cow, Low Yield Cows, Lactating Count
- Line Chart — Daily Milk Production Trend (April 2025)
- Bar Chart — Total Production by Breed
- Bar Chart — Total Production by Section
- Donut Chart — Breeding Results (Confirmed / Repeat / Not Confirmed)
- Bar Chart — Vet Cases by Condition
- Alert Table — Bottom 10 Low Yield Cows
- Slicer — Filter entire dashboard by Section (A/B/C/D)

**Data Model:** 3 active relationships — Daily Milk Log, Vet Log, Breeding Log all connected to Cow Master via Cow Tag (Many-to-One)

**DAX Measures:**
```
Total Production (L) = SUM('Daily Milk Log'[Total (L)])
Avg Daily Yield Per Cow = ROUND(DIVIDE([Total Production (L)], DISTINCTCOUNT('Daily Milk Log'[Cow Tag]) * 30), 1)
Low Yield Cows = COUNTROWS(FILTER(VALUES('Daily Milk Log'[Cow Tag]), CALCULATE(DIVIDE([Total Production (L)], 30)) < 8))
```

---

## Key Insights From Data

1. **HF Cross is the highest yielding breed** at 11.2L/cow/day — despite having fewer cows than Gir
2. **Kankrej and Sahiwal are underperformers** at under 5L/cow/day average
3. **Section A leads production** at 6,685.8L for the month
4. **7 cows flagged as chronic low yield** — candidates for veterinary review
5. **78.3% recovery rate** across 60 vet cases — Routine Checkup is most common condition
6. **Concentrate Feed is the biggest cost driver** in the feed budget
7. **32% conception rate** from 25 breeding events — 8 confirmed pregnancies

---

## Files in This Repository
- `Dairy_Farm_MIS_Modasa.xlsx` — Complete Excel MIS workbook
- `Dairy_Farm_MIS_Dashboard.pbix` — Power BI dashboard file

---

## About This Project
Built as a demonstration of end-to-end MIS system design for dairy farm operations — covering data entry structure, dynamic reporting, and management dashboard creation. Designed to align with real operational reporting requirements.
