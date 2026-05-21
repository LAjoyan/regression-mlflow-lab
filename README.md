# Regression Model Lab

This repository contains my experiments with regression models in machine learning.

The goal of this project is to practice training different regression models, evaluate their performance, and track experiments using MLflow.

This project uses different types of datasets for regression experiments:

- CSV datasets loaded with Pandas
- Built-in regression datasets from Scikit-learn

## What this repository includes

- CSV datasets
- Data cleaning and preparation
- Regression model training
- Model evaluation
- MLflow experiment tracking
- Comparison between different regression models

## Regression models I may use

- Linear Regression
- Ridge Regression
- Lasso Regression
- Decision Tree Regressor
- Random Forest Regressor
- KNN Regression
- SVM Regression
- Gradient Boosting Regressor

## Tools and libraries

- Python
- Pandas
- NumPy
- Scikit-learn
- MLflow
- Matplotlib / Seaborn


## 📊 Tracking Experiments with MLflow

This project uses MLflow to track and compare different machine learning models (Linear Regression, Ridge, etc.). All experiment data is saved locally to a SQLite database.

### How to view the MLflow Dashboard
To see the model comparisons, metrics, and parameters, run the following command in your terminal:

`uv run mlflow ui --port 5000`

(Note: If the server instantly crashes on Windows, you may need to limit the workers by running:

`uv run mlflow ui --port 5000 --workers 1)`

Once the server starts, open your web browser and go to: `http://127.0.0.1:5000`

### What you can do in the MLflow UI:

- View Run History: See a leaderboard of every model you have trained.
- Compare Models: Check the boxes next to multiple runs and click Compare to automatically generate scatter plots and see which model had the best `test_R2_Score`.
- Inspect Parameters: View the exact "under the hood" settings (hyperparameters) used for each algorithm to ensure 100% reproducibility.
- Download Artifacts: Click on any run to access the `Artifacts` folder, where you can download the actual trained `model.pkl` file and its required environment variables.

### 🛑 Important Git Note

If you clone this repository, you will generate your own local tracking data. The following tracking files are included in the `.gitignore` so they are not accidentally pushed to GitHub:
- `mlflow.db` (The local database storing metrics and parameters)
- `mlruns/` (The default folder for MLflow if a database isn't used)


## Purpose

This project is part of my learning journey toward becoming an MLOps engineer.
I use this repository to improve my understanding of regression models, experiment tracking, and machine learning workflows.