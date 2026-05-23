# FIFA-Player-Dataset-Analysis-Using-Web-Scraping-Techniques
# ⚽ Scouting with Python: FIFA Player Analytics via Web Scraping

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)](https://jupyter.org)
[![BeautifulSoup](https://img.shields.io/badge/BeautifulSoup-4-green)](https://www.crummy.com/software/BeautifulSoup/)
[![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

> A complete end-to-end data science project that scrapes live FIFA player statistics from **sofifa.com**, cleans and transforms the data, and delivers rich exploratory analysis with professional visualizations.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Project Structure](#-project-structure)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Notebook Walkthrough](#-notebook-walkthrough)
- [Visualizations](#-visualizations)
- [Dataset Description](#-dataset-description)
- [Key Findings](#-key-findings)
- [Ethical Scraping](#-ethical-scraping)
- [Future Work](#-future-work)
- [License](#-license)

---

## 🌍 Overview

This project demonstrates a full **data science pipeline** built around web scraping:

1. **Collect** — Scrape FIFA player data (ratings, market values, wages, positions, nationalities) directly from [sofifa.com](https://sofifa.com)
2. **Clean** — Parse and transform raw HTML into structured tabular data
3. **Analyse** — Perform exploratory data analysis (EDA) on ~300+ players
4. **Visualise** — Generate publication-quality charts to uncover patterns and insights

Whether you're a football enthusiast, a data science student, or a developer exploring web scraping techniques, this project serves as a practical, hands-on reference.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🕷️ **Live Web Scraping** | Fetches real-time data from sofifa.com using `requests` + `BeautifulSoup` |
| 🧹 **Data Cleaning** | Handles currency parsing (`€120.5M` → float), duplicates, and missing values |
| 📊 **6 Visualizations** | Histograms, scatter plots, violin plots, KDE density maps, bar charts, heatmaps |
| 🔢 **Correlation Analysis** | Pearson correlation matrix across all numeric features |
| 💾 **CSV Export** | Saves cleaned dataset to `fifa_players_cleaned.csv` |
| 🤝 **Ethical Scraping** | Polite delays between requests; browser-like headers |

---

## 📁 Project Structure

```
fifa-web-scraping/
│
├── fifa_analysis.ipynb          # Main Jupyter Notebook
├── fifa_players_cleaned.csv     # Exported cleaned dataset (auto-generated)
│
├── outputs/                     # Saved chart images
│   ├── overall_distribution.png
│   ├── age_vs_overall.png
│   ├── top_value_players.png
│   ├── top_nationalities.png
│   ├── overall_vs_potential.png
│   ├── age_by_rating_band.png
│   └── correlation_heatmap.png
│
├── README.md                    # Project documentation
└── requirements.txt             # Python dependencies
```

---

## 🛠️ Tech Stack

| Library | Version | Purpose |
|---|---|---|
| `requests` | 2.x | HTTP requests for web scraping |
| `beautifulsoup4` | 4.x | HTML parsing |
| `lxml` | 4.x | Fast HTML/XML parser backend |
| `pandas` | 2.x | Data manipulation and analysis |
| `numpy` | 1.x | Numerical operations |
| `matplotlib` | 3.x | Base plotting library |
| `seaborn` | 0.x | Statistical visualizations |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook or JupyterLab

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/your-username/fifa-web-scraping.git
cd fifa-web-scraping
```

**2. Create a virtual environment (recommended)**

```bash
python -m venv venv
source venv/bin/activate        # macOS/Linux
venv\Scripts\activate           # Windows
```

**3. Install dependencies**

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install requests beautifulsoup4 lxml pandas numpy matplotlib seaborn jupyter
```

**4. Launch Jupyter Notebook**

```bash
jupyter notebook fifa_analysis.ipynb
```

**5. Run all cells**

Go to **Kernel → Restart & Run All** and the notebook will scrape, clean, analyse, and visualise automatically.

---

## 📓 Notebook Walkthrough

The notebook is organized into **8 sections**:

| Section | Description |
|---|---|
| **1. Libraries** | Import all dependencies and configure plot styles |
| **2. Web Scraping** | Paginated scraping of sofifa.com player listings |
| **3. Data Cleaning** | Type coercion, currency parsing, deduplication |
| **4. EDA** | Top players, nationality counts, descriptive statistics |
| **5. Visualizations** | 6 charts covering ratings, age, value, and nationality |
| **6. Correlation** | Heatmap of Pearson correlations between numeric fields |
| **7. Export** | Save cleaned DataFrame to CSV |
| **8. Summary** | Printed live summary of key dataset metrics |

---

## 📊 Visualizations

| Chart | Insight |
|---|---|
| **Overall Rating Distribution** | Most players cluster between 65–75; elite players are rare |
| **Age vs Overall (scatter)** | Peak performance typically between ages 25–30 |
| **Top 10 Players by Value** | Market value is heavily skewed toward a small elite |
| **Top 15 Nationalities** | England, Germany, Spain dominate the player pool |
| **Overall vs Potential (KDE)** | Young players show the highest growth headroom |
| **Age by Rating Band (violin)** | Higher-rated bands show tighter, older age distributions |
| **Correlation Heatmap** | Strong correlation between Overall ↔ Value and Overall ↔ Wage |

---

## 🗂️ Dataset Description

The scraped and cleaned dataset contains the following columns:

| Column | Type | Description |
|---|---|---|
| `Name` | string | Player full name |
| `Nationality` | string | Country of origin |
| `Club` | string | Current club team |
| `Positions` | string | Playing positions (e.g. `ST`, `CAM`) |
| `Age` | int | Player age |
| `Overall` | int | Current FIFA overall rating (0–99) |
| `Potential` | int | Maximum potential rating (0–99) |
| `Growth` | int | Potential − Overall (growth headroom) |
| `Value_EUR` | float | Market value in Euros |
| `Wage_EUR` | float | Weekly wage in Euros |

---

## 🔍 Key Findings

- 📈 **Overall ratings** follow a roughly normal distribution centred around **67–70**
- 💰 **Market value** and **weekly wage** are strongly correlated with Overall rating (`r > 0.85`)
- 🎂 **Peak performance** age is typically **25–30** years old
- 🌍 **England, Germany, and Spain** consistently have the most players in top leagues
- 🌱 **Young players (U21)** with high Potential scores represent the best growth investment

---

## ⚖️ Ethical Scraping

This project follows responsible web scraping practices:

- ✅ Adds **1.5-second delays** between requests to avoid server overload
- ✅ Uses **browser-like headers** for standard identification
- ✅ Scrapes only **publicly available data** — no login or paywalled content
- ✅ Does **not store or redistribute** the scraped data commercially
- ⚠️ Always review a website's `robots.txt` and Terms of Service before scraping

---

##  Future Work

- [ ] Scrape **individual player detail pages** for granular skill attributes (pace, shooting, dribbling, etc.)
- [ ] Add **time-series tracking** — monitor player ratings across multiple FIFA editions
- [ ] Build a **player comparison tool** (radar charts)
- [ ] Train a **regression model** to predict market value from player stats
- [ ] Deploy as an **interactive Streamlit or Dash dashboard**

---

## 🙌 Acknowledgements

- Player data sourced from [sofifa.com](https://sofifa.com) (public FIFA stats tracker)
- FIFA is a registered trademark of **EA Sports** — this project is unofficial and for educational purposes only

---

<p align="center">Made with ❤️ and Python &nbsp;|&nbsp; ⭐ Star this repo if you found it useful!</p>
