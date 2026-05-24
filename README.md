# Cosmetic Process Optimization: Dual-Engine Multivariate Analysis (MANOVA)

An industrial data analytics project that evaluates the multi-variable quality profile of a cosmetic emulsion formulation using an interactive Excel process dashboard alongside a Python-driven Multivariate Analysis of Variance (MANOVA) statistical engine.

## 🧪 Project Overview
In cosmetic manufacturing, altering process parameters typically impacts multiple physical properties simultaneously. This project simulates and analyses **120 production batches** of a hair cream formulation to determine how variations in formula ingredients and processing temperatures interact to affect the final product's physical vector space.

### Independent Variables (Factors)
* **Formula Type:** Standard, Organic Polymer, Surfactant Boosted
* **Mixing Temperature:** Low (35°C) vs. High (60°C)

### Dependent Variables (Quality Metrics)
* **Viscosity (cP):** Emulsion thickness (Target: 2000–3500 cP)
* **pH:** Skin safety and compatibility (Target: 6.0–7.0)
* **Stability (Days):** Product shelf life before phase separation (Target: > 10 days)

---

## 📊 Dual-Engine Methodology

### 1. Excel Interactive Dashboard
* **Cross-Tabulation:** Built structured Pivot Tables to isolate and compute multivariate averages for every combination of formula and temperature treatment.
* **Dynamic Control:** Integrated interactive **Slicers** to allow plant operators and quality control managers to dynamically filter and inspect chemical batch traits on the fly.
* **Exploratory Insights:** Visually identified a stark, universal drop in product shelf life (`Stability_Days`) when batches were exposed to high thermal mixing configurations.

### 2. Python Statistical Engine (`statsmodels` & `seaborn`)
* **Type I Error Protection:** Utilizing a multivariate approach (MANOVA) instead of running isolated ANOVAs protected the experiment against alpha inflation ($1 - 0.95^3 \approx 14.3\%$ false-positive risk).
* **Data Visualization:** Generated paired subplots featuring 95% Confidence Interval error bars to visually map data distribution variance and overlap metrics.
* **Mathematical Validation:** Executed a two-way MANOVA to mathematically prove the standalone significance of process factors and map interaction boundaries.

---

## 📈 Key Statistical Findings

The Python MANOVA script generated the following multivariate outputs based on **Wilks' Lambda ($\Lambda$)**:

| Process Factor | Wilks' Lambda ($\Lambda$) | P-Value (`Pr > F`) | Industrial Significance |
| :--- | :--- | :--- | :--- |
| **Formula Type** | 0.0896 | < 0.001 | 🔴 Highly Significant standalone effect |
| **Mixing Temperature** | 0.5768 | < 0.001 | 🔴 Highly Significant standalone effect |
| **Formula × Temperature** | 0.9498 | **0.4432** | 🟢 Non-Significant Interaction |

### Operational Conclusions:
1. **The Interaction is Not Significant ($P = 0.443$):** This mathematically confirms that temperature variations affect all three formulation matrices uniformly. There are no volatile, specific chemical interactions unique to a single pairing.
2. **Thermal Degradation:** Combining the non-significant interaction with the visual confidence intervals proves that high heat consistently degrades emulsion stability across the board. 
3. **Actionable Recommendation:** To maximize shelf life without sacrificing viscosity metrics, the production line should prioritize **Low-Temperature (35°C) mixing profiles**, specifically utilizing the **Organic Polymer** baseline for optimal long-term batch stability.

---

## 💻 Tech Stack & Libraries Used
* **Spreadsheet Architecture:** Microsoft Excel (Pivot Tables, Advanced Filtering, Slicers, Custom Layouts)
* **Language Engine:** Python 3.x
* **Data Manipulation:** `pandas`
* **Statistical Modeling:** `statsmodels.multivariate.manova`
* **Data Visualization:** `seaborn`, `matplotlib`

## 📂 Repository Structure
```text
├── cosmetic_process_optimization.csv    # Raw experimental dataset (120 batches)
├── process_dashboard.xlsx               # Excel file with Pivot Tables and Slicers
├── manova_engine.py                     # Python statistical testing pipeline
├── process_optimization_plots.png       # Generated interaction bar charts
└── README.md                            # Project documentation