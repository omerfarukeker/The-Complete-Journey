# The-Complete-Journey

Churn prediction model notebook for a retail dataset (DunnHumby's The Complete Journey Dataset). 

_**This readme file gives the outlook of the detailed notebook (the .ipynb file in the repo)**_

## The Dataset

The dataset consist of eight tables in separate .csv files, we will go through six of them which we will use in this notebook. The dataset covers a two year span purchase transactions of 2500 households. Also demographics information of households, campaign and coupon redemption informations are available. In the modeling phase we will join these tables to make our final dataset.

1. Campaign Descriptions (_campaigndesc.csv)
2. Campaigns (_campaigntable.csv)
3. Coupons (coupon.csv)
4. Coupon Redemptions (_couponredempt.csv)
5. Transactions (_transactiondata.csv)
6. Demographics (_hhdemographic.csv)

## Churn Prediction

Datasets have been examined and found out that it does not contain a column which indicates whether customer(household) is churned or not. Therefore we will have to define our own churn definition and move on to the modelling.

Churn rate works well for subscription-based products or ones that have regular nature of interactions like Netflix subscription. It’s clear that customer has churned at the moment when he cancels or misses the next planned payment.

When we know which customers have churned we can ask them for reasons and prioritize fixes for them. But for not regular, transactional products churn rate is hard to measure since we don’t know which customers are churned and which are dormant.

A generally accepted retail churn rate is between five to sevent percent per year. Less than five percent is a great goal, but a churn rate over ten percent is cause for concern. Even as you acquire more customers, your business can't grow unless you have a greater volume of incoming customers than outgoing ones.

Satisfying existing customers is actually more profitable than obtaining new ones. It costs five times more to obtain a new customer than it does to retain an existing customer. Decreasing your churn rate by five percent increases profits up to 125%.

Our definition of transactional churn which splits households around 85%/15% No Churn/Churn:

_"A customer will be considered as churned if not purchased from a store 2 weeks or more."_

## Feature engineering

Following features are generated and used along with the demographics data

1. List of campaigns received by each household
2. Total number of received campaigns per household
3. List of campaigns resulted in coupon redemption
4. The number of redemptions made by each household
5. Most Frequent Campaign Type (A,B,C) received by each household
6. Top 20 stores with high number of households which have more high out weeks
7. Amount of purchase of a household within two years

## ML Model Training & Testing

A Machine Learning model is trained with the training data. The machine learning model is chosen as **XGBoost** (Extreme Gradient Boosting) as they are known to be performing well with imbalanced datasets like the ones we use.

**Hyperparameter optimisation** with **RepeatedStratifiedKFold** is used for optimising the model parameters. The classification results are evaluated with the **ROC-AUC** along with few other metrics.

