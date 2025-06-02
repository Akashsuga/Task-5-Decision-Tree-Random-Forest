# Task 5 - Decision Trees & Random Forests (Heart Disease Dataset)

##  Objective

To explore and implement tree-based classification models — **Decision Trees** and **Random Forests** — and extract useful patterns from medical data to predict heart disease.

---

## Project Contents
- **heart.csv** — Original dataset
- **task5_tree_based_models.py** — Python script for Decision tree and Random Forest
- **Visual Images** — Folder containing all visualizations
- **README.md** — This documentation

---

##  Dataset

- **File**: `heart.csv`
- **Source**: [Kaggle - Heart Disease Dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset)
- **Target Variable**: `target`
  - `0` = No Heart Disease  
  - `1` = Has Heart Disease

---

##  Tools & Libraries

- Python 
- `pandas`, `matplotlib`, `seaborn`
- `scikit-learn` (DecisionTree, RandomForest, metrics)

---

##  Exploratory Data Analysis (EDA)

###  Correlation Heatmap
![Correlation Heatmap](https://github.com/user-attachments/assets/2a8c0dc3-cd04-4195-b039-3c39c1412218)

Helps visualize how features are correlated with each other and the target variable.
> High positive correlation seen in `cp`, `thalach` and negative correlation in `exang`, `oldpeak`.

###  Target Class Distribution
![Target Class Disribution](https://github.com/user-attachments/assets/7afa83ff-c167-4131-b589-55d036899d3e)

Bar chart showing class balance.
> Dataset is reasonably balanced — no major class imbalance.

###  Pairplot of Top 3 Features
![Pair Plot -Imporant features](https://github.com/user-attachments/assets/9eba3720-6879-413b-8222-c35be69c7567)

Visual representation of how the 3 most important features vary across classes.

---

##  Modeling Steps

###  1. Decision Tree Classifier
![Decision Tree](https://github.com/user-attachments/assets/19f4512b-c286-4661-9bf2-a3e287075296)

- Trained using `sklearn.tree.DecisionTreeClassifier`
- Visualized using `plot_tree()`
- Accuracy and classification report printed

###  2. Controlled Tree Depth (Pruning)
- Used `max_depth=4` to reduce overfitting
- Slight accuracy improvement observed

###  3. Random Forest Classifier
![download](https://github.com/user-attachments/assets/fde92f3c-4f61-412d-9c1a-ac1fa3a118e1)

- Used `RandomForestClassifier(n_estimators=100)`
- Outperformed single Decision Tree
- Used for feature importance analysis

###  4. Cross-validation
- 5-fold cross-validation performed on both models for stability check

---

##  Model Results

| Model                  | Test Accuracy | CV Accuracy (5-fold) |
|-----------------------|---------------|----------------------|
| Decision Tree          | ~78%          | ~77%                 |
| Pruned Decision Tree   | ~80%          | ~78%                 |
| Random Forest          | ~85%          | ~84%                 |

---

##  Feature Importance (Random Forest)

| Feature    | Description                           | Importance |
|------------|---------------------------------------|------------|
| `cp`       | Chest pain type                       | High       |
| `thalach`  | Max heart rate achieved               | High       |
| `exang`    | Exercise-induced angina               | High       |
| `oldpeak`  | ST depression                         | Moderate   |
| `fbs`      | Fasting blood sugar > 120 mg/dl       | Low        |

---

##  Insights, Patterns & Anomalies

###  Patterns
- **Chest pain type (`cp`)** is the strongest indicator of heart disease.
- **High heart rate (`thalach`)** usually correlates with no heart disease.
- **Exercise-induced angina (`exang`)** is common in those with heart disease.

###  Anomalies
- Some patients with **high cholesterol** had no heart disease — indicates it’s not a stand-alone predictor.
- **`fbs` (fasting blood sugar)** had minimal influence — potential candidate for feature drop.

---

## Concepts Practiced

- Decision Trees (Entropy, Information Gain)
- Random Forests (Bagging, Ensemble Learning)
- Overfitting & Tree Depth Control
- Feature Importance
- Cross-validation

---
# Conclusion

We applied Decision Tree and Random Forest models to predict heart disease using medical data. EDA revealed key predictors like chest pain type and heart rate. While Decision Trees offered interpretability, Random Forests delivered better accuracy and generalization. Overall, this task strengthened our understanding of classification, feature importance, and model evaluation in real-world scenarios
