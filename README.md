# A-Look-Into-Indian-StartUps
ACM Data Analytics Project 2023

**1. Suitable Investor Recommender**   
This Python code defines a function suitable_investor(company, sector, location) that recommends potential investors for a startup company based on its attributes. The function takes three parameters: company (the name of the startup), sector (the industry sector of the startup), and location (the geographical location of the startup).

Features

The following features are considered for each startup:

Company
Sector
Location
Select Investors

How it Works

The new startup entry, provided by the user, is concatenated with the original dataset. The 'Select Investors' field is left empty in this case.
Relevant features for each startup are combined into a single string.
Text data is transformed into numerical features using TF-IDF vectorization.
The cosine similarity matrix is computed to measure the similarity between startups.
The index of the new startup entry is determined.
The top 5 most similar startups are identified using the cosine similarity scores.
The recommended investors for the new startup are extracted from the most similar startups.


**2. Predict Valuation**
This is a Python function that predicts the valuation of a company based on various input parameters. The function takes the following inputs:

sector: The sector to which the company belongs.
subsector: The sub-sector of the company.
entryvaluation: The entry valuation of the company in billions of dollars ($B).
entry: The entry point of the company.
location: The location of the company.
investors: List of investors.

The function performs the following steps:

It prepares the necessary data by selecting relevant features from the dataset and creating an input data frame.
Splits the data into training and testing sets using the train_test_split function from the sklearn.model_selection module.
Encodes categorical features using target encoding with the help of the TargetEncoder class from the category_encoders library.
Initializes a Gradient Boosting Regressor model from the sklearn.ensemble module and fits it to the encoded training data.
Predicts the valuation for the input data using the trained model.
Formats the predicted valuation into a human-readable form, rounded to the nearest million dollars.


**3. Predicted Funding Amount**
This code snippet defines a Python function `ret_predicted_funding(year, domain, city, stage)` that predicts the funding amount for a startup based on given input parameters. The function follows these steps:
   
   1. Data Preparation:
      
      - The code assumes the data is stored in a DataFrame named `df`.
      - Features (X) are extracted, including 'Founded' (year of founding), 'Domain', 'City', and 'Stage'.
      - The target variable 'Amount' is the funding amount, converted to a floating-point number.
   
   2. Input Data:
      
      - The input parameters, 'year', 'domain', 'city', and 'stage', are used to create an input DataFrame named `input_data`.
   
   3. Train-Test Split:
      
      - The data is split into training and testing sets using an 80-20 split ratio and a random seed of 42.
      - The input data is appended to the testing set for prediction.
   
   4. Outlier Handling:
      
      - Outliers in the training set are identified and normalized using the z-score method.
      - Outliers are defined as values deviating more than 3 times the standard deviation from the median funding amount for a given domain.
   
   5. Categorical Variable Encoding:
       
      - Categorical variables are identified and encoded using target encoding.
      - The `TargetEncoder` from a library (presumably scikit-learn) is used to perform this encoding.
   
   6. Feature Selection:
       
      - The `SelectKBest` method with `f_regression` score function is used for feature selection.
      - The top k (in this case, 4) features with the highest scores are selected.
   
   7. Model Selection and Training:
       
      - A `RandomForestRegressor` model is chosen with specific hyperparameters (max_depth, min_samples_split, n_estimators).
      - The model is trained on the selected features from the training set.
   
   8. Prediction:
       
      - The trained model is used to predict funding amounts on the selected features from the test set.
      - The predicted funding amount for the last test instance is retrieved.
   
   9. Formatting and Output
       
      - The predicted funding amount is post-processed by dividing it by 1,000,000 (to convert to millions) and rounding to 1 decimal place.
      - The formatted value is returned as a string in the format "$X million".
   
   To use the `ret_predicted_funding` function, call it with appropriate values for 'year', 'domain', 'city', and 'stage'. The function will predict the funding amount for the given startup based on the provided input parameters.


**4. Time-to-Unicorn Predictor**   
This repository contains a Python function get_time_to_unicorn that predicts the time it takes for a startup to become a unicorn based on various input parameters. A unicorn refers to a startup company valued at over $1 billion.

Function Description

The get_time_to_unicorn function takes the following input parameters:

founded: The year the startup was founded.
sector: The sector to which the startup belongs.
subsector: The sub-sector to which the startup belongs.
entryvaluation: The initial valuation of the startup at the time of entry.
location: The location of the startup.
The function performs the following steps:

Selects relevant features for the model from the input data, including 'Founded', 'Sector', 'Sub-Sector', 'Entry Valuation^^ ($B)', and 'Location'.
Prepares the input data using the provided input parameters.
Splits the dataset into training and testing sets using a test size of 20% and a random state of 42.
Encodes categorical features in the training and testing sets using the TargetEncoder.
Creates and trains a Decision Tree Regression model on the encoded training data.
Makes predictions for the testing set using the trained model.
Returns the predicted time-to-unicorn for the given input.
