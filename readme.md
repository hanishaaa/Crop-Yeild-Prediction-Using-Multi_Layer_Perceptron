# 🌾 Forecasting Crop Yield Using Machine Learning (MLP)

## 📌 Overview
This project focuses on forecasting crop yield using a **Multilayer Perceptron (MLP)** model trained on environmental, land cover, and agricultural data.

The objective is to predict **future crop yield (t+1)** using features from the current year (t), simulating a real-world agricultural forecasting scenario.

---

## 🚀 Key Highlights
- 📊 Dataset: ~67,000 records, 37 features
- 🌍 Multi-country & multi-crop dataset
- 🤖 Model: MLPRegressor (Neural Network)
- 📈 R² Score: **0.95**
- 📉 MAE: **~1015 kg/ha**
- ⚠️ RMSE: **~3223 kg/ha**

---

## 🧠 Problem Statement
Accurate crop yield prediction is critical for:
- Agricultural planning
- Food security
- Supply chain optimization

This project builds a machine learning model to predict **next-year yield using historical environmental and land data**.

---

## 📂 Dataset Description

The dataset is created by merging multiple sources:

### 🌦 Environmental Data
- Rainfall
- Snowfall
- Soil moisture (4 depths)
- Soil temperature (4 depths)
- Evaporation & transpiration
- Canopy water content

### 🌱 Land Cover Data
- 17 land cover classes (percentage distribution)

### 🌍 Categorical Features
- Country (one-hot encoded)
- Crop type (one-hot encoded)

### ⏳ Temporal Feature
- Year

---

## 🏗️ Data Preprocessing Pipeline

1. Data cleaning and standardization
2. Merging 17 CSV datasets (environment + land + yield)
3. Monthly → yearly aggregation
4. Spatial mapping using latitude & longitude
5. Country-level aggregation
6. Feature scaling using MinMaxScaler
7. Target transformation using log scaling

Final dataset:
- **67,963 rows**
- **37 columns**
- No missing values

---

## 🎯 Target Variable

The model predicts:


Created using:
- Grouping by country & crop
- Applying `.shift(-1)` on yield column

---

## 🤖 Model Architecture

The model is a **Multilayer Perceptron (MLP)**:

- Input Layer: 100–150 features
- Hidden Layer 1: 256 neurons (ReLU)
- Hidden Layer 2: 128 neurons (ReLU)
- Output Layer: 1 neuron (Regression)

---

## ⚙️ Hyperparameters

| Parameter | Value |
|----------|------|
| Hidden Layers | (256, 128) |
| Activation | ReLU |
| Optimizer | Adam |
| Max Iterations | 300 |
| Early Stopping | True |
| Validation Split | 10% |
| Random State | 42 |

---

## 📊 Model Evaluation

| Metric | Value |
|-------|------|
| MAE | 1015.48 |
| RMSE | 3223.85 |
| R² Score | 0.9505 |

### Interpretation:
- High R² indicates strong predictive performance
- RMSE highlights presence of some large errors
- Model generalizes well across countries and crops

---

## 🧪 Evaluation Strategy

Instead of random split:
- Training: **2010–2021**
- Testing: **2022 → predict 2023**

This ensures:
- Realistic forecasting setup
- No future data leakage

---

## 🛡️ Overfitting Prevention

- Early stopping
- Validation split (10%)
- Feature aggregation
- Log transformation of target
- Feature scaling

---

## 📈 Results

The model successfully:
- Captures trends in crop yield
- Generalizes across different countries and crops
- Achieves strong predictive accuracy

---

## 📊 Visualizations

- Actual vs Predicted Yield Scatter Plot
- Country-Crop Comparison Plot

---

## 🛠️ Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib / Seaborn

---


---

## ⚡ How to Run

```bash
# Clone the repository
git clone https://github.com/your-username/crop-yield-forecasting.git

# Navigate to project folder
cd crop-yield-forecasting

# Install dependencies
pip install -r requirements.txt

# Run the model
python ML_291772.ipynb
