# Shooting-Incident-Classification
An analysis of factors in U.S. shooting incidents to build a model that classifies fatality outcomes. This project demonstrates a full data science workflow, from EDA with Power BI to advanced techniques like SMOTE for handling imbalanced data.

# 🎯 Shooting Incident Fatality Classification

![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg?logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-0.24%2B-orange?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Pandas-1.3%2B-150458?logo=pandas)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?logo=powerbi&logoColor=black)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

---

## 📋 Project Overview

This project uses machine learning to classify the outcome of shooting incidents as either **fatal** or **non-fatal**. By analyzing a dataset of incidents, this work aims to build a predictive model that can identify key factors contributing to fatalities. The project demonstrates a complete data science workflow, from data cleaning and exploratory analysis to handling imbalanced data and comparing multiple classification models.

## 📊 The Dataset

The analysis is based on the `shootings.csv` dataset, which includes various attributes for each incident:
-   **Demographics:** `age`, `gender`, `race`
-   **Situational Factors:** `armed`, `threat_level`, `flee` status
-   **Procedural Details:** `body_camera` presence
-   **Outcome:** `manner_of_death` (used to engineer the binary `fatality` target variable)

### Key Challenge: Severe Class Imbalance

A critical aspect of this dataset is its severe class imbalance. **94.6%** of the incidents resulted in a fatality, while only **5.4%** were non-fatal. This imbalance poses a significant challenge, as a naive model could achieve high accuracy simply by always predicting "fatal." To build a meaningful classifier, this issue was addressed using the **SMOTE (Synthetic Minority Over-sampling Technique)** on the training data.

![Class Distribution Chart](https://i.imgur.com/Kz8jHnE.png) ## 🛠️ Methodology

The project was executed through a systematic pipeline:

1.  **Data Cleaning & Preprocessing:**
    -   Handled missing values in `armed`, `age`, `gender`, `race`, and `flee` by imputing with the mean or mode.
    -   Engineered time-based features (`year`, `month`, `day`) from the `date` column.
    -   Created the binary target variable `fatality` by mapping `shot` and `shot and Tasered` to 1 (fatal).

2.  **Exploratory Data Analysis (EDA):**
    -   Utilized **Power BI** for interactive dashboarding to explore trends and patterns visually.
    -   Used Python libraries (Matplotlib, Seaborn) to plot distributions of key features like age, race, and threat level.

3.  **Feature Engineering & Scaling:**
    -   Converted categorical features to a numerical format using both **One-Hot Encoding** and **Label Encoding**.
    -   Scaled all numerical features using `StandardScaler` to ensure models were not biased by feature magnitudes.

4.  **Modeling & Evaluation:**
    -   Trained and compared three different classification models:
        -   Logistic Regression
        -   K-Nearest Neighbors (KNN)
        -   **Random Forest Classifier**
    -   Evaluated models using Accuracy, Precision, Recall, and F1-Score, focusing on performance for the minority (non-fatal) class.

## 🏆 Results: Random Forest as the Top Performer

After addressing the class imbalance with SMOTE, the **Random Forest Classifier** emerged as the best-performing model. It achieved an outstanding **accuracy of 98%** on the test set and demonstrated a strong ability to correctly identify both fatal and non-fatal incidents, as shown by its balanced precision and recall scores.

**Confusion Matrix for Random Forest Model:**

*(You should add a screenshot of your Random Forest confusion matrix here to visually support the results)*

| Model                     | Accuracy | Recall (Class 0) | Precision (Class 0) | F1-Score (Class 0) |
| ------------------------- | :------: | :--------------: | :-----------------: | :----------------: |
| Logistic Regression       |  74.0%   |       0.79       |        0.18         |       0.29         |
| K-Nearest Neighbors (KNN) |  94.0%   |       0.84       |        0.47         |       0.60         |
| **Random Forest** | **98.0%**|     **0.84** |      **0.77** |     **0.80** |

## 📊 Power BI Dashboard

An interactive dashboard was created in Power BI to provide a high-level overview of the dataset. It allows for dynamic exploration of trends across different states, races, and threat levels. The `.pbix` file is available in the `/dashboard` directory.

*(Add a screenshot of your Power BI dashboard from the presentation here)*

## 🚀 How to Run this Project

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/PushpakShrimal/Shooting-Incident-Classification.git](https://github.com/PushpakShrimal/Shooting-Incident-Classification.git)
    cd Shooting-Incident-Classification
    ```
2.  **Create and activate a virtual environment:**
    ```bash
    python -m venv env
    source env/bin/activate  # On Windows: env\Scripts\activate
    ```
3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Run the Jupyter Notebook:**
    ```bash
    jupyter notebook notebooks/Project_4_(Classifying_Shooting_Incident_Fatality)_.ipynb
    ```
5.  **View the Dashboard:**
    -   Open the `dashboard/` folder and launch the `.pbix` file using Power BI Desktop.

---
