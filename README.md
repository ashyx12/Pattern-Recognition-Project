# Heart Disease Risk Prediction

A machine learning project for predicting heart disease risk using the Cleveland heart disease dataset. The project compares multiple classification models, calibrates prediction probabilities, and includes a simple web interface for sending patient inputs to a deployed prediction API.

## Overview

This project trains and evaluates heart disease classification models using common clinical features such as age, chest pain type, resting blood pressure, cholesterol, maximum heart rate, exercise-induced angina, and related cardiac indicators.

The goal is not only to predict disease presence, but also to make predictions more reliable by using calibrated confidence scores and deferring uncertain cases for human review.

## Features

- Trained Logistic Regression, SVM, Random Forest, and Gradient Boosting classifiers
- Used stratified train, calibration, and test splits
- Tuned models with GridSearchCV and 5-fold stratified cross-validation
- Evaluated performance using AUROC, precision, recall, F1-score, false negative rate, coverage, and selective risk
- Applied probability calibration to improve confidence reliability
- Added selective prediction to defer low-confidence cases
- Used fuzzy logic for interpretable risk categorization
- Built a simple HTML interface connected to an AWS API endpoint

## Project Structure

```text
.
├── README.md
├── heart_cleveland_upload.csv
├── index.html
└── main.ipynb
```

## Dataset

The dataset contains 297 patient records with 13 clinical input features and one binary target column:

- `condition = 0`: no heart disease
- `condition = 1`: heart disease present

## Model Performance

Best observed notebook results:

| Model | AUROC | Precision | Recall | F1-score |
| --- | ---: | ---: | ---: | ---: |
| Logistic Regression | 0.9308 | 1.0000 | 0.8214 | 0.9020 |
| SVM | 0.9275 | 1.0000 | 0.7857 | 0.8800 |
| Random Forest | 0.9286 | 0.8750 | 0.7500 | 0.8077 |
| Gradient Boosting | 0.9252 | 0.9130 | 0.7500 | 0.8235 |

The final notebook exports a calibrated Random Forest model using `joblib`.

## How to Run

Install dependencies:

```bash
pip install numpy pandas matplotlib scikit-learn joblib jupyter
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open and run:

```text
main.ipynb
```

For local execution, make sure the dataset path points to the local CSV file:

```python
df = pd.read_csv('heart_cleveland_upload.csv')
```

## Web Interface

The `index.html` file provides a simple form for entering patient feature values and sending them to a prediction API.

To open locally:

```bash
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000/index.html
```

## Tech Stack

- Python
- scikit-learn
- Pandas
- NumPy
- Matplotlib
- Joblib
- HTML, CSS, JavaScript
- AWS Lambda
- API Gateway
- Amazon S3

## Disclaimer

This project is for educational purposes only and should not be used for medical diagnosis or clinical decision-making.
