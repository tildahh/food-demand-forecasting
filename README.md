### Food Demand Forecasting

**Sara Orona**

#### Executive summary
Our objective was to predict the number of orders for different meals using various machine learning models. After evaluating several models, we found that the Neural Network performed the best with a Validation RMSLE of 0.528 and a Test RMSLE of 0.532, indicating it generalizes well to unseen data.


#### Rationale
Accurate demand forecasting is crucial for fulfillment centers to optimize inventory levels, reduce food waste, and ensure adequate staffing. By predicting the number of orders, we can make informed decisions that enhance operational efficiency and customer satisfaction.


#### Research Question
How can we predict the number of orders for distribution centers using machine learning models, and what are the key factors influencing these orders?

#### Data Sources
The dataset used in this analysis includes:

* 77 distribution center's order history grouped by week and meal 
* These distribution centers operate across 8 regions and are categorized by center type A, B, and C
* The distribution center offer on average 46 unique meals 
* On average each center has 10,745 orders per week with a high of 29,631 and low of 2,932 orders
* Meal attributes includes category, cuisine, and pricing
* Promotional data such as email promotions and homepage features

Here is a sample of the data used for the analysis:

| Week   | Checkout Price | Base Price | Discount | Email Promo | Homepage Featured | Meal ID | Meal Category | Cuisine    | City | Region | Center | Center Type | Op Area | Num Orders |
|--------|----------------|------------|----------|-------------|-------------------|---------|---------------|------------|------|--------|--------|-------------|---------|------------|
| 88     | 485.03         | 680.03     | 195.0    | 0           | 0                 | 1962    | Pizza         | Continental| 596  | 71     | 99     | TYPE_A      | 4.5     | 270        |
| 67     | 484.03         | 485.03     | 1.0      | 0           | 0                 | 2304    | Desert        | Indian     | 590  | 56     | 153    | TYPE_A      | 3.9     | 53         |
| 108    | 185.30         | 185.30     | 0.0      | 0           | 0                 | 2707    | Beverages     | Italian    | 675  | 34     | 106    | TYPE_A      | 4.0     | 445        |
| 100    | 292.03         | 291.03     | 0.0      | 0           | 0                 | 1525    | Other Snacks  | Thai       | 556  | 77     | 50     | TYPE_A      | 4.8     | 256        |

#### Methodology
1. Data Preprocessing: Cleaning and preparing the data for modeling, including feature engineering of new temporal features and handling categorical variables.
2. Model Training and Validation: Splitting the data into training, validation, and test sets. Evaluating multiple machine learning models using RMSLE as the performance metric.
3. Hyperparameter Tuning: Using RandomizedSearchCV for hyperparameter tuning to optimize model performance.
4. Permutation Importance: Analyzing feature importance to understand the key drivers of meal orders.

#### Results
The Neural Network model outperformed other models in terms of Validation RMSLE, as shown below.
![Model Comparison: Validation RMSLE](https://github.com/tildahh/food-demand-forecasting/blob/main/images/validation_rmsle.png)

##### Feature Importance Analysis
Both the SHAP and Permutation Importance plots highlight `center_type_week_count`, `checkout_price`, and `region_week_count` as the key features. SHAP values give detailed insights into how these features impact individual predictions, while Permutation Importance shows their essential role in keeping the model accurate. Together, these analyses provide a clear understanding of which features are most important and how they affect the predictions.

###### SHAP Values
- **Most Important Features**: The features `center_type_week_count`, `checkout_price`, and `region_week_count` have the biggest influence on our model's predictions.
- **Impact on Predictions**: The `checkout_price` generally lowers the predicted number of orders when it increases, while the effect of `center_type_week_count` can be either positive or negative depending on its value.

![SHAP Summary Plot](https://github.com/tildahh/food-demand-forecasting/blob/main/images/shap-summary-plot.png)
![SHAP Values](https://github.com/tildahh/food-demand-forecasting/blob/main/images/shap-values.png)

###### Permutation Importance
- **Crucial Features**: `center_type_week_count`, `region_week_count`, and `checkout_price` are essential for the accuracy of our model. Changing these features has the biggest negative impact on the model’s performance.
- **Direct Impact**: This plot shows which features are most important for the model’s accuracy, confirming that `center_type_week_count` and `checkout_price` are critical.

![Permutation Importance Plot](https://github.com/tildahh/food-demand-forecasting/blob/main/images/perm-importance-nn.png)

### Additional Insights
- **Customer Preferences by Region and Cuisine**: This plot shows the average orders for different cuisines across various regions.
![Customer Preferences by Region and Cuisine](https://github.com/tildahh/food-demand-forecasting/blob/main/images/pref-by-region-and-cuisine.png)

- **Impact of Promotions on Number of Orders**: This plot illustrates the effect of promotions on the number of orders placed.
![Impact of Promotions on Number of Orders](https://github.com/tildahh/food-demand-forecasting/blob/main/images/impact_promotion_num_orders.png)

- **Seasonality patterns by cuisine**
[seasonality](https://github.com/tildahh/food-demand-forecasting/blob/main/images/seasonality_cuisine.png)

#### Next steps
Based on the model's insights, we recommend the following actions:

1. **Pricing Strategy**: Adjust the pricing of meals, particularly focusing on reducing `checkout_price` with promotions to optimize order volumes.
2. **Promotional Campaigns**: Leverage discounts strategically, as `discount_percent` was a significant factor influencing orders.

#### Outline of project

- [Link to notebook](https://github.com/tildahh/food-demand-forecasting/blob/main/food_demand_forecasting.ipynb)

##### Contact and Further Information
- Email: sara.orona@outlook.com
- ([LinkedIn](https://www.linkedin.com/in/sara-orona/))
