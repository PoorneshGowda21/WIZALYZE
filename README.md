# 🏆 WIZALYZE — DATAWIZ Data Analytics Competition
**2nd Place — NMIT Bengaluru | 28 February 2026**

---

## 📌 About the Competition

**DATAWIZ** is a data analytics competition organised by the **Wizalyze Club at NMIT Bengaluru**.

- **Format:** Choose 1 of 3 real datasets, clean it, analyse it, build a dashboard, and present findings to judges in 5 minutes
- **Time Limit:** 6 hours
- **Total Marks:** 30 (Dashboard Design /5 · Insights /5 · Analytical Thinking /5 · Presentation /15)
- **Result:** 🥈 2nd Place

**Team Members:**
- Adwin HS
- Darshan AM
- Poornesh ([@PoorneshGowda21](https://github.com/PoorneshGowda21))
- Puneeth MG

---

## 📂 Dataset

**Sample Superstore Sales Dataset**

| Property | Detail |
|---|---|
| Rows | 9,994 |
| Columns | 21 (original) → 28 (after cleaning) |
| Date Range | January 2014 – December 2017 |
| Domain | Retail Sales — USA |

The dataset contains order-level data for a retail store selling Furniture, Office Supplies, and Technology products across the United States.

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **Python (Google Colab)** | Data cleaning, feature engineering, exploratory data analysis |
| **Pandas** | Loading, cleaning, and transforming the dataset |
| **Numpy** | Numerical calculations |
| **Matplotlib & Seaborn** | Generating EDA charts and visualisations |
| **Power BI Desktop** | Building the interactive 5-page dashboard |

---

## 📁 Repository Structure

```
WIZALYZE/
│
├── data/
│   ├── Sample_Superstore.xls          # Original raw dataset
│   └── superstore_final_powerbi.csv   # Cleaned dataset (28 columns)
│
├── notebook/
│   └── Superstore_Phase2_EDA.ipynb    # Complete Google Colab notebook
│
├── dashboard/
│   └── DATAWIZ_Superstore.pbix        # Power BI dashboard file
│
├── presentation/
│   └── Wizalyze_Pitch_Final.pptx      # 5-slide pitch deck
│
├── requirements.txt                   # Python dependencies
└── README.md                          # This file
```

---

## 🔍 Problem Statement

> *Despite strong revenue growth, the organisation is facing declining profit margins and operational inefficiencies.*

**4 Objectives:**
1. Identify loss-making products and sub-categories
2. Detect regional inefficiencies
3. Analyse shipping cost vs delivery performance
4. Optimise inventory and discount strategies

**3 Dashboard Questions to Answer:**
1. Should the company reduce discounts in specific sub-categories?
2. Which region needs operational restructuring?
3. Which product lines should be discontinued?

---

## 🧹 Phase 1 — Data Cleaning

The original dataset had 9,994 rows and 21 columns. After cleaning:

| Issue Found | Fix Applied |
|---|---|
| 1 duplicate row | Removed |
| 449 postal codes missing leading zeros | Zero-padded back to 5 digits |
| 16 product names with trailing whitespace | Stripped |
| No derived columns for analysis | 7 new columns added |

**7 New Columns Created:**

| Column | Formula | Why Needed |
|---|---|---|
| `Profit_Margin_Pct` | Profit ÷ Sales × 100 | To compare products fairly by efficiency |
| `Delivery_Days` | Ship Date − Order Date | To measure shipping speed per order |
| `Is_Loss` | "Loss" if Profit < 0 else "Profit" | To colour-code visuals in Power BI |
| `Year` | Extracted from Order Date | For year-over-year trend charts |
| `Quarter` | Extracted from Order Date | For seasonal analysis |
| `Month` | Extracted from Order Date | For monthly filtering |
| `Discount_Band` | Grouped into 0%, 1-10%, 11-20%, 21-30%, 31%+ | To find the discount danger threshold |

---

## 📊 Phase 2 — Exploratory Data Analysis

All analysis was performed in **Google Colab** using Python.

### Key Findings

#### 1. Overall KPIs
| Metric | Value |
|---|---|
| Total Sales | $2,297,201 |
| Total Profit | $286,397 |
| Profit Margin | 12.47% |
| Loss-Making Orders | 1,871 (18.7%) |
| Total Profit Drain | −$156,131 |

#### 2. The Discount Trap 🔴
| Discount Band | Avg Profit | Loss Rate |
|---|---|---|
| 0% | +$66.90 | 0.0% |
| 1–10% | +$96.06 | 4.3% |
| 11–20% | +$24.74 | 14.0% |
| 21–30% | −$45.68 | **91.6%** |
| 31%+ | −$107.21 | **97.8%** |

> Any order with more than 20% discount loses money 91.6% of the time.

#### 3. Loss-Making Sub-Categories 🔴
| Sub-Category | Sales | Profit |
|---|---|---|
| Tables | $206,966 | **−$17,725** |
| Bookcases | $114,880 | **−$3,473** |
| Supplies | $46,674 | **−$1,189** |

#### 4. Regional Performance
| Region | Sales | Margin | Avg Discount |
|---|---|---|---|
| West | $725K | 14.94% | 11% ✅ |
| East | $679K | 13.48% | 15% |
| South | $392K | 11.93% | 15% |
| Central | $501K | **7.92%** | **24%** 🔴 |

#### 5. Expansion Targets ✅
| State | Profit Margin | Current Sales |
|---|---|---|
| Delaware | 36.35% | $27K |
| Minnesota | 36.24% | $30K |
| Indiana | 34.33% | $54K |

#### 6. Shipping Performance
| Ship Mode | Margin | Avg Delivery | Volume Share |
|---|---|---|---|
| First Class | 13.93% | 2.18 days | 15.4% |
| Second Class | 12.51% | 3.24 days | 19.5% |
| Same Day | 12.38% | 0.04 days | 5.4% |
| Standard Class | 12.08% | 5.01 days | **59.7%** |

---

## 📊 Phase 3 — Power BI Dashboard

Built a **5-page interactive dashboard** in Power BI Desktop.

| Page | Name | What It Shows |
|---|---|---|
| 1 | Executive Overview | 4 KPI cards, Sales vs Profit trend, Category donut, Segment bar, Year slicer |
| 2 | Loss Analysis | Sub-category profit bar, Discount band table, Segment discount, Loss products table |
| 3 | Regional Analysis | US filled map, Region comparison, Expansion targets |
| 4 | Shipping Analysis | Margin by mode, Delivery days, Volume share pie |
| 5 | Strategic Recommendations | 3 insight cards (STOP / FIX / GROW) + 6-row action table |

---

## 🎯 Strategic Recommendations

| Priority | Recommendation | Data Backing | Expected Impact |
|---|---|---|---|
| 🔴 Critical | Cap all discounts at 20% | 91.6% loss rate above 20% | Fixes $135K in discount-driven losses |
| 🔴 Critical | Discontinue Tables sub-category | −$17,725 on $207K sales | Saves $17.7K annually |
| 🔴 High | Restructure Central region discounts | 24% discount → 7.92% margin | +$35K profit potential |
| 🟠 Medium | Expand to Delaware & Minnesota | 36%+ margins, under $30K sales | High ROI market entry |
| 🟠 Medium | Promote Copiers, Paper, Labels | 37–44% margins — best in portfolio | Scale profitable lines |
| 🟡 Low | Shift Standard Class to Second Class | 1.85% margin gap, 2× faster delivery | Better experience + slight margin gain |

---

## 🏆 Result

> **2nd Place — DATAWIZ, Wizalyze Club, NMIT Bengaluru**
> **28 February 2026**

---

## 🚀 How to Run the Notebook

1. Open [Google Colab](https://colab.research.google.com)
2. Upload `Superstore_Phase2_EDA.ipynb`
3. Upload `Sample_Superstore.xls` to the Colab file panel
4. Click **Runtime → Run All**
5. Download `superstore_final_powerbi.csv` from the output
6. Load the CSV into Power BI Desktop to explore the dashboard

---

## 📬 Contact

**Poornesh** — [GitHub](https://github.com/PoorneshGowda21)

---

*Built with 💙 in 6 hours at NMIT Bengaluru*
