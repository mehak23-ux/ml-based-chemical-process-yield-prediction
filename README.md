# 🧪 Chemical Process Yield Prediction

A machine learning project that predicts **chemical process yield (%)** from key operating conditions using **Multiple Linear Regression**.

> **Note:** The dataset used in this project is simulated for demonstration purposes and is **not experimental or industrial plant data**.

---

## 📌 Project Overview

Chemical process yield can depend on several operating conditions such as temperature, pressure, flow rate, concentration, and residence time.

This project demonstrates how **Multiple Linear Regression** can be used to model the relationship between these process variables and the resulting chemical process yield.

The complete workflow includes:

- Dataset generation
- Data exploration
- Data cleaning
- Exploratory visualization
- Train-test splitting
- Multiple Linear Regression
- Model prediction
- Model evaluation
- Regression coefficient interpretation
- Prediction on new process conditions

---

## 🎯 Objective

The objective is to predict **Yield (%)** based on the following process parameters:

| Feature | Unit |
|---|---|
| Temperature | °C |
| Pressure | bar |
| Flow Rate | L/min |
| Concentration | % |
| Residence Time | min |

### Target Variable

**Yield (%)**

---

## 📊 Dataset

The project generates a simulated dataset containing **300 observations**.

The input variables are randomly generated within predefined operating ranges:

| Variable | Range |
|---|---:|
| Temperature | 60–120 °C |
| Pressure | 1–5 bar |
| Flow Rate | 2–10 L/min |
| Concentration | 10–40 % |
| Residence Time | 5–30 min |

Random noise is added to make the dataset more representative of real-world variability.

The generated yield is constrained between **0% and 100%**.

### ⚠️ Important

This dataset is simulated and is intended only to demonstrate a machine-learning workflow. The resulting model should **not** be interpreted as a validated chemical engineering or industrial process model.

---

## 🛠️ Technologies Used

- **Python**
- **NumPy** – numerical computations
- **Pandas** – data manipulation and analysis
- **Matplotlib** – data visualization
- **Scikit-learn** – machine learning and model evaluation
- **Jupyter Notebook**

---

## 🤖 Machine Learning Model

### Multiple Linear Regression

The model assumes a linear relationship between the process variables and yield:

```text
Yield = β₀ + β₁Temperature + β₂Pressure
        + β₃FlowRate + β₄Concentration
        + β₅ResidenceTime + ε
```

The model is trained using **80% of the data** and evaluated on the remaining **20%**.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y,
    test_size=0.20,
    random_state=42
)
```

---

## 🔍 Exploratory Data Analysis

Scatter plots are generated for each process variable against yield:

- Temperature vs Yield
- Pressure vs Yield
- Flow Rate vs Yield
- Concentration vs Yield
- Residence Time vs Yield

These visualizations help examine the relationships between operating conditions and process yield.

---

## 🧹 Data Cleaning

Before training the model, the dataset is checked for:

- Missing values
- Duplicate rows
- Data types
- Statistical properties

```python
df.isnull().sum()
df.duplicated().sum()
df.describe()
```

---

## 📈 Model Evaluation

The model is evaluated using three standard regression metrics:

### Mean Absolute Error — MAE

Measures the average absolute difference between actual and predicted yield.

### Root Mean Squared Error — RMSE

Measures the square root of the average squared prediction error.

### R² Score

Measures how much of the variation in yield is explained by the regression model.

```python
mae = mean_absolute_error(y_test, y_pred)

rmse = np.sqrt(
    mean_squared_error(y_test, y_pred)
)

r2 = r2_score(y_test, y_pred)
```

The notebook also generates an **Actual vs Predicted Yield** plot to visually evaluate model performance.

---

## ⚙️ Feature Coefficient Interpretation

The regression coefficients are used to understand the direction of the relationships captured by the model.

Based on the simulated dataset:

- **Temperature:** Positive coefficient
- **Pressure:** Positive coefficient
- **Flow Rate:** Negative coefficient
- **Concentration:** Positive coefficient
- **Residence Time:** Positive coefficient

These relationships describe the simulated data and **do not establish causation**.

---

## 🔮 Sample Prediction

The trained model can predict yield for new operating conditions.

Example:

```python
new_conditions = pd.DataFrame({
    "Temperature_C": [95],
    "Pressure_bar": [3],
    "Flow_Rate_L_min": [5],
    "Concentration_percent": [25],
    "Residence_Time_min": [18]
})

predicted_yield = model.predict(new_conditions)
```

The model returns an estimated process yield for these operating conditions.

---

## 📁 Project Structure

```text
Chemical-Process-Yield-Prediction/
│
├── Chemical_Process_Yield_Prediction.ipynb
└── README.md
```

---

## 🚀 How to Run

### 1. Clone the repository

```bash
git clone https://github.com/your-username/Chemical-Process-Yield-Prediction.git
```

### 2. Navigate to the project

```bash
cd Chemical-Process-Yield-Prediction
```

### 3. Install dependencies

```bash
pip install numpy pandas matplotlib scikit-learn jupyter
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
Chemical_Process_Yield_Prediction.ipynb
```

Run the cells sequentially.

---

## 📌 Key Takeaways

This project demonstrates a complete beginner-friendly machine-learning workflow for a chemical engineering problem:

**Data Generation → Exploration → Cleaning → Visualization → Train/Test Split → Model Training → Prediction → Evaluation → Interpretation**

It provides an example of how machine learning can be applied to process data to estimate chemical process yield.

---

## ⚠️ Limitations

- The dataset is simulated rather than collected from an actual chemical plant.
- Multiple Linear Regression assumes a linear relationship between variables
