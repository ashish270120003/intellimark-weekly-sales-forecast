# 📊 Intellimark AI - Data Science Forecast Assignment

## 🚀 Overview

This project focuses on analyzing and forecasting weekly sales data for various products using machine learning techniques. The objective is to predict weekly sales quantities for the months of **September, October, and November 2024**, based on historical sales patterns, and evaluate the model's accuracy on **June, July, and August 2024**.

---

## 📁 Project Structure

```bash
├── eda_intellimark.ipynb           # Exploratory Data Analysis notebook
├── forecast_model_intellimark.ipynb # Forecasting and modeling notebook
├── models/
│   └── model_serial_XXX.pkl        # Serialized model files for reproducibility
├── forecasts/
│   └── forecast_results.csv        # Final forecast outputs for Sept–Nov 2024
├── actuals/
│   └── actual_data_jun_aug.csv     # Ground truth data used for validation
├── README.md                       # This documentation
└── requirements.txt                # List of Python dependencies
````

---

## 🔍 1. Exploratory Data Analysis (EDA)

* Inspected dataset structure, types, and missing values.
* Visualized weekly sales over time per product and brand.
* Identified seasonality, trends, anomalies, and any missing intervals.
* Explored product categories, channels, and top-selling items.
* Summary insights helped guide the modeling approach.

---

## 🤖 2. Forecasting & Modeling

* Prepared data at a consistent **weekly interval**, handling missing weeks.
* Split the data:

  * **Training set**: Up to May 2024.
  * **Validation set**: June–August 2024.
* Built forecasting models using techniques such as:

  * `Prophet` for per-series forecasting.
  * `XGBoost` with lag and rolling features.
* Saved models for each `SerialNum` for reproducibility.

---

## 📈 3. Forecasts

* Generated weekly sales forecasts for:

  * **September–November 2024**
* Output format:

  ```csv
  SerialNum,weekend_date,forecasted_quantity
  1234,2024-09-01,345
  1234,2024-09-08,312
  ...
  ```

---

## 📊 4. Validation & Accuracy

* Calculated **Monthly Accuracy** for:

  * **June 2024**
  * **July 2024**
  * **August 2024**

Using:

$$
\text{Accuracy} = 1 - \frac{\sum |\hat{y} - y|}{\sum y}
$$

* Performance was reported per `SerialNum` and aggregated to evaluate robustness.

---

## 💾 Model Artifacts

Models were saved using `joblib` or `pickle`:

```python
import joblib
joblib.dump(model, 'models/model_serial_123.pkl')
```

---

## 📦 Dependencies

Ensure the following libraries are installed. You can install all with:

```bash
pip install -r requirements.txt
```

### `requirements.txt` includes:

```
pandas
numpy
matplotlib
seaborn
scikit-learn
prophet
xgboost
joblib
```

---

## 📌 Notes & Assumptions

* Missing weekly data was handled by resampling with a complete `date_range`.
* Models were built individually per `SerialNum` to account for unique trends.
* No external data (e.g., holidays) was included unless mentioned.
* All models and outputs are reproducible using provided files.```
