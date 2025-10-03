# TensorFlow-Diabetes-Regressor

---

## 🎯 Project Overview: Deep Learning Regression on Diabetes Progression

This project explores the use of a **Deep Neural Network (DNN)** built with **TensorFlow/Keras** to predict the quantitative progression of diabetes in patients one year after baseline measurements. The goal is to develop a robust regression model to estimate a continuous health metric.

### 📊 Dataset

* **Source:** Scikit-learn's built-in Diabetes dataset.
* **Problem Type:** Regression.
* **Target:** A continuous measure of disease progression, ranging from approximately 25 to 346.
* **Features:** 10 baseline medical features (Age, BMI, Blood Pressure, and six blood serum measurements) which are pre-scaled.

---

## 🧪 Initial Model Architecture (Underfitting Diagnostic)

The initial model was a basic DNN implemented to establish a baseline performance:

* **Layers:** 2 Dense Hidden Layers (64, 32 neurons) + 1 Output Layer (1 neuron).
* **Optimizer:** Adam (`learning_rate=0.001`).
* **Loss Function:** Mean Squared Error (MSE).
* **Regularization:** Used Keras `EarlyStopping` on validation loss.

### Initial Performance Metrics (Test Set)

| Metric | Result | Interpretation |
| :--- | :--- | :--- |
| $\mathbf{R^2}$ | $\mathbf{0.3338}$ | The model explains only **33.38%** of the target variance, indicating a **poor fit**. |
| **RMSE** | $\mathbf{59.4111}$ | High root mean squared error, suggesting significant average deviation from the true progression value. |
| **MAE** | $\mathbf{49.2895}$ | The average absolute error is nearly 50 units, which is unacceptable for a medical prediction task. |

---

## 🚀 Next Steps: Addressing Underfitting in TensorFlow

The initial results confirm the model exhibits **high bias (underfitting)**. The simple network failed to capture the complex, non-linear relationships. The following steps are critical for achieving an industrially viable $\mathbf{R^2}$ score:

1.  **Increase Network Capacity:** The model is structurally too simple. I will **add more hidden layers** (e.g., a $\text{128-64-32}$ structure) and/or use **$\text{Dropout}$** for better generalization.
2.  **Feature Engineering:** Explore generating **non-linear interaction terms** (e.g., $\text{BMI} \times \text{Age}$) to boost the model's explanatory power, since the pre-scaled features are limited.
3.  **Hyperparameter Tuning:** Conduct a systematic search (e.g., $\text{Grid Search}$ or $\text{Bayesian Optimization}$) to find optimal values for the **learning rate**, **batch size**, and $\text{L2/L1}$ regularization to balance bias and variance.
