# student-performance-prediction
A Machine Learning project that predicts students' final mathematics grades using Python and compares Linear Regression, Decision Tree, and Random Forest models.
# Student Performance Prediction using Machine Learning

## Project Overview

This project uses Machine Learning to predict students' final mathematics grades based on their academic, personal, and social information.

The main objective is to understand which factors are associated with student performance and compare different machine learning models.

## Dataset

- **Dataset:** UCI Student Performance Dataset
- **File:** `student-mat.csv`
- **Total records:** 395 students
- **Total columns:** 33
- **Target variable:** `G3` (final mathematics grade, 0–20)

## Technologies Used

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Joblib

## Project Workflow

1. **Data Collection:** Loaded the student mathematics dataset.
2. **Data Cleaning:** Checked missing values and dataset structure.
3. **Exploratory Data Analysis:** Studied grade distributions, feature relationships, and correlations.
4. **Data Preprocessing:**
   - Handled missing values using SimpleImputer.
   - Scaled numerical features using StandardScaler.
   - Converted categorical features using OneHotEncoder.
5. **Model Training:** Trained Linear Regression, Decision Tree, and Random Forest models.
6. **Model Evaluation:** Evaluated models using MAE, MSE, RMSE, and R².
7. **Cross-Validation:** Used 5-fold cross-validation to check model consistency.
8. **Feature Importance:** Identified influential features using Random Forest.

## Models Compared

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Linear Regression | 1.647 | 2.378 | 0.724 |
| Decision Tree | 1.316 | 2.571 | 0.678 |
| Random Forest | **1.201** | **2.015** | **0.802** |

Random Forest performed best among the three models on the test set.

## Two Prediction Experiments

To understand the importance of previous examination grades, two experiments were performed.

| Metric | With G1 & G2 | Without G1 & G2 |
|---|---:|---:|
| MAE | 1.201 | 2.994 |
| RMSE | 2.015 | 3.751 |
| R² Score | 0.802 | 0.314 |
| 5-Fold CV MAE | 0.921 | 2.907 |

**Observation:** The model using G1 and G2 performed considerably better. This indicates that previous examination grades are strong predictors of final grades.

## Feature Importance

The Random Forest model identified the following influential features:

1. G2 – Previous second-period grade
2. Absences – Number of student absences
3. Reason – Home-related school choice reason
4. Age
5. G1 – Previous first-period grade

G2 was the most influential feature in the fitted model.

## Evaluation Metrics

- **MAE:** Measures the average absolute prediction error.
- **MSE:** Measures the average squared prediction error.
- **RMSE:** Measures prediction error on the original grade scale.
- **R² Score:** Measures how much variation in the target variable is explained by the model.

## Saved Models

The trained models were saved using Joblib:

- `student_performance_model.pkl`
- `student_performance_model_without_grades.pkl`

Example of loading the best model:

```python
import joblib

model = joblib.load("student_performance_model.pkl")

predictions = model.predict(new_student_data)
```

## Conclusion

This project helped me understand the complete Machine Learning workflow, from data analysis and preprocessing to model training and evaluation.

Random Forest achieved the best test-set performance, with an R² score of approximately 0.80 when previous examination grades were included.

The experiments also demonstrated how feature selection can significantly affect model performance.

## Limitations

- The dataset contains only 395 students.
- The data represents students from Portuguese schools.
- The model predicts mathematical performance and may not generalize to other subjects or populations.
- Feature importance indicates predictive relationships, not causation.
- Predictions should not be used as the sole basis for important educational decisions.

## Future Improvements

- Experiment with hyperparameter tuning.
- Try additional machine learning algorithms.
- Build a simple web application using Streamlit.
- Test the model on additional student datasets.

---

**Project Type:** Beginner Machine Learning Project  
**Domain:** Education / Predictive Analytics  
**Language:** Python
