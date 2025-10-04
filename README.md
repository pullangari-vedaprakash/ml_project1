# Student Performance Prediction

## Overview

This project is an end-to-end machine learning application designed to predict student performance (test scores) based on various demographic and academic factors. The model analyzes how variables such as gender, ethnicity, parental level of education, lunch type, and test preparation courses impact students' math, reading, and writing scores.

Key highlights:
- **Exploratory Data Analysis (EDA)**: Performed in Jupyter Notebook to uncover insights like linear relationships between scores and the influence of factors like lunch and parental education.
- **ML Pipeline**: Includes data ingestion, preprocessing, model training, hyperparameter tuning, and evaluation using multiple regression models.
- **Models Evaluated**: Linear Regression, Lasso, Ridge, K-Neighbors Regressor, Decision Tree, Random Forest, XGBRegressor, CatBoost, and AdaBoost (with GridSearchCV for optimization).
- **Deployment**: Hosted on AWS Elastic Beanstalk as a web app using Flask for real-time predictions.
- **Tech Stack**: Python, Pandas, NumPy, Scikit-learn, CatBoost, XGBoost, Flask, AWS Elastic Beanstalk.

The project follows best practices for ML workflows, including exception handling, logging, and modular code structure.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [EDA Insights](#eda-insights)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## Features

- **Predictive Modeling**: Predicts student scores using ensemble and boosting algorithms for high accuracy.
- **Hyperparameter Tuning**: Uses GridSearchCV to find optimal parameters for each model.
- **Web Interface**: A simple Flask-based web app for inputting student details and getting predictions.
- **Modular Pipeline**: Custom utilities for saving/loading models, evaluating performance, and handling exceptions.
- **Visualization**: Pairplots and other Seaborn/Matplotlib visuals in EDA to highlight data relationships.
- **Deployment Ready**: Configured for AWS Elastic Beanstalk with `application.py` and `requirements.txt`.

## Dataset

The dataset (`stud.csv`) contains 1000 records with the following features:
- **gender**: Male/Female
- **race_ethnicity**: Group A/B/C/D/E
- **parental_level_of_education**: Education level (e.g., bachelor's, master's)
- **lunch**: Standard/Free-Reduced
- **test_preparation_course**: None/Completed
- **math_score, reading_score, writing_score**: Target variables (scores out of 100)

Source: Synthetic dataset inspired by real-world student performance studies (e.g., from Kaggle).

Key Insights from Data:
- Shape: (1000, 8)
- No missing values or duplicates.
- Scores are normally distributed with some outliers.

## Installation

1. Clone the repository:
2. Create a virtual environment (optional but recommended):
3. Install dependencies:


## Usage

### Local Development

1. Run EDA Notebook:
- Open `notebook/1. EDA STUDENT PERFORMANCE .ipynb` in Jupyter.
- Execute cells to perform data analysis and visualize insights.

2. Train Models:
- Run the training pipeline:
- This will preprocess data, evaluate models, and save the best one in `artifacts/`.

3. Run the Flask App Locally:
- Open `http://127.0.0.1:5000/` in your browser.
- Input student details via the form to get score predictions.

### Prediction Example

Input:
- Gender: Female
- Race/Ethnicity: Group B
- Parental Education: Bachelor's Degree
- Lunch: Standard
- Test Preparation: None

Output: Predicted scores for Math, Reading, and Writing.


## EDA Insights

From the notebook:
- Scores increase linearly with each other (e.g., high math scores correlate with high reading/writing).
- Females outperform males in pass percentage and top scores.
- Factors like standard lunch and higher parental education positively impact performance.
- Test preparation course completion is beneficial but not strongly correlated.
- Visualizations: Pairplots colored by gender show clear trends.

For full details, refer to the notebook.

## Model Training and Evaluation

- **Preprocessing**: One-hot encoding for categoricals, scaling for numerics.
- **Models**: Evaluated using R² score on train/test split.
- **Best Model**: CatBoost or XGBoost (based on hyperparameter tuning; achieves ~90% R²).
- **Evaluation**: Custom function in `utils.py` uses GridSearchCV and reports test scores.

## Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/YourFeature`).
3. Commit changes (`git commit -m 'Add YourFeature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a Pull Request.
