# Modeling Soil Organic Carbon under Climate Change Scenarios: A Heterogeneous Ensemble Machine Learning Approach

This repository contains a Python re-implementation of my MSc thesis research, originally conducted in R. The project focuses on predicting Soil Organic Carbon (SOC) across the Iberian Peninsula (Portugal and Spain) and assessing the potential impact of climate change (SSP585 scenario) on SOC stocks.

## 📖 Project Overview
Soil Organic Carbon (SOC) is a critical indicator of soil health and climate regulation. This study develops a predictive framework using five individual machine learning algorithms and a heterogeneous ensemble approach. The objective is not only to improve prediction accuracy but also to provide insights into future SOC dynamics under climate change, supporting sustainable soil management.

## 🛠️ Methodology
- **Corrected Temporal Framework:** A key scientific improvement in this Python implementation is the correction of a temporal mismatch present in the original R workflow. The ensemble models were trained using **current climate variables** (`Temp_Iberi`, `Prec_World`) to predict current SOC. Then, future SOC was predicted by substituting the current climate variables with **future scenario variables** (`t58560`, `pr58060`). This ensures scientific validity and prevents data leakage.
- **Base Models:** Five algorithms were trained and tuned using `scikit-learn` and `xgboost`: Random Forest (RF), XGBoost, Cubist (HistGradientBoostingRegressor as proxy), Support Vector Regression (SVR), and Decision Tree (DT).
- **Ensemble Strategy:** A heterogeneous ensemble was constructed using a weighted averaging approach. The optimal weights were determined through 1,000 iterations of random sampling and normalization.
- **Dataset:** 
  - Target variable: LUCAS 2018 topsoil (0-20 cm) SOC measurements across the Iberian Peninsula (N = 1,223 samples).
- **Predictors (SCORPAN framework):** Climate (precipitation, temperature), Topography (Elevation, Slope, TWI), Vegetation (EVI), and Soil properties (EC).

## 📂 Repository Structure
- `SOC.ipynb`: The main Python notebook containing data loading, model training, ensemble construction, and both current and future predictions.
- `Scenario.csv`: The input dataset containing both current and future climate variables.
- `current_predictions_ensemble.csv`: Predicted SOC under current climate conditions.
- `scenario_predictions_future.csv`: Predicted SOC under the SSP585 climate scenario (2021-2040).
- `ensemble_weights.csv`: Optimal weights of the base learners in the ensemble.

## 📊 Key Findings
- **Model Performance:** The corrected ensemble model achieved **R² = 0.360** on the test dataset, demonstrating reliable predictive capability for SOC mapping.
- **Ensemble Weights:** Random Forest and Cubist received the highest weights in the ensemble, demonstrating their robustness for SOC modeling.
- **Future Projections:** The corrected future predictions indicate a general decline in SOC under the SSP585 scenario, with croplands showing the largest losses.

## ⚙️ How to Run
1. Clone the repository.
2. Ensure the required libraries are installed: `pip install pandas numpy scikit-learn xgboost`
3. Open `SOC.ipynb` in Jupyter Notebook or JupyterLab.
4. Run the cells sequentially to reproduce the results.

## 📧 Contact
Hadiyeh Hassan Nia Badrabad
MSc in Remote Sensing and GIS
Shahid Beheshti University, Tehran, Iran
Email: hassanniab.h@gmail.com
ORCID: 0009-0009-8556-3366