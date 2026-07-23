# 🎬 Netflix Content Strategy — Exploratory Data Analysis

> **Role:** Data Analyst — Content Intelligence Team
> **Tool:** Python (Google Colab) | **Dataset:** Netflix Movies & TV Shows (Kaggle)

---

## 📌 Project Overview

You are a Data Analyst hired at a media consulting firm. Your manager has handed you Netflix's complete content library dataset and asked you to:

- Understand the data structure and quality
- Clean and prepare it for analysis
- Find patterns, trends, and anomalies
- Visualize key insights across 7 charts
- Deliver **5 business recommendations** to guide Netflix's content strategy

---

## 📁 Project Structure

```
Netflix_EDA/
│
├── Netflix_EDA.ipynb       ← Main notebook (run this in Google Colab)
└── README.md               ← You are here
```

---

## 📊 Dataset

| Field | Detail |
|-------|--------|
| **Source** | [Kaggle — Netflix Movies and TV Shows](https://www.kaggle.com/datasets/shivamb/netflix-shows) |
| **Author** | Shivam Bansal |
| **Rows** | 6,234 titles |
| **Columns** | 12 |
| **Coverage** | Content available on Netflix as of mid-2021 |

### Columns

| Column | Description |
|--------|-------------|
| `show_id` | Unique ID for each title |
| `type` | Movie or TV Show |
| `title` | Name of the content |
| `director` | Director(s) — 31.6% missing |
| `cast` | Main cast members |
| `country` | Country of production |
| `date_added` | Date added to Netflix |
| `release_year` | Original release year |
| `rating` | Content rating (TV-MA, PG-13, etc.) |
| `duration` | Runtime in minutes (movies) or seasons (TV shows) |
| `listed_in` | Genre tags |
| `description` | Short synopsis |

---

## 🛠️ Tech Stack

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, cleaning, and EDA |
| `numpy` | Numerical operations |
| `matplotlib` | All chart rendering |
| `seaborn` | Heatmap visualization |

---

## 🚀 How to Run

### Option 1 — Google Colab (Recommended)

1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Upload Notebook**
3. Select `Netflix_EDA.ipynb`
4. Click **Runtime → Run All** or press `Shift + Enter` cell by cell

> The dataset is loaded automatically from a public URL — no manual download needed.

### Option 2 — Jupyter Notebook (Local)

```bash
# 1. Install dependencies
pip install pandas numpy matplotlib seaborn

# 2. Launch Jupyter
jupyter notebook Netflix_EDA.ipynb
```

---

## 📋 Notebook Walkthrough

### Step 0 — Setup
Imports all libraries and applies a consistent Netflix-inspired dark theme across all charts.

---

### Step 1 — Load & Inspect the Data
- Loads the CSV from a public GitHub mirror
- Checks `.shape`, `.dtypes`, `.isnull()`, `.duplicated()`
- Prints a **5-line plain-English summary** of what the dataset contains

**Key finding:** Zero duplicates. Director info is missing for 31.6% of titles — but dropping those rows would destroy too much data.

---

### Step 2 — Clean the Data

Every cleaning decision is documented with a reason:

| Column | Action | Reason |
|--------|--------|--------|
| `director` | Fill → `"Unknown"` | Dropping 31% of rows loses too much data |
| `cast` | Fill → `"Unknown"` | Same reasoning; 9% missing |
| `country` | Fill → `"Unknown"` | Preserves 476 rows for other analysis |
| `rating` | Fill → `"NR"` | NR (Not Rated) is a valid Netflix classification |
| `date_added` | Parse to `datetime` | Enables year/month extraction |
| `country` | Extract first listed | Multi-country titles use first as primary origin |
| `duration` | Extract numeric value | Converts `"90 min"` → `90` for numerical analysis |

---

### Step 3 — Exploratory Data Analysis (5 Questions)

| # | Question | Method Used |
|---|----------|-------------|
| Q1 | Most common genres on Netflix? | `value_counts()` |
| Q2 | Which rating produces the longest movies? | `groupby` + `mean()` |
| Q3 | How has content volume grown year-over-year? | `groupby` + `unstack()` |
| Q4 | How do US, India, UK differ in content type? | `groupby` + `unstack()` |
| Q5 | What does a typical Netflix TV show look like? | `describe()` + `value_counts()` |

---

### Step 4 — Visualizations (7 Charts)

| # | Chart Type | What It Shows |
|---|-----------|---------------|
| 1 | Bar Chart | Movies vs TV Shows count |
| 2 | Line Chart | Titles added per year (2008–2020) |
| 3 | Histogram | Movie duration distribution |
| 4 | Scatter Plot | Release year vs year added to Netflix |
| 5 | Pie Chart | Content rating breakdown |
| 6 | Heatmap | Monthly additions by year (2015–2020) |
| 7 | Horizontal Bar | Top 10 countries by content volume |

All charts include:
- ✅ Title
- ✅ Axis labels
- ✅ Legend where applicable
- ✅ One-line insight printed below each chart

---

### Step 5 — Business Insights Report

Five data-backed recommendations delivered as a formal analyst memo:

| # | Insight | Chart Reference |
|---|---------|----------------|
| 1 | Double down on TV originals — they drive lower churn | Chart 1 + Chart 2 |
| 2 | Time big releases for Q4 (Oct–Dec peak) | Chart 6 |
| 3 | Invest in Indian TV series, not just Bollywood movies | Chart 7 + EDA Q4 |
| 4 | Keep movies in the 90–110 min sweet spot | Chart 3 |
| 5 | Expand family/kids content to defend against Disney+ | Chart 5 |

---

## 📈 Key Findings at a Glance

- **68.4%** of Netflix content is Movies; TV shows are catching up fast
- Netflix added **26× more content** in 2019 vs 2015
- The average Netflix movie is **99 minutes** long
- **TV-MA + TV-14** ratings account for nearly **60%** of all titles
- India contributes **777 titles** but 93% are movies — TV is an untapped market
- **50%** of Netflix TV shows have only 1 season

---

## 👤 Author

**Karan** — Data Analysis Assignment
Course: TuteDude | Python & Data Analysis Track

---

## 📄 License

Dataset: [CC0 Public Domain](https://creativecommons.org/publicdomain/zero/1.0/) via Kaggle
