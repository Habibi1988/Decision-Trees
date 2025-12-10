# 💊 Decision Tree Classification for Drug Prediction

This project documents the development, training, and evaluation of a Decision Tree Classifier aimed at predicting the appropriate medication for a patient based on key health metrics.

## 🎯 Objectives

* Develop and train a classification model using the **Decision Tree Algorithm**.
* Apply the model to a real-world dataset for drug prediction.
* Analyze the impact of the `max_depth` hyperparameter on model performance.

---

## 💾 Data Analysis and Pre-processing

The dataset contains 200 records from patients who responded to one of five drugs: Drug A, B, C, X, or Y.

### Features

| Feature | Data Type | Notes |
| :--- | :--- | :--- |
| `Age` | `int64` | Patient's age. |
| `Sex` | `object` | Patient's gender. |
| `BP` | `object` | Blood Pressure (High, Low, Normal). |
| `Cholesterol`| `object` | Cholesterol level (High, Normal). |
| `Na_to_K` | `float64` | Sodium to Potassium ratio. |
| `Drug` | `object` | **Target Variable**. |

### 🔍 Label Encoding

Categorical features were converted to numerical representations using `LabelEncoder`:

* **Sex:** `F` $\rightarrow 0$, `M` $\rightarrow 1$
* **BP:** `High` $\rightarrow 0$, `Low` $\rightarrow 1$, `Normal` $\rightarrow 2$
* **Cholesterol:** `High` $\rightarrow 0$, `Normal` $\rightarrow 1$

### Correlation Analysis

By mapping the target variable (`Drug`) to a numerical equivalent (`Drug_num`), we found the correlation of input features with the drug recommendation:

| Feature | Correlation with `Drug_num` | Significance |
| :--- | :--- | :--- |
| **Na\_to\_K** | **0.589120** | **Most Significant** |
| BP | 0.372868 | Highly Significant |
| Cholesterol | 0.055629 | Low |
| Sex | -0.098573 | Low |
| Age | -0.004828 | Negligible |

### Class Distribution

The dataset exhibits class imbalance, with `DrugX` and `DrugY` having the most samples. 

---

## 🌳 Modeling and Evaluation

### Data Splitting

The features (`X`) and target (`y`) were separated and split into training (70%) and testing (30%) sets using `train_test_split` with `random_state=32`.

### 1. Model Configuration 1: $\text{max\_depth} = 4$

| Parameter | Value |
| :--- | :--- |
| Criterion | `entropy` |
| **Max Depth** | **4** |

#### Performance ($\text{max\_depth} = 4$)
