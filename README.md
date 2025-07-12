# Kaggle

**📁 Dataset**  
Data provided by the Kaggle competition Playground Series - Season 5, Episode 5:

train.csv – training data with target column Calories

test.csv – test data to predict on

sample_submission.csv – submission format

**🧹 Data Preprocessing**  
Categorical encoding: Converted Sex to binary (0 = female, 1 = male).

Removed the id column for modeling.

Duplicate records were retained because they likely represent different individuals with similar measurements.

No missing values were present.

**🏗️ Feature Engineering**  
New features added to enhance model learning:

BMI = Weight / (Height²)

HR_Duration = Heart Rate × Duration

Temp_Duration = Body Temp × Duration

Age_Group = Binned age groups

Z-score normalization (_z) of Heart_Rate and Body_Temp within each age group

Effort = Weight × Duration

temp_diff = Body Temperature − 37°C

**⚙️ Modeling – PyTorch MLP**  
A 3-layer Multilayer Perceptron (MLP) with ReLU activations.

Loss function: Mean Squared Error (MSE)

Optimizer: Adam with learning rate 1e-3

Early stopping is used to avoid overfitting, with a patience of 5 epochs.

**📊 Training**  
Data split: 80% training, 20% validation

Features and targets were standardized using StandardScaler.

The model achieved stable validation loss with early stopping triggered.

**🧪 Prediction**  
Test data was processed with the same transformations as training data.

Predictions were inverse-transformed to return to the original Calories scale.

Results were saved as submission2.csv.

**📤 Submission Format**  
csv
Copy
Edit
id,prediction
0,27.604
1,108.437
...
**✅ Dependencies**  
numpy, pandas, seaborn, matplotlib

scikit-learn

torch, torchvision
