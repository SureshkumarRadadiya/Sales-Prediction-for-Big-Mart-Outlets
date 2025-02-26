# Sales-Prediction-for-Big-Mart-Outlets

BigMart Sales Prediction!

The data scientists at BigMart have collected 2013 sales data for 1559 products across 10 stores in different cities. Also, certain attributes of each product and store have been defined. The aim is to build a predictive model and predict the sales of each product at a particular outlet.

Using this model, BigMart will try to understand the properties of products and outlets which play a key role in increasing sales.

Please note that the data may have missing values as some stores might not report all the data due to technical glitches. Hence, it will be required to treat them accordingly. 

Data Dictionary
We have train (8523) and test (5681) data set, train data set has both input and output variable(s). You need to predict the sales for test data set.


<img src="Violin Plot of Item Outlet Sales By Item Type.png">

<img src="Violin Plot of Item Outlet Sales by Outlet Identifier.png">

<img src="Violin Plot of Item Outlet Sales by Outlet Size.png">

<img src="Scatter Plot of Item MRP vs Item Outlet Sales.png">

<img src="Scatter Plot of Item Visibility vs Item Outlet Sales.png">

<img src="Scatter Plot of Item Weight vs Item Outlet Sales.png">

<img src="Correlation Heatmap of Numeric Columns.png">


# Approach Note: Sales Prediction for Big Mart Outlets

# Objective:

The primary goal of this project was to build a predictive model to estimate sales for different Big Mart outlets based on historical data. The key focus was on understanding the impact of various features such as product attributes, store type, and location on sales performance.

# Data Exploration & Preprocessing:

Dataset Overview: The dataset consisted of sales data for various products across multiple outlets. The key variables included Item_Identifier, Item_Weight, Item_Fat_Content, Outlet_Identifier, Outlet_Size, Outlet_Location_Type, and Item_Outlet_Sales.

- Handling Missing Values: Imputed missing values for Item_Weight using the mean and handled Outlet_Size inconsistencies by mapping them based on Outlet_Type.

# Feature Engineering: 
Created new features such as Item_Age (years since establishment), transformed Item_Fat_Content into uniform categories, and encoded categorical variables using Label Encoding and One-Hot Encoding where necessary.

# Model Experimentation:

# Baseline Models:
- Implemented Linear Regression to establish a baseline understanding of the relationships among features.
- Observed issues like multicollinearity and heteroscedasticity, requiring further feature selection.

# Tree-Based Models:
- Decision Tree Regressor: Improved performance but prone to overfitting.
- Random Forest Regressor: Provided better generalization, handling feature interactions effectively.
- XGBoost Regressor: Performed best in terms of RMSE, leveraging boosting techniques for improved predictions.

# Hyperparameter Tuning:

# implementation of CatBoostRegressor with hyperparameter tuning using Optuna.
1. Defining Categorical Features:
  - Identifies categorical columns using np.where(x_train.dtypes == object)[0].   
2. Hyperparameter Optimization:
- Uses Optuna's trial.suggest_* methods to optimize l2_leaf_reg, max_bin, subsample, learning_rate, max_depth, min_data_in_leaf, etc.
- Splits training data using train_test_split().
- Initializes CatBoostRegressor with selected parameters.
  
- Used GridSearchCV and RandomizedSearchCV for optimizing n_estimators, max_depth, and learning_rate.
- Final model selection was based on RMSE and cross-validation scores.

# Results & Insights:

- XGBoost delivered the lowest RMSE and was selected as the final model.
- Store location and outlet type were significant determinants of sales, highlighting the importance of external factors.
- Feature engineering played a crucial role in improving model accuracy.

# Conclusion & Future Work:

This project successfully built an accurate sales prediction model using tree-based techniques. Future work can include adding external economic indicators, experimenting with deep learning models, and deploying the model into a production environment for real-time predictions.
