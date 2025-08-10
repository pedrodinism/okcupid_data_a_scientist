# Project Overview #
This project tackles a multi-class classification problem using two distinct types of features:

1. Tabular data — categorical and numerical columns
2. Free-text data — a series of essays written by each person

The core idea is to train separate models for each data type, and then stack them to produce a single final prediction.
The first model is itself built using stacking, making this a double-stacking approach.

# Exploratory Data Analysis (EDA) #
The project begins with an exploratory analysis of the dataset.

Outliers and missing values were handled.

Some categories were grouped together to ensure that each class had enough examples for the model to learn effectively.

The free-text fields were cleaned by removing punctuation, HTML tags, and stop words (words with little to no predictive value).

# Feature Engineering #
A flexible setup was created so the target column could be changed simply by modifying a single variable (col_to_predict).

After selecting the target column:

Rows with unknown values for the target are removed.

Categorical variables are one-hot encoded.

Numerical variables are standardized.

# Model Training #
Model 1 — Tabular Data Stacking
This is a stacked model with the following base learners:

- Logistic Regression
- Random Forest
- Extra Trees
- Decision Tree
- K-Nearest Neighbors
- XGBoost

The final estimator in the stack is a Logistic Regression model.

Model 2 — Text Classification
The text model is a pipeline composed of:

- CountVectorizer (to transform text into numerical features using a bag-of-words representation)
- Multinomial Naive Bayes (the classifier)

# Final Output — Double Stacking #
The outputs from the two models (probabilities for each class) are combined into a new dataset of meta-features.
A Logistic Regression model is then trained on these meta-features to produce the final prediction.
