
# AIML Recruitment Tasks — Coding Ninjas 10X Club

**Candidate:** Saran Mathesh  
**University:** SRM Institute of Science and Technology (SRMIST)  
**Domain:** Artificial Intelligence and Machine Learning

## Overview

This repository contains my solutions for the Second-Year AIML recruitment tasks for the Coding Ninjas 10X Club.

The project focuses on two machine learning applications:

1. **Air Quality Forecasting** — Predicting the next hour's ground-truth carbon monoxide concentration using historical measurements and a Random Forest regressor.
2. **MNIST Digit Classification** — Training and comparing baseline and modified neural networks to classify handwritten digits from 0 to 9.

Both notebooks include data analysis, model development, evaluation, visualizations, and findings.

---

## Repository Structure

```text
AIML-Recruitment/
│
├── Task1_Air_Quality_Forecasting.ipynb
├── Task2_MNIST_Neural_Network.ipynb
└── README.md
```

---

# Task 1 — Air Quality Forecasting

## Objective

Predict the next hour's ground-truth carbon monoxide concentration (`CO(GT)`) using current and historical air quality measurements.

## Dataset

- **Source:** UCI Machine Learning Repository
- **Dataset:** Air Quality
- **Observations:** 9,357 hourly records
- **Target:** Next-hour `CO(GT)`

## Methodology

### 1. Data Loading and Inspection
- Loaded the UCI Air Quality dataset.
- Inspected data types, missing values, and descriptive statistics.
- Examined distributions and correlations among variables.

### 2. Data Cleaning
- Combined the date and time columns into a timestamp.
- Checked for missing and duplicate timestamps.
- Replaced invalid sentinel values with missing values.
- Examined hourly continuity and handled missing observations.

### 3. Exploratory Data Analysis
- Visualized pollutant distributions.
- Examined CO concentration over time and across hours of the day.
- Analyzed correlations between pollutant measurements and environmental variables.

### 4. Feature Engineering
Created time-series features, including:
- Current CO concentration
- Lagged CO and NOx measurements
- Rolling averages of CO
- Hour, day of the week, and month

The prediction target was created by shifting `CO(GT)` one row into the future.

### 5. Model Training
- Used a chronological train-test split.
- Built a preprocessing and modeling pipeline.
- Trained a Random Forest regressor.
- Compared the model against mean and persistence baselines.

### 6. Evaluation
Used:
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- Coefficient of Determination (R²)

## Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Mean Baseline | 1.0750 | 1.3533 | -0.0155 |
| Persistence Baseline | 0.5148 | 0.7980 | 0.6480 |
| Random Forest | 0.4189 | 0.6020 | 0.7990 |

### Key Findings
- The Random Forest outperformed both baselines on the evaluated test observations.
- The current CO concentration was the most influential feature in the model's feature-importance analysis.
- Time of day and pollutant sensor measurements also contributed to predictions.
- Feature importance indicates predictive contribution, not causation.

---

# Task 2 — MNIST Neural Network

## Objective

Classify handwritten digits from 0 to 9 using neural networks trained on the MNIST dataset.

## Dataset

- **Dataset:** MNIST handwritten digits
- **Training images:** 60,000
- **Test images:** 10,000
- **Image dimensions:** 28 × 28 pixels
- **Number of classes:** 10

## Methodology

### 1. Dataset Understanding
- Loaded the MNIST dataset.
- Inspected image dimensions, labels, and pixel distributions.
- Visualized representative handwritten digits.

### 2. Preprocessing
- Normalized pixel values to the range [0, 1].
- Prepared training, validation, and test datasets.
- Used the same dataset split for model comparison.

### 3. Baseline Model
Trained a baseline neural network with a Dense hidden layer containing 128 units.

### 4. Modified Model
Trained a modified neural network with a Dense hidden layer containing 256 units and 128 units in the next layer.

### 5. Evaluation
Compared both models using:
- Test accuracy
- Test loss
- Training and validation curves
- Classification reports
- Confusion matrices
- Misclassified image examples

## Results

| Metric | Baseline | Modified |
|---|---:|---:|
| Test Accuracy | 97.56% | 97.48% |
| Test Loss | 0.083 | 0.070 |
| Best Validation Accuracy | 97.80% | 97.94% |

### Key Findings
- The baseline achieved a slightly higher test accuracy than the modified model.
- The modified model achieved a lower test loss.
- The modified model's validation accuracy was slightly higher, but this did not translate into better test accuracy.
- The modified model misclassified 252 test images.
- The confusion matrix and misclassified examples help identify visually similar digits that are difficult to distinguish.

### Interpretation

Increasing the network's depth and capacity did not improve test accuracy in this experiment. The results demonstrate that a larger architecture does not automatically generalize better to unseen data.

---

# Limitations

## Air Quality Forecasting
- Missing ground-truth measurements limit the number of usable observations.
- A one-row shift represents one elapsed hour only when timestamps are continuous.
- Random Forest predictions may not capture all temporal patterns or sudden pollution changes.
- The dataset represents a particular monitoring location and historical period.

## MNIST Classification
- The models were evaluated on the standard MNIST dataset, which may not represent real-world handwriting.
- Neural network performance depends on architecture, hyperparameters, and training configuration.
- Similar-looking digits can lead to classification errors.
- The modified model did not improve test accuracy over the baseline in this run.

---

# Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- TensorFlow / Keras
- Google Colab
- Git and GitHub

---

# How to Run

1. Open the notebook in Google Colab.
2. Run the cells sequentially from top to bottom.
3. Allow the dataset to load and preprocessing to complete.
4. Train the models and inspect the evaluation metrics and visualizations.

The Air Quality notebook downloads the UCI dataset when executed. The MNIST notebook uses the MNIST dataset.

---

# Conclusion

These tasks provided practical experience in time-series forecasting, data preprocessing, feature engineering, neural network training, model evaluation, and error analysis.

The experiments highlight the importance of comparing models against meaningful baselines, using appropriate evaluation strategies, and interpreting results based on actual test performance.

---

**Submitted as part of the AIML Domain recruitment process for the Coding Ninjas 10X Club.**
