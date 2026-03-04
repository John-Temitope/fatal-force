# 🚨 Fatal Force — Analysing a Decade of Fatal Police Shootings in the US

> A data analysis project exploring over 10,400 fatal police shootings recorded by The Washington Post between 2015 and 2024.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Background & Context](#background--context)
- [Datasets](#datasets)
- [Tech Stack](#tech-stack)
- [Key Findings](#key-findings)
- [Project Structure](#project-structure)
- [How to Run](#how-to-run)
- [Visualisations](#visualisations)
- [Challenges](#challenges)
- [Acknowledgements](#acknowledgements)

---

## Overview

This project digs into The Washington Post's Fatal Force database — one of the most comprehensive records of fatal police shootings in the United States. The analysis covers victim demographics (race, age, gender), circumstances (armed status, threat type, flee status), mental health involvement, geographic patterns, and the agencies responsible.

The data is enriched with four US Census datasets to explore how socioeconomic factors like poverty and education correlate with where and how police killings occur.

---

## Background & Context

No comprehensive federal database of fatal police shootings existed before The Washington Post began building one in 2015. Since then, they have tracked details of every on-duty fatal shooting — gathering information from law enforcement websites, local news reports, social media, and independent databases.

This project was built to go beyond the headlines and let the numbers speak — asking questions like:

- Are certain communities killed at disproportionate rates relative to their population?
- Is the number of police killings increasing over time?
- Which cities and agencies are responsible for the most deaths?
- Does poverty connect to where killings are concentrated?

---

## Datasets

| Dataset | Source | Description |
|---|---|---|
| `fatal-police-shootings-data.csv` | The Washington Post | 10,430 records of fatal police shootings (2015–2024) |
| `fatal-police-shootings-agencies.csv` | The Washington Post | 3,727 police agencies linked to shootings |
| `Median_Household_Income_2015.csv` | US Census Bureau | Median household income by city |
| `Pct_People_Below_Poverty_Level.csv` | US Census Bureau | Poverty rate by city |
| `Pct_Over_25_Completed_High_School.csv` | US Census Bureau | High school graduation rate by city |
| `Share_of_Race_By_City.csv` | US Census Bureau | Racial demographic share by city |

---

## Tech Stack

| Tool / Library | Purpose |
|---|---|
| **Python** | Core programming language |
| **Pandas** | Data loading, cleaning, transformation and merging |
| **NumPy** | Numerical operations and array manipulation |
| **Plotly Express** | Interactive bar, pie, line, choropleth and treemap charts |
| **Matplotlib** | Static chart framework |
| **Seaborn** | KDE plots, joint plots, regression plots and heatmaps |
| **Google Colab** | Cloud notebook environment with Google Drive integration |
| **Collections (Counter)** | Counting occurrences of specific values |

---

## Key Findings

- 📈 **Rising trend** — Police killings increased every year from 995 in 2015 to 1,175 in 2024
- 🗺️ **Geographic concentration** — California (1,405), Texas (1,085), and Florida (701) account for the most killings by state
- 🏙️ **Top cities** — Los Angeles (157), Phoenix (130), and Houston (125) lead all cities
- ⚖️ **Racial disparity** — Black Americans are killed at up to **4x their population share** in cities like Chicago, Houston, and Los Angeles
- 🔫 **Armed status** — Over 58% of victims were carrying a gun; **5.42% were entirely unarmed**
- 🧠 **Mental health** — **19.7%** of all killings involved someone experiencing a mental health crisis
- 👶 **Age** — **14.56%** of victims were under 25 years old
- 🏛️ **Agencies** — The LAPD (144), US Marshals Service (136), and Phoenix PD (125) recorded the most shootings

---

## Project Structure

```
fatal-force/
│
├── Fatal_Force.ipynb          # Main analysis notebook
├── README.md                  # Project documentation
│
├── data/
│   ├── fatal-police-shootings-data.csv
│   ├── fatal-police-shootings-agencies.csv
│   ├── Median_Household_Income_2015.csv
│   ├── Pct_People_Below_Poverty_Level.csv
│   ├── Pct_Over_25_Completed_High_School.csv
│   └── Share_of_Race_By_City.csv
```

---

## How to Run

### Option 1 — Google Colab (Recommended)

1. Open the notebook in [Google Colab](https://colab.research.google.com/)
2. Upload the datasets to your Google Drive
3. Update the file paths in the **Load the Data** section to match your Drive location
4. Run all cells from top to bottom

### Option 2 — Local Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/John-Temitope/fatal-force.git
   cd fatal-force
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy plotly matplotlib seaborn
   ```

3. **Launch the notebook**
   ```bash
   jupyter notebook Fatal_Force.ipynb
   ```

4. Update any file paths in the **Load the Data** section if needed, then run all cells.

---

## Visualisations

The notebook includes the following charts:

- 📊 Bar chart — Poverty rate by US state
- 📊 Bar chart — High school graduation rate by US state
- 📈 Dual-axis line chart — Poverty rate vs graduation rate
- 🔵 Joint plot & regression — Poverty vs education relationship
- 🥧 Donut chart — Racial breakdown of fatal shootings
- 📊 Bar chart — Deaths by gender
- 📦 Box plot — Age distribution by gender and threat type
- 📊 Horizontal bar chart — Weapon types carried by victims
- 📊 Bar chart — Gun-armed vs unarmed victims
- 📈 Histogram + KDE — Age distribution of victims
- 🔵 KDE grid — Age distribution split by race
- 📊 Bar chart — Total killings by race
- 🥧 Pie chart — Mental illness involvement
- 📊 Bar chart — Top 10 cities by killings
- 🗺️ Choropleth map — Police killings by US state
- 🌡️ Heatmap — Racial kill rate ratio across top 10 cities
- 📈 Line charts — Killings over time (total, by state, by race)
- 📈 Cumulative line charts — Running totals by state and race
- 🌡️ Animated heatmap — Racial killings across states by year
- 📊 Horizontal bar chart — Top 10 agencies by total shootings
- 🌳 Treemap — Top cities by number of agencies involved
- 🥧 Pie chart — Shootings by agency type
- 📈 Facet line chart — Yearly trends for top 20 agencies
- 🌳 Treemap — Top states and their leading agencies

---

## Challenges

- **City name matching** — Merging census data with shooting records required custom logic to handle inconsistent city names across datasets and cities that span multiple states
- **Multi-valued fields** — Some records had multiple agency IDs (e.g. `491;492`) and mixed racial identifiers (e.g. `W;B`), requiring careful parsing without distorting counts
- **Missing data strategy** — Rather than dropping incomplete rows or filling blanks with zeros, missing categorical values were retained as `unknown` where appropriate, and median imputation was used only for household income
- **Animated heatmap gaps** — Categories with zero killings in a given year disappeared from the animation; fixed by re-indexing with a full MultiIndex of all year-state-race combinations

---

## Acknowledgements

- [The Washington Post](https://www.washingtonpost.com/graphics/investigations/police-shootings-database/) for maintaining and publishing the Fatal Force database
- [US Census Bureau](https://www.census.gov/) for the socioeconomic datasets

---

*Built by [Adeniran John](https://portfolio-website-i0zw.onrender.com) — Python Developer & Data Analyst*
