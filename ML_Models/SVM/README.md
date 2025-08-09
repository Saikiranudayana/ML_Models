# Support Vector Machines — Classifier, Regressor & Kernels

## 1. Support Vector Classifier (SVC) 🚀🚀🚀

### About

The **Support Vector Classifier** is a supervised learning algorithm that separates classes by finding the **optimal hyperplane** with the largest margin between them.
It works well for both **linear and non-linear classification** by using **kernel functions** to transform the feature space when needed.

### How It Works ⚙️⚙️⚙️

* Finds a hyperplane that **maximizes the margin** between different classes.
* If data is not perfectly separable, allows soft margins by introducing **slack variables**.
* Uses the **kernel trick** to project non-linear data into a higher-dimensional space where it can be linearly separated.

### Mathematical Intuition 📐📐📐

Given training data $(x_i, y_i)$ where $y_i \in \{-1, +1\}$:

**Hard Margin Optimization**:

$$
\min_{w,b} \ \frac{1}{2} \|w\|^2
$$

subject to:

$$
y_i (w^T x_i + b) \geq 1
$$

**Soft Margin Optimization** (non-separable data):

$$
\min_{w,b,\xi} \ \frac{1}{2} \|w\|^2 + C \sum_{i=1}^m \xi_i
$$

subject to:

$$
y_i (w^T x_i + b) \geq 1 - \xi_i
$$

Prediction:

$$
\hat{y} = \text{sign}(w^T x + b)
$$

### Advantages ✅✅✅

* Works well in high dimensions.
* Handles both linear & non-linear data.
* Strong generalization due to margin maximization.

### Limitations ⚠️⚠️⚠️

* Slow for large datasets.
* Requires careful parameter tuning.
* Sensitive to noisy data.

### Applications 💡💡💡

* Text classification (spam filtering)
* Image recognition
* Bioinformatics
* Fraud detection

---

## 2. Support Vector Regressor (SVR) 📊📊📊

### About

**Support Vector Regression** is an adaptation of SVM for regression tasks.
Instead of finding a hyperplane to separate classes, SVR finds a function that deviates from the actual targets by at most $\epsilon$, while being as flat as possible.

### How It Works ⚙️⚙️⚙️

* Fits a regression line (or curve) within an **epsilon-insensitive margin**.
* Points lying inside the margin are ignored (no penalty).
* Points outside the margin incur a penalty proportional to the distance from the margin.

### Mathematical Intuition 📐📐📐

Given training data $(x_i, y_i)$:

Optimization:

Minimize: (1/2) ||w||² + C * Σ (ξᵢ + ξᵢ*)

subject to:

$$
y_i - (w^T x_i + b) \leq \epsilon + \xi_i
$$

$$
(w^T x_i + b) - y_i \leq \epsilon + \xi_i^*
$$

$\xi_i, \xi_i^* \geq 0$

Prediction:

$$
\hat{y} = w^T x + b
$$

### Advantages ✅✅✅

* Controls model complexity via $\epsilon$.
* Works well for high-dimensional regression problems.
* Robust to outliers within $\epsilon$ margin.

### Limitations ⚠️⚠️⚠️

* Parameter tuning (C, $\epsilon$, kernel) is crucial.
* Computationally heavy for very large datasets.

### Applications 💡💡💡

* Time-series forecasting
* Financial predictions
* Demand forecasting
* Environmental modeling

---

## 3. SVM Kernels 🔄🔄🔄

### About

Kernels allow SVM to work in **non-linear spaces** by mapping data into a higher-dimensional feature space without explicitly computing the transformation — known as the **kernel trick**.

### Common Kernel Functions ⚙️⚙️⚙️

* **Linear Kernel**:
  $K(x, x') = x^T x'$
  Best for linearly separable data.

* **Polynomial Kernel**:
  $K(x, x') = (x^T x' + c)^d$
  Captures polynomial relationships.

* **Radial Basis Function (RBF) Kernel**:
  $K(x, x') = \exp(-\gamma \|x - x'\|^2)$
  Very popular; works well for non-linear boundaries.

* **Sigmoid Kernel**:
  $K(x, x') = \tanh(\kappa x^T x' + c)$
  Similar to neural networks’ activation.

### Advantages ✅✅✅

* Enables modeling complex relationships.
* Avoids explicit computation in high-dimensional spaces.

### Limitations ⚠️⚠️⚠️

* Wrong kernel choice can hurt performance.
* More parameters to tune.

### Applications 💡💡💡

* Non-linear classification
* Complex regression
* Pattern recognition

---


# 🖥️ Support Vector Machines (SVM) Examples

This directory contains three example notebooks demonstrating the use of Support Vector Machines for both classification and regression tasks, as well as kernel-based transformations.

## 1️⃣ Support Vector Classifier (SVC) Example

📄 [Notebook Link](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/SVM/Support_Vector_Classifier_Example.ipynb)

This notebook demonstrates:

* 🧪 Creating and splitting a synthetic dataset for binary classification.
* ⚙️ Implementing SVM classification with different kernels:

  * 📏 Linear
  * 🌐 RBF (Radial Basis Function)
  * 🔢 Polynomial
  * ➖ Sigmoid
* 📊 Comparing classification performance metrics (precision, recall, f1-score, confusion matrix).
* 🔍 Performing hyperparameter tuning using `GridSearchCV` to improve model performance.

## 2️⃣ Support Vector Regressor (SVR) Example

📄 [Notebook Link](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/SVM/Support_Vector_Regressor_Example.ipynb)

This notebook demonstrates:

* 📊 Using the `tips` dataset for regression tasks.
* 🛠️ Preprocessing categorical data using label encoding and one-hot encoding.
* 📈 Implementing Support Vector Regression with default parameters.
* 🧮 Evaluating model performance using R² score and Mean Absolute Error (MAE).
* 🔍 Performing hyperparameter tuning using `GridSearchCV` to optimize SVR parameters.

## 3️⃣ Support Vector Classifier with Kernel Features Example

📄 [Notebook Link](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/SVM/Support_Vector_Classifier_Kernel_Example.ipynb)

This notebook demonstrates:

* 🎯 Creating two concentric circular datasets to illustrate non-linear separability.
* 🧩 Engineering polynomial features manually (`X1²`, `X2²`, `X1*X2`) for kernel-based classification.
* ⚙️ Applying SVC with different kernels (linear, polynomial, RBF, sigmoid).
* ✅ Showing perfect classification accuracy after kernel transformation.

## 📚 Key Learnings

* 💪 SVM is a powerful technique for both classification and regression.
* 🔑 Kernel functions help in handling non-linear data by mapping it to higher-dimensional spaces.
* 🎯 Hyperparameter tuning (e.g., `C`, `gamma`, `kernel`) is crucial for improving model performance.
* 🧼 Proper preprocessing of data is essential for optimal results, especially with categorical features in SVR.

---
