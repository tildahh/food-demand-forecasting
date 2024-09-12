### Food Demand Forecasting

**Sara Orona**
![Header](https://github.com/tildahh/food-demand-forecasting/blob/main/images/food-demand-header2.png)
#### Executive summary
Our objective was to predict the number of orders for different meals using various machine learning models. Our predictive model identified three critical features that most significantly influence food demand: `center_type_week_count`, `checkout_price`, and `region_week_count`. By focusing on these features, businesses can implement targeted strategies to optimize operations, pricing, and marketing efforts. These data-driven decisions will enhance operational efficiency, meet consumer demand more effectively, and drive overall business growth.


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

Sample of the data used for the analysis:

| Week   | Checkout Price | Base Price | Email Promo | Homepage Featured | Meal ID | Meal Category | Cuisine    | City | Region | Center | Center Type | Op Area | Num Orders |
|--------|----------------|------------|-------------|-------------------|---------|---------------|------------|------|--------|--------|-------------|---------|------------|
| 88     | 485.03         | 680.03     | 0           | 0                 | 1962    | Pizza         | Continental| 596  | 71     | 99     | TYPE_A      | 4.5     | 270        |
| 67     | 484.03         | 485.03     | 0           | 0                 | 2304    | Desert        | Indian     | 590  | 56     | 153    | TYPE_A      | 3.9     | 53         |
| 108    | 185.30         | 185.30     | 0           | 0                 | 2707    | Beverages     | Italian    | 675  | 34     | 106    | TYPE_A      | 4.0     | 445        |
| 100    | 292.03         | 291.03     | 0           | 0                 | 1525    | Other Snacks  | Thai       | 556  | 77     | 50     | TYPE_A      | 4.8     | 256        |

**Customer Preferences by Region and Cuisine**: 
The average order count by cuisine in each of the eight different regions.
![Customer Preferences by Region and Cuisine](https://github.com/tildahh/food-demand-forecasting/blob/main/images/pref-by-region-and-cuisine.png)

#### Methodology
1. Data Preprocessing: Cleaning and preparing the data for modeling, including feature engineering of new temporal features and handling categorical variables.
2. Model Training and Validation: Splitting the data into training, validation, and test sets. Evaluating multiple machine learning models using RMSLE as the performance metric.
3. Hyperparameter Tuning: Using RandomizedSearchCV for hyperparameter tuning to optimize model performance.
4. Permutation Importance: Analyzing feature importance to understand the key drivers of meal orders.

#### Results
After evaluating several models, we found that the Neural Network performed the best with a Validation RMSLE of 0.528 and a Test RMSLE of 0.532, indicating it generalizes well to unseen data.
![Model Performance](https://github.com/tildahh/food-demand-forecasting/blob/main/images/model_performance_metrics.png)

##### Feature Importance Analysis
Both the SHAP and Permutation Importance plots highlight `center_type_week_count`, `checkout_price`, and `region_week_count` as the key features. SHAP values give detailed insights into how these features impact individual predictions, while Permutation Importance shows their essential role in keeping the model accurate. Together, these analyses provide a clear understanding of which features are most important and how they affect the predictions.

1. **Center Type Week Count**:
  - This feature tracks the number of orders processed by different types of distribution centers (e.g., TYPE_A, TYPE_B, TYPE_C) within a given week.
  - Understanding the operational activity levels across different center types helps in recognizing patterns of peak demand and operational efficiency. For instance, if TYPE_A centers consistently handle higher volumes, this may indicate better logistical capabilities or higher regional demand.
- Actionable Strategies:
  - Operational Scaling: Enhance capacity and resources for center types with higher demand during peak weeks to ensure smooth operations and avoid bottlenecks.
  - Resource Allocation: Optimize workforce and inventory distribution based on the expected activity levels of different center types.

2. **Checkout Price**:
  - This feature represents the selling price of food items.
  - Pricing is a critical lever that directly influences consumer purchasing behavior. The model’s recognition of checkout price as a top feature underscores its importance in driving demand.
- Actionable Strategies:
  - Dynamic Pricing: Implement dynamic pricing strategies to balance demand. For example, offering discounts during low-demand periods can boost sales and help maintain a steady flow of orders.
  - Promotional Campaigns: Use pricing data to design targeted promotional campaigns that attract more customers and increase order volumes during off-peak periods.

3. **Region Week Count**:
  - This feature captures the total number of orders within each region for each week.
  - Regional demand patterns provide insights into geographical variations in consumer behavior and external factors affecting demand.
- Actionable Strategies:
  - Tailored Marketing: Develop region-specific marketing strategies based on demand patterns. For instance, regions with higher demand in certain weeks could benefit from localized promotions and advertisements.
  - Inventory Management: Adjust inventory levels to match regional demand, ensuring that high-demand regions are well-stocked while avoiding overstocking in lower-demand areas.

###### SHAP Values
- **Most Important Features**: The features `center_type_week_count`, `checkout_price`, and `region_week_count` have the biggest influence on our model's predictions.
- **Impact on Predictions**: The `checkout_price` generally lowers the predicted number of orders when it increases, while the effect of `center_type_week_count` can be either positive or negative depending on its value.

![SHAP Summary Plot](https://github.com/tildahh/food-demand-forecasting/blob/main/images/shap-summary-plot.png)

###### Permutation Importance
- **Crucial Features**: `center_type_week_count`, `region_week_count`, and `checkout_price` are essential for the accuracy of our model. Changing these features has the biggest negative impact on the model’s performance.
- **Direct Impact**: This plot shows which features are most important for the model’s accuracy, confirming that `center_type_week_count` and `checkout_price` are critical.

![Permutation Importance Plot](https://github.com/tildahh/food-demand-forecasting/blob/main/images/perm-importance-nn.png)

### Additional Insights

- **Impact of Promotions on Number of Orders**: This plot illustrates the effect of promotions on the number of orders placed.
![Impact of Promotions on Number of Orders](https://github.com/tildahh/food-demand-forecasting/blob/main/images/impact_promotion_num_orders.png)

- **Seasonality patterns by cuisine**
![seasonality](https://github.com/tildahh/food-demand-forecasting/blob/main/images/seasonality_cuisine.png)

#### Next steps
Based on the model's insights, we recommend the following actions:

1. **Pricing Strategy**: Adjust the pricing of meals, particularly focusing on reducing `checkout_price` with promotions to optimize order volumes.
2. **Promotional Campaigns**: Leverage discounts strategically, as `discount_percent` was a significant factor influencing orders.

#### Outline of project

- [Link to notebook](https://github.com/tildahh/food-demand-forecasting/blob/main/food_demand_forecasting.ipynb)

##### Contact and Further Information
- Email: sara.orona@outlook.com
- ([LinkedIn](https://www.linkedin.com/in/sara-orona/))
