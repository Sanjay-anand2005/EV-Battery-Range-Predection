# EV Battery Range Prediction

Predicting the **real-world driving range** of electric vehicles using machine learning — because certified ARAI range rarely matches reality.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Pandas](https://img.shields.io/badge/pandas-2.0%2B-green)
![scikit--learn](https://img.shields.io/badge/scikit--learn-1.3%2B-orange)
![Status](https://img.shields.io/badge/status-in--progress-yellow)

---

## Overview

A significant challenge for EV owners is **range anxiety** — the fear that a vehicle has insufficient range to reach its destination. While manufacturers provide certified range figures (like ARAI in India), these are often measured under ideal conditions and rarely reflect real-world performance.

This project builds a predictive model that estimates real-world EV range more accurately by considering factors such as ambient temperature, AC usage, traffic, terrain, battery age, and driving style.

The current state of the project covers **comprehensive Exploratory Data Analysis (EDA)** and **Data Cleaning**.

---

## Problem Statement

Certified EV range figures are misleading. Real-world range is affected by:
- Battery capacity & age
- Vehicle weight & aerodynamics
- Ambient temperature & AC usage
- Terrain, traffic, and driving style

Drivers need a data-driven estimate — not a brochure number.

---

## Objectives

- [x] Perform EDA to uncover key patterns and relationships in the EV dataset
- [x] Analyze how battery capacity, vehicle weight, and driving conditions affect real-world range
- [x] Clean and preprocess data (outliers, skewness)
- [ ] Build and evaluate ML models (Linear Regression, Random Forest, XGBoost)
- [ ] Identify the most influential features for accurate prediction
- [ ] Deploy as a web app (Streamlit)

---

## Dataset

**Source:** [`SohamThakkar-07/india-ev-range-dataset`](https://huggingface.co/datasets/SohamThakkar-07/india-ev-range-dataset) (Hugging Face)

- **7,291 rows** × **25 columns**
- **No missing values**, **no duplicates**
- Features include: `battery_capacity_kWh`, `motor_power_kW`, `vehicle_weight_kg`, `drag_coefficient_Cd`, `ambient_temperature_C`, `ac_usage`, `terrain_type`, `battery_age_years`, `energy_consumption_kWh_per_km`, `real_world_range_km`, `ARAI_certified_range_km`, and more.
- **Target:** `real_world_range_km`

The dataset loads automatically in the notebook.

---

## Technologies Used

| Category | Tools |
|---|---|
| Language | Python 3.10+ |
| Data Manipulation | pandas, numpy |
| Visualization | matplotlib, seaborn |
| Dataset Loading | Hugging Face `datasets` |
| Environment | Jupyter Notebook |
| ML (upcoming) | scikit-learn, XGBoost |

---

## Installation

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/ev-battery-range-prediction.git
cd ev-battery-range-prediction

# 2. Create and activate a virtual environment
python3 -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch Jupyter
jupyter notebook notebooks/Project_EV1.ipynb
```

The notebook auto-downloads the dataset on first run — no manual setup needed.

---

## Key Findings (EDA)

- **Correlation:** `battery_capacity_kWh` has a strong positive correlation with `ARAI_certified_range_km` (**0.80**) and a moderate positive correlation with `real_world_range_km` (**0.33**).
- **Energy Consumption:** `battery_capacity_kWh` is strongly negatively correlated with `energy_consumption_kWh_per_km` (**-0.64**), as physically expected.
- **Skewness:** `price_lakh_INR` (skew ≈ **5.14**), `energy_consumption_kWh_per_km` (**1.92**), and `motor_power_kW` (**1.03**) are significantly right-skewed.
- **Outliers:** IQR analysis reveals a wide spread — from budget EVs (₹7 lakh) to luxury models (₹750 lakh) — meaning outlier handling must preserve legitimate premium vehicles.

---

## Results & Visualizations

The notebook includes:
- 📊 Histograms for all numerical features (distribution & skewness)
- 🔥 Correlation heatmap of numeric features
- 🔵 Scatter plot: Battery Capacity vs. Real-World Range
- 📈 KDE plots for skewed features

> Add screenshots of these plots to the `assets/` folder and reference them here, e.g.
> `![Correlation Heatmap](assets/correlation_heatmap.png)`

---

## Future Improvements

- **Feature Engineering:** power-to-weight ratio, combined "harsh driving" score
- **Transformations:** log-transform skewed features like `price_lakh_INR`
- **Modeling:** train & compare Linear Regression, Random Forest, XGBoost
- **Tuning:** GridSearchCV for hyperparameter optimization
- **Deployment:** interactive Streamlit web app for live range prediction

---

## Author

**Sanjay Anand**
- GitHub: [@sanjay-anand](https://github.com/sanjay-anand)
- Add your LinkedIn / email if you want

---

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
