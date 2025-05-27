
#  Medical Feature Engineering Pipeline

This repository contains a professional, end-to-end **feature engineering pipeline** applied to a large-scale real-world **medical dataset** consisting of:

-   900,000+ patient records
-  102 raw features with **~74.7% missing values**
-  Multi-domain clinical data (renal, lipid, liver, blood, etc.)

---

##  Project Objectives

- Handle large-scale missing data using **domain-informed model-based imputation**
- Clean and validate medical data (e.g. units, ranges, outliers)
- Engineer new meaningful features to boost AI-driven diagnostics
- Generate a final dataset with **0 missing values** and **high clinical integrity**

---

##  Methodology Overview

###  1. Data Cleaning & Validation
- Removal of duplicate and corrupted records
- Standardizing inconsistent units (e.g., mg/dL, mmol/L)
- Handling implausible values (e.g., height = 0 cm)
- Column type correction and label encoding

###  2. Hierarchical Merging
- Records merged across visits using `Patient_ID`, `Visit_ID`, and `Lab_Type`
- Priority given to most recent & complete entries

###  3. Imputation Strategy
- **Group-wise modeling**: data divided into medical domains (e.g., Lipid Profile, CBC, Liver, Renal)
- **Model-based Imputation**:
  - XGBoost Regressor & Random Forest for top features
  - Trained using patients with no missing data in domain
- **Statistical fallback**:
  - Median, mean, mode, IQR for remaining NaNs

###  4. Feature Engineering
- Constructed 9+ new features including:
  - Mean Arterial Pressure (MAP)
  - TG/HDL Ratio, LDL/HDL Ratio
  - eGFR/Creatinine, Uric Ratio
- Binning & bucketing applied for risk stratification

###  5. Correlation Analysis
- Pearson/Spearman correlation heatmaps
- Feature inter-dependence visualized using `networkx`

---

##  Final Results

| Metric                | Value                   |
|-----------------------|-------------------------|
| Records               | 900,000                 |
| Original Features     | 102                     |
| Engineered Features   | 12                      |
| Final Columns         | 114                     |
| Null Values Remaining | 0                     |
| Numerical Columns     | 109                     |
| Categorical Columns   | 5                       |

---

##  Repository Structure

```bash
├── report/
│   └── Feature_Engineering_1.pdf     # Full PDF project report
├── figures/
│   └── correlation_heatmap.png       # Sample visualization
├── README.md                         # Project summary (this file)
```

>  Dataset is confidential and not included due to medical privacy constraints.

---

##  Tools & Technologies
- Python 3.10
- pandas, numpy, seaborn, matplotlib
- XGBoost, RandomForestRegressor
- scikit-learn, LightGBM
- networkx, scipy

---

##  Author

**Asma Ahmed Aqeel Alzubaidi**  
M.Sc. in Artificial Intelligence – King Khalid University  
Supervised by **Dr. Abdulmohsen Alqarni**

---

##  Related Projects

> [🔗 CIFAR-10 Multi-Model Classification](https://github.com/Asma-Ahmed-Aqil-AL-Zubaidi/cifar10-multimodel)  
> [🔗 Visual-Language Pipeline (NVIDIA Bootcamp)](https://github.com/Asma-Ahmed-Aqil-AL-Zubaidi/nvidia-vlm-project)  

---

##  Tags
`#FeatureEngineering` `#MedicalAI` `#XGBoost` `#Imputation` `#DataCleaning` `#Python` `#AIinHealthcare`

---

##  License
This project is released for educational and demonstration purposes only. Contact the author for permission to reuse.
