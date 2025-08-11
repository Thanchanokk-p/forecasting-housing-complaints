# forecasting-housing-complaints
Forecasting High-Priority Housing Complaints in NYC 311

# Forecasting High-Priority Housing Complaints in NYC 311

## 📌 Overview
This project develops a **predictive model** to forecast **high-priority housing complaints** in New York City's 311 service system.  
The goal is to help the NYC Department of Housing Preservation and Development (**HPD**) **allocate resources efficiently** and **respond faster** to urgent housing issues, such as heating and hot water complaints.

---

## 🎯 Problem Statement
NYC’s 311 receives a large volume of housing complaints annually.  
Current processing follows a **first-come, first-served** basis without predictive prioritization, leading to delays in resolving urgent issues.

**Business Objectives:**
- Predict the likelihood of **high-priority complaints** in specific areas.
- Optimize **workforce and budget allocation** for HPD.
- Proactively prevent **system overload** and escalate response times for urgent cases.

**Value Proposition:**
- **For HPD & NYC Government:** Better resource allocation and emergency preparedness.
- **For Residents:** Faster resolution of urgent complaints and improved trust in public services.

---

## 📊 Data Sources
Two main datasets were used (~2.5 GB total):

1. **[311 Service Request Dataset](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9/about_data)** (2011–2019) – Complaint records for trend and pattern analysis.
2. **[PLUTO Dataset](https://www.nyc.gov/assets/planning/download/pdf/data-maps/open-data/dwn-pluto-mappluto.pdf)** – Property and building characteristics for spatial and contextual insights.

---

## 🛠 Methodology

### 1. Data Preparation
- **Cleaning:** Handled null values, removed duplicates, corrected outliers, standardized formats.
- **Feature Engineering:** Created variables (e.g., building age) and handled skewness using Box-Cox transformation.
- **Feature Selection:** Used Spearman correlation to select features with >0.15 correlation to the target variable.

### 2. Model Development
- **Class Imbalance Handling:** Applied **ADASYN** to balance classes.
- **Models Tested:** Logistic Regression, XGBoost, Neural Networks.
- **Evaluation Metric Priority:** **Recall** (minimizing missed urgent complaints).

### 3. Model Fine-Tuning
- **Logistic Regression:** RFE with Pipeline + Randomized Search improved recall/F1-score.
- **XGBoost:** Fine-tuned hyperparameters for recall optimization.
- **Neural Networks:** Adjusted learning rate, early stopping, and batch size.

### 4. Final Model
- **Chosen Model:** **Fine-Tuned XGBoost** with **Youden’s J threshold adjustment**.
- **Performance:** Recall = 0.78, FNR = 0.22 (best at detecting real complaints).

---

## 📈 Key Insights
- **Heat/Hot Water Complaints** account for 42% of reports, peaking in winter.
- **The Bronx**, especially Grand Concourse, experiences the highest complaint density.
- **Building age** is a strong predictor of heating issues.
  **Seasonal trends** show complaints spike sharply from October to February.
- **Geospatial clustering** reveals high-density complaint zones in specific ZIP codes.
- **Recall prioritization** is critical—missing urgent complaints has higher costs than false positives.
---

## 🔮 Future Improvements
- Incorporate **weather data**, **maintenance history**, and **landlord responsiveness**.
- Explore **hybrid models** combining rules-based and ML predictions.
- Implement **time-series anomaly detection** for early warnings.
- Use **SHAP/LIME** for model explainability.
- Conduct **real-world pilot testing** for threshold optimization.

---

## 📂 Repository Structure
```bash
├── data/ # Raw and processed datasets (not included in repo)
├── notebooks/ # Jupyter notebooks for EDA and modeling
├── scripts/ # Python scripts for preprocessing and modeling
├── README.md # Project documentation
└── requirements.txt # Dependencies
```
