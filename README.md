# Student Placement Prediction System 🎓

This project is a Machine Learning-powered Web Application built using **Django** and **Scikit-learn**. It predicts whether a student will get placed based on their academic records, work experience, and specialisation.

---

## 🧠 Model Training & Performance (Jupyter Notebook Analysis)

The model training was performed in `models.ipynb`. Below is the performance analysis of all tested algorithms:

### 1. Model Accuracy Comparison
During the training phase, multiple models were evaluated on the test dataset.

| Algorithm | Accuracy Score | Status |
| :--- | :--- | :--- |
| **Logistic Regression** | **0.86 (86%)** | Very Strong Base |
| **K-Nearest Neighbors (KNN)** | 0.84 (84%) | Good Performance |
| **Support Vector Machine (SVM)** | 0.84 (84%) | Stable |
| **Decision Tree** | 0.84 (84%) | Prone to Overfitting |
| **Gaussian Naive Bayes** | 0.84 (84%) | Simple but Effective |
| **XGBoost Classifier** | 0.84 (84%) | Reliable |

### 2. Cross-Validation Results
To ensure the models are not just "memorizing" data (overfitting), 5-fold cross-validation was performed:
- **SVM:** ~86.04% (Most Stable)
- **Logistic Regression:** ~85.58%
- **KNN:** ~82.32%

### 3. Final Selection: Stacking Classifier 🏆
The **Best Fit** model selected for the final web application is a **Stacking Classifier**. 
- **Base Learners:** Logistic Regression, SVM, and KNN.
- **Final Estimator:** Logistic Regression.
- **Final Accuracy:** **88.37%**

This Stacking approach was chosen because it combines the strengths of multiple models to reduce errors and provide the most reliable placement predictions.

---

## 🛠️ Technology Stack
- **Web Framework:** Django (Python)
- **Machine Learning Library:** Scikit-Learn
- **Model Storage:** Joblib
- **Exploratory Data Analysis:** Pandas, Seaborn, Matplotlib

---

## 📊 Dataset Features (Inputs)
The model processes the following **12 inputs** to make a prediction:

| Feature | Key Factors for "Not Placed" | Value for Negative Prediction |
| :--- | :--- | :--- |
| **Academic Scores** | Low % in SSC, HSC, Degree, MBA | Set below 55.0% |
| **Work Experience** | Lack of industry exposure | Set to `0` (No) |
| **Specialisation** | Mkt & HR vs Mkt & Fin | Set to `1` (Mkt&HR) |
| **E-test Score** | Low employability score | Set below 60.0% |

---

## 📂 Internal Project Structure
- `Model_Ml/model/views.py`: Contains the logic to load the model and perform **Manual Scaling** (Mean/Std) to match the training data.
- `Model_Ml/final_model/model.joblib`: The trained 88.37% accuracy model.
- `model_created/models.ipynb`: Full training pipeline and visualization.
- `model_created/Placement_Data_Full_Class.xls`: Raw dataset.

---

## ⚙️ How to Use
1. **Browse to:** `http://127.0.0.1:8000/`
2. **Input Data:** Fill in the 12 fields.
3. **Analyze:** If results show "Not Placed", try improving the academic scores or adding work experience in the input fields to see how the prediction changes.

---

## 📝 Scaling Note
Since the model was trained using `StandardScaler` in the notebook, the web application converts your raw input scores into normalized Z-scores using the dataset's Mean and Standard Deviation before making the final prediction.
