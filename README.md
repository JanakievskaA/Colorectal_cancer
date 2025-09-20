
# Colorectal Cancer Incidence Prediction  

**Colorectal Cancer Incidence Prediction** is a machine learning project that forecasts colorectal cancer incidence rates across countries worldwide. The project not only predicts incidence but also identifies the most influential dietary and lifestyle risk factors. In addition, clustering techniques are applied to group countries into risk profiles, offering actionable insights for global public health strategies.  

---

##  Data & Methods  

- **Sources (2020–2023):**  
  - World Bank (demographics, lifestyle data)  
  - FAOSTAT (dietary indicators)  
  - Global Health Observatory (obesity, alcohol, tobacco use)  
  - Global Cancer Observatory (colorectal cancer incidence)  
- **Preprocessing:**  
  - Median imputation for missing values  
  - Removal of highly correlated features  
  - Standardization with `StandardScaler`  
  - Outlier filtering using **IsolationForest** (8 countries removed → 137 kept)  
- **Variables:**  
  - Risk factors – obesity, alcohol & tobacco, fat & red meat consumption, low physical activity  
  - Neutral factors – total energy supply, carbohydrates, sweeteners  
  - Outcome – number of colorectal cancer cases per 100,000 inhabitants  

---

##  Predictive Models  

- **Main Models:**  
  - **XGBoost** (R² = 0.78, best performance)  
  - **Random Forest** (slightly lower R², still strong)  
- **Validation:** Leave-One-Out Cross-Validation (LOOCV)  
- **Hyperparameter Tuning:** RandomizedSearchCV  
- **Baseline Models:** KNN (best among additional), SVR, Linear Regression  
- **Target Transformation:** Applied `log1p` to incidence due to right skewness, reverted predictions to original scale  

---

##  Interpretability  

- **Feature Importance (XGBoost):** Ranked most relevant predictors, model achieved R² = 0.78 on test data 
- **SHAP Analysis:** Showed not only variable importance but also *direction of influence* (e.g., higher fat supply → higher incidence)

---

##  Clustering  
 
- **Clustering Method:** **KMeans** (k=3), optimal clusters determined by Silhouette Score & Elbow Method  
- **Visualization:** PCA (95% variance explained) used for 2D representation  
- **Cluster Profiles:**  
  - **Low Risk (55 countries):** Mainly Africa & SE Asia – plant-based diets, lowest incidence  
  - **Medium Risk (69 countries):** Europe, Asia, Latin America – mixed dietary patterns, moderate incidence  
  - **High Risk (21 countries):** Mostly Europe & Oceania – high fat and animal protein intake, highest incidence  
<img width="907" height="651" alt="PCA" src="https://github.com/user-attachments/assets/44d8bb27-00ee-4e20-afcf-33df8b25afd5" />

---

##  Conclusion  

This project shows how machine learning can improve cancer epidemiology by combining predictive modeling, interpretability, and clustering. The findings highlight the value of data-driven methods for designing targeted prevention strategies and allocating health resources more effectively.  

