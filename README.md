# GasConcentration-Prediction-ML

This project focuses on predicting the concentration of nitrogen monoxide (NO) and ammonia (NH₃) using electrochemical gas sensor data and machine learning models. The goal is to accurately estimate gas concentrations from sensor readings, particularly current values, using regression techniques.

---

## 📊 Problem Statement

Given a dataset containing:
- **Time (s)**
- **Sensor Current (nA)**
- **NH₃ Concentration (ppb)**

The objective is to predict the **NO Concentration (ppb)** accurately.

---

## 🧠 Models Used

- **Linear Regression**
- **Polynomial Regression**
- **Random Forest Regressor (best performance)**
- **Gradient Boosting Regressor**
- **XGBoost Regressor**
- **Support Vector Regressor (SVR)**

Each model was trained and evaluated using metrics like:

- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- R² Score

---

## ⚙️ Data Preprocessing

- Standardization using `StandardScaler`
- Splitting into `X_train`, `X_test`, `y_train`, `y_test`
- Scaling and reshaping for pipeline input
- Creating pipelines with preprocessing + model

---

## 🔍 Model Evaluation

| Model           | MAE   | RMSE  | R² Score |
|----------------|-------|-------|----------|
| Random Forest  | 0.017 | 0.751 | **0.999** |
| XGBoost        | 3.886 | 9.83  | 0.906     |
| SVR            | 3.848 | 12.92 | 0.838     |
| GradientBoost  | 3.922 | 9.72  | 0.908     |

✅ The **Random Forest Regressor** with GridSearchCV was selected as the final model.

---

## 📈 Visualizations

- Scatter plots of predicted vs actual values
- Time vs Current trends
- NO concentration trends
- Residual plots for error distribution

---

## 🧪 Predicting New Samples

The model can take new sensor inputs (Time, Current, NH₃) and predict NO concentration using the built pipeline:

```python
# Example input
input_data = pd.DataFrame([[639, 42.0, 10]], columns=['Time(s)', 'Current(nA)', 'NH3(ppb)'])

# Predict
predicted_no = pipeline.predict(input_data)

