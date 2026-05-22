# Regression Model Lab

This repository contains my experiments with regression models in machine learning.

The goal of this project is to practice training different regression models, evaluate their performance, and track experiments using MLflow.

This project uses a CSV datasets loaded with Pandas for regression experiments

## What this repository includes

- CSV datasets
- Data visualization and preparation
- Scikit-learn Pipeline integration for robust preprocessing
- Regression model training & evaluation
- MLflow experiment tracking
- Cross-experiment comparison between different regression models

## 📁 Repository Structure

```text
regression-mlflow-lab/
├── data/
│   └── Advertising.csv              # The dataset used for training models
├── regression_model_comparison_with_scaling.ipynb       # Notebook 1: Linear & SVM (Standardized)
├── regression_model_comparison_without_scaling_and_KNN.ipynb  # Notebook 2: Trees & KNN (Raw/Pipelines)
├── pyproject.toml                   # Python dependencies and project configuration (uv)
├── uv.lock                          # Locked dependency versions
├── .python-version                  # Specifies the Python version used
├── README.md                        # Project documentation
├── .gitignore                       # Files to be ignored by Git
│
# --- Generated Locally (Not pushed to GitHub) ---
├── mlflow.db                        # SQLite database storing MLflow metrics & parameters
├── mlruns/                          # Directory storing actual trained model artifacts (.pkl files)
└── .venv/                           # Local Python virtual environment
```

## Regression models I used

- Linear Regression ✔️
- Ridge Regression ✔️
- Lasso Regression ✔️
- Decision Tree Regressor ✔️
- Random Forest Regressor ✔️ 🏆
- KNN Regression ✔️
- SVM Regression ✔️
- Gradient Boosting Regressor ✔️

## 🏆 Key Insights & Methodology (The "Model Tournament")
To find the absolute best model for my dataset without data leakage, I structured my workflow like a tournament:

1. The Standardized Bracket (Notebook 1): I tested models that require feature scaling (Linear Regression, Ridge, Lasso, SVM) using StandardScaler. SVM won this bracket.
2. The Tree & Distance Bracket (Notebook 2): I tested models that don't need scaling (Decision Tree, Random Forest, Gradient Boosting) using raw data. To keep the comparison fair, I also included KNN, but wrapped it in a scikit-learn Pipeline with MinMaxScaler. This ensured the distance-based algorithm got scaled data without altering the raw data fed to the tree models!
3. The Grand Champion: Ultimately, Random Forest Regressor outperformed all other models, achieving the highest R-squared (R²) score and the lowest RMSE on this dataset.

## Tools and libraries

- Python
- Pandas
- NumPy
- Scikit-learn
- MLflow
- Matplotlib / Seaborn


## 📊 Tracking Experiments with MLflow

This project uses MLflow to track and compare different machine learning models. All experiment data is saved locally to a SQLite database.
**My biggest takeaway from this project was the sheer power of the MLflow UI.** With MLflow I was able to natively combine two different experiments (folders) in the UI and generate side-by-side performance charts instantly.

### How to view the MLflow Dashboard
To see the model comparisons, metrics, and parameters, run the following command in your terminal:

`uv run mlflow ui --port 5000`

(Note: If the server instantly crashes on Windows, you may need to limit the workers by running:

`uv run mlflow ui --port 5000 --workers 1`

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
I use this repository to improve my understanding of regression models, experiment tracking, preventing data leakage via pipelines, and streamlining machine learning workflows.