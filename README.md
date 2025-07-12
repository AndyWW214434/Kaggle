# 🏋️‍♂️ Playground Calories Competition

This repository contains my solution for the **Playground Series - Season 5, Episode 5** hosted on Kaggle. The task involves predicting **Calories burned** based on biometric and activity data.

---

## 📁 Dataset

- **Source**: Kaggle [Playground S5E5](https://www.kaggle.com/competitions/playground-series-s5e5/)
- **Files**:
  - `train.csv`: Training data with target variable `Calories`
  - `test.csv`: Test set without labels
  - `sample_submission.csv`: Required submission format

---

## 🧹 Data Preprocessing

- **Categorical Encoding**: Converted `Sex` to binary (0 = Female, 1 = Male)
- **Dropped**: `id` column (not useful for modeling)
- **Duplicates**: Retained, assuming each row represents a distinct activity session
- **Missing Values**: None found in the dataset

---

## 🏗️ Feature Engineering

Engineered new features to improve model performance:

| Feature Name     | Description                                 |
|------------------|---------------------------------------------|
| `BMI`            | `Weight / (Height²)`                        |
| `HR_Duration`    | `Heart_Rate × Duration`                     |
| `Temp_Duration`  | `Body_Temp × Duration`                      |
| `Age_Group`      | Age binned into discrete groups             |
| `Heart_Rate_z`   | Z-score normalized Heart Rate (by age group)|
| `Body_Temp_z`    | Z-score normalized Body Temp (by age group) |
| `Effort`         | `Weight × Duration`                         |
| `temp_diff`      | `Body_Temp − 37°C`                          |

---

## ⚙️ Modeling – PyTorch MLP

Built a **3-layer Multilayer Perceptron (MLP)** using PyTorch:

- **Architecture**: Dense layers with ReLU activations
- **Loss Function**: Mean Squared Error (MSE)
- **Optimizer**: Adam (learning rate = 1e-3)
- **Training Strategy**: Early stopping with patience = 5 epochs

---

## 📊 Training Strategy

- **Train/Validation Split**: 80% / 20%
- **Scaling**: StandardScaler applied to features and target
- **Outcome**: Achieved stable validation loss with early stopping

---

## 🧪 Prediction & Submission

- Applied same transformations to `test.csv`
- Predictions inverse-transformed to match original calorie scale
- Output saved as: `submission2.csv`

**Submission Format:**

```csv
id,Calories
0,218.12
1,178.63
...
