# 🚀 Exoplanet Discovery Method Classification

## Project Overview

This project classifies the discovery method of exoplanets using the Exoplanets — Method Classification Dataset. The focus is on distinguishing between the two most common methods: "Radial Velocity" and "Transit". The workflow includes data cleaning, missing value handling, exploratory data analysis, and machine learning with decision trees.

## Dataset Description 🪐

- **method**: Discovery method (e.g., "Radial Velocity", "Transit", etc.)
- **number**: Number of planets in the discovered system
- **orbital_period**: Orbital period of the planet (in days)
- **mass**: Planet mass in Jupiter masses (contains missing values)
- **distance**: Distance from Earth (in light years)
- **year**: Year of discovery

## Getting Started ⚡️

1. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```
2. Open and run the notebook `exoplanet.ipynb` step by step.

## Approach

- **Binary Classification**: The problem is simplified to a binary classification task by focusing only on the "Radial Velocity" and "Transit" methods, which represent the majority of the dataset. This avoids issues related to underrepresented classes and leads to a more interpretable and robust model.

- **Handling Missing Values**: Missing values are present exclusively in the `mass` and `distance` columns. The absence of these values is strongly correlated with the discovery method, especially for "Transit". Two boolean features (`has_mass` and `has_distance`) are created to indicate missingness, and the original columns are dropped. This preserves the information about missingness, which is highly predictive for the classification task.

- **Exploratory Data Analysis**: Univariate analysis of the main numerical features (`number`, `orbital_period`, `year`) is performed using histograms and boxplots to understand their distributions and relationships with the target variable.

- **Model Training**: Decision tree models are trained, as they are robust to non-normal distributions and outliers. Evaluation is performed using stratified 5-fold cross-validation.

- **Feature Importance**: The most important feature for classification is `has_mass`, highlighting the crucial role of missing value management in the model's performance.

## Results 📊

- **Cross-validation accuracy**: ~96%
- **Test set accuracy**: ~98%
- The model achieves high precision, recall, and F1-score for both classes.
- The classification is mainly driven by the presence or absence of the `mass` value, rather than intrinsic physical differences between the planets discovered by the two methods.

## Files
- `exoplanet.ipynb`: Main analysis and modeling notebook
- `exoplanet.csv`: Dataset
- `requirements.txt`: List of required Python packages

## Author ✨
Michele Guida
