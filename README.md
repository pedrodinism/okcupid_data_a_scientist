This project tackles a multi-class classification problem using two different types of features:

1. Tabular data (categorical + numerical columns)
2. Text-free data, where each person wrote several essays about themselves

The idea was to train several models with the different data and then stack those models to reach a final output.

The first model is achieved with stacking as well, making this a double-stacking approach.

# --- EDA --- #

The first step consists on performing EDA on the dataset. I analyzed the data, handled outliers, missing values and also grouped some categories together, to try to ensure that every class had enough data for the model to learn.
Also cleaned the free text fields by removing pontuaction, html and stop words (words that are meaningless to the model).

# --- Feature engineering --- #

In the second step I created some logic in a way that allows me to predict results for different columns only by changing one variable (col_to_predict).
After selecting this column:
- unknown values for the target are removed from the dataset
- categorical variables are one-hot encoded
- numerical variables are standardized

# --- Model training --- #

In this step the data is split between train and test datasets and the models are trained.
The first model is stacked with the following base models:
- Logistic Regression
- Random Forest
- Extra Trees
- Decision Tree
- K-Nearest Neighbors
- XGBoost

The final estimator is a Logistic Regression model

The second model (text-model) is a Multinomial Naive Bayes

# --- Final output --- #

In this phase it is used Logistic Regression to compute the final decision using the outputs from the 2 models




