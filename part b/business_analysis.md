# Part B: Business Case Analysis
# B1 Problem Formulation
# Answer for B1.a: 
As per scenario target variable is number of Item sold. The input features are store_id, store_size, location_type, promotion_type,promotion_id,transaction_id,transaction_date,weekend, festival_days.
We formulate this scenoriao as a supervised ML regression problem because our target variable i.e. number of item sold is continuous numeric value, also data is labeled and learn mappings from inputs to outputs. Our objective is to prdict number of item sold  by considering the important feature, so algorithm linear regression will give the prediction.
# Answer for B1.b:
Total sales revenue is affected by discount, price change & multiple category products sale, so the final evaluation of store on the basis of only Total sale revenue is not justifiable.If we use item sold as factor for evaluation of store it directly reflects demand & promotion effectiveness.So this illustrate real world ML world projects principle that the target variable is align with business objective & not majorly affected by external factors to show the true performance.
# Answer for B1.c:
If we run one single gloabl model across 50 stores, it may not able to capture correct trend of the customer behaviour & promotion effect across the all location.
A better approach would be go for building model segment wise means built separate model for urban, semi-urban, rural stores combined with promotion type. So in this approach we can find pattern of customer behaviour and promotion effectiveness and accordingly plan the actionable things to maximize the number of item sold.
# B2 Data and EDA Strategy
# Answer for B2.a:
We can join the four tables by using primary keys like store_id, promotion_id, transaction_date, transaction_id.
The grain of the final modelling dataset would be:total item sold per store per month.
Before modelling we perform aggregration on below-
Total item sold, promotion_type applied, number of transaction, is_weekend and is_festival indicators.
# Answer for B2.b:
We can use below EDA Startergies
# 1.Correlation Heatmap-To Identify relationship between numerical features & helps in feature selection
# 2.Sales trend over time(Line chart)-To identify seasonality & trends
# 3.Sales by promotion type(Bar chart)-To identify which promotion deliver the highest sale
# 4.Sales by location type(Box Plot)- To identify & compare sales across the location, helps for segmentation stratergy
# Answer B2.c:
If 80% of transactions in the dataset occurred without any promotion then model may become biased give most results toward predicting non-promotion outcomes. So model may miss to learn actual effects of promotions.To overcome this we use balanced dataset, also analyse promotion and non promotion dataset separately.
# Model Evaluation and Deployment
# Answer B3.a:
I set the train and test split based on time span, using earlier months for training and latest months for testing. A random split in appropriate here because there is chance of mixing past and future data, which is not good for prediction and results in unrealistic performance.
Here we are predicting number of Item sold which is continuous value, so we measure how close the predicted values are to the actual values.Evaluation done through below metricses:
Mean Squared Error(MSE)-Computes the average of the squared differences between predictions and actuals
Root Mean Square Error-Measure large error, useful for identifying large prediction mistakes.
# Answer B3.b:
Feature Impotance concept helps to identify which factors influence model predictions. In this scenario the model recommends the Loyalty Points Bonus for Store 12 in December festival season,year end high customer activity, while Flat Discount for Store 12 in March due to overall lower demand in market.By analysing these seasonal features we can conclude how different factors influence decision across month.This helps communicate insight to marketing team.
# Answer B3.c:
The trained model can be saved using joblib or pickle.
At the start of each month data is collected and preprocessed using the existing pipeline and saved model is used to generate predictions.
While monitoring I track the MSE & RMSE over time, find changes in data distribution and set alert for performance degradation, if the performance drops, the model should be retrained with updated data.  

