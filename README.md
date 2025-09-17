# Crime and Guns: Do Gun Laws Affect Crime in 2025?

This repository explores whether **gun laws and policies have a measurable effect on crime rates** across different countries in 2025.

We merge two public datasets:

* [Overview of gun laws by nation (Wikipedia)](https://en.wikipedia.org/wiki/Overview_of_gun_laws_by_nation)
* [Crime rate by country (World Population Review)](https://worldpopulationreview.com/country-rankings/crime-rate-by-country)

The notebook demonstrates data wrangling, regression analysis, and statistical testing to answer a hotly debated question:
👉 *Do countries that allow guns for personal protection or require a "good reason" have different crime rates?*

---

## Data Sources

* **Gun laws**: extracted from Wikipedia tables (license rules, restrictions, reasons for ownership).
* **Crime index**: Numbeo 2024 crime index (values 1–100, higher = more crime).

---

## Methods

* **Data Cleaning & Normalization**

  * Handle mismatched country names between datasets.
  * Normalize regions like "DR Congo → Democratic Republic of the Congo".
  * Fix missing U.S. values manually.

* **Statistical Analysis**

  * Compare mean crime rates across law categories (`Yes for Personal Protection`, `Yes for Good Reason`).
  * Run **OLS regression models**.
  * Apply **Tukey post-hoc test** for multiple comparisons.

* **Key Libraries**:

```python
import requests
import pandas as pd
import numpy as np
import statsmodels.formula.api as smf
import statsmodels.stats.multicomp as multi
```

---

## Results

* Allowing **personal protection (PP)** alone: no statistically significant impact on crime index.
* Allowing guns for a **good reason (GR)**: no significant difference either.
* **Interesting finding**: when laws allow **Personal Protection = Yes** but **Good Reason = No**, the crime index is statistically different (Tukey HSD test, p < 0.05).

---

## Example Data Snapshot

| Country       | Crime Index | Yes for PP | Yes for GR | Yes for PP\&GR |
| ------------- | ----------- | ---------- | ---------- | -------------- |
| Venezuela     | 81.2        | 0          | 0          | 00             |
| Andorra       | 12.9        | 1          | 0          | 10             |
| United States | 49.0        | 1          | 1          | 11             |

---

## Important Note

This project is for **educational and exploratory purposes only**.

* The datasets are incomplete, inconsistently defined, and not peer-reviewed.
* Real-world policy analysis requires far more rigorous data and methodology.

---

## How to Run

1. Clone this repo:

```bash
git clone https://github.com/your-username/crime-and-guns-2025.git
cd crime-and-guns-2025
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Run the Jupyter notebook:

```bash
jupyter notebook
```

---
