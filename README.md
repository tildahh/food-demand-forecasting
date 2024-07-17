### Food Demand Forecasting

**Sara Orona**

#### Executive summary
Our objective was to predict the number of orders for different meals using various machine learning models. After evaluating several models, we found that the Random Forest model performed the best with a Train RMSLE of 0.73 and a Test RMSLE of 0.73, indicating it generalizes well to unseen data.


#### Rationale
Accurate demand forecasting is crucial for fulfillment centers to optimize inventory levels, reduce food waste, and ensure adequate staffing. By predicting the number of orders, we can make informed decisions that enhance operational efficiency and customer satisfaction.


#### Research Question
How can we predict the number of orders for distribution centers using machine learning models, and what are the key factors influencing these orders?

#### Data Sources
The dataset used in this analysis includes:

* Weekly meal order data
* Meal attributes such as category, cuisine, and pricing
* Center details including city, region, and operational area
* Promotional indicators such as email promotions and homepage features

#### Methodology
1. Data Preprocessing: Cleaning and preparing the data for modeling, including feature engineering and handling categorical variables.
2. Model Training and Validation: Splitting the data into training, validation, and test sets. Evaluating multiple machine learning models using RMSLE as the performance metric.
3. Hyperparameter Tuning: Using RandomizedSearchCV for hyperparameter tuning to optimize model performance.
4. Permutation Importance: Analyzing feature importance to understand the key drivers of meal orders.

#### Results
The Random Forest model achieved the lowest RMSLE on both the training and test sets, indicating its robustness and accuracy. Key features influencing number of orders included 'checkout_price', 'base_price', and 'discount_percent'. These insights suggest that pricing strategies and promotional discounts significantly impact order volumes.

#### Next steps
Based on the model's insights, we recommend the following actions:

Pricing Strategy: Adjust the pricing of meals, particularly focusing on 'checkout_price' and 'base_price', to optimize order volumes.
Promotional Campaigns: Leverage discounts strategically, as 'discount_percent' was a significant factor influencing orders.
Further Analysis: Conduct deeper analysis on other influential features to uncover additional insights.

#### Outline of project

- [Link to notebook 1]()

##### Contact and Further Information
- Email: sara.orona@outlook.com
- ([LinkedIn](https://www.linkedin.com/in/sara-orona/))
