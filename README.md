# Bass Model Analysis: EcoFlow Ocean Pro Home Battery Storage

**Course:** DS 223 Marketing Analytics  
**Author:** Silva Vardanyan  
**Date:** 03.04.2026  

---

## Overview

This project applies the **Bass Diffusion Model** to predict the adoption of the [EcoFlow Ocean Pro Home Battery Storage](https://time.com/collections/best-inventions-2025/7318344/ecoflow-ocean-pro-home-battery-storage/), selected from TIME Magazine's Best Inventions of 2025 list.

Since the EcoFlow Ocean Pro is a newly launched product with no historical adoption data, a **look-alike analysis** is performed using the **Tesla Powerwall** (2015–2025) as the comparable innovation. Bass Model parameters (p, q, M) are estimated from Powerwall historical installation data and then applied to forecast EcoFlow Ocean Pro diffusion through 2039.

---

## Innovation Selected

**EcoFlow Ocean Pro Home Battery Storage**  
🔗 [TIME Best Inventions 2025](https://time.com/collections/best-inventions-2025/7318344/ecoflow-ocean-pro-home-battery-storage/)

The EcoFlow Ocean Pro uses sodium-ion (seawater-inspired) battery chemistry, making it non-flammable and environmentally safer than lithium-ion alternatives. It is designed for residential solar integration and broad market accessibility.

## Look-Alike Innovation

**Tesla Powerwall** — a lithium-ion home battery storage system launched in 2015.  
Both products target homeowners, integrate with solar PV systems, and compete in the residential energy storage market, making the Powerwall a structurally appropriate look-alike for Bass Model parameter estimation.

---

## Key Results

| Parameter | Value |
|---|---|
| p - coefficient of innovation | 0.00093 |
| q - coefficient of imitation | 0.5929 |
| M - market potential (Powerwall, NLS) | 1,724,786 |
| M - market potential (EcoFlow, Fermi) | 2,200,000 |
| Predicted peak adoption year (EcoFlow) | ~2035 |
| Cumulative adopters by 2039 | 2,024,408 (~92% of M) |

---

## Repository Structure

```
├── bass_model_ecoflow.Rmd        # Main R Markdown source file
├── README.md                     # This file
│
├── data/
│   └── Tesla Powerwall.csv       # Historical Tesla Powerwall installation data (2015–2025)
│
└── report/
    └── Bass Model Analysis - EcoFlow.pdf    # Final compiled PDF report
```

---

## Data

**File:** `data/Tesla Powerwall.csv`  
**Description:** Annual and cumulative Tesla Powerwall installations from 2015 to 2025, compiled from Tesla quarterly reports, Wikipedia, and industry analyses.  
**Columns:**
- `Year` — calendar year
- `Installations` — annual unit installations
- `Cumulative` — cumulative installations to date
- `Source` — reference URL for each data point

---

## Methods

1. **Look-alike selection** — Tesla Powerwall chosen as the comparable product
2. **Bass Model parameter estimation** using two methods:
   - Method 1: Non-Linear Least Squares (`nls()`) → p = 0.00093, q = 0.5929, M = 1,724,786
   - Method 2: `diffusion` package → p = 0.0024, q = 0.4615, M = 2,252,152
3. **Market potential estimation** for EcoFlow Ocean Pro via Fermi's logic → M = 2,200,000
4. **Diffusion forecast** for 2025–2039 using NLS-estimated p and q applied to EcoFlow's M

---

## How to Reproduce

### Requirements

- R (≥ 4.3)
- RStudio
- TinyTeX or a LaTeX distribution (for PDF knitting)

### Required R Packages

```r
install.packages(c("ggplot2", "ggpubr", "knitr", "diffusion", "dplyr", "formatR"))
```

### Steps

1. Clone or download this repository
2. Open `Bass_Model_Analysis.Rproj` in RStudio
3. Ensure the data file is located at `data/Tesla Powerwall.csv`
4. Open `bass_model_ecoflow.Rmd`
5. Click **Knit → Knit to PDF**

> If TinyTeX is not installed, run `tinytex::install_tinytex()` in the R console first.

---

## References

- Bass, F. M. (1969). A new product growth for model consumer durables. *Management Science*, 15(5), 215–227.
- Rogers, E. M. (1962). *Diffusion of Innovations*. Free Press.
- Tesla, Inc. (2025). *1 Million Powerwalls Installed*. https://www.tesla.com/en_qa/learn/1-million-powerwalls-installed
- Tesla, Inc. (2019). *Q4 2018 Update Letter*. https://cdn.arstechnica.net/wp-content/uploads/2019/01/Tesla-2018-Q4-Update-Letter1.pdf
- Drive Tesla Canada (2024). *Tesla reaches 750,000 Powerwall installs worldwide*. https://driveteslacanada.ca/news/tesla-reaches-750000-powerwall-installs-worldwide/
- Benzinga (2023). *Tesla Energy Passes 500,000 Powerwall Installations*. https://www.benzinga.com/news/23/06/32901830
- TIME Magazine (2025). *Best Inventions 2025 — EcoFlow Ocean Pro*. https://time.com/collections/best-inventions-2025/7318344/ecoflow-ocean-pro-home-battery-storage/
- BDG (2021). *Residential Energy Storage Report*. https://www.dret-ca.com/wp-content/uploads/2021/03/Residential-Energy-Storage-by-BDG-Final-Report.pdf
- World Bank (2024). *World Development Indicators*. https://data.worldbank.org
