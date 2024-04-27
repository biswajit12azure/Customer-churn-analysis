# Churn Prediction Analysis
#### Contributors : Biswajit Dash

<br>


## Data Requirements
---

### Data Feature Explanation
---
| **Data** | **Variable** | **Description** |
|:---:|:---:|:---:|
| E Comm | CustomerID | Unique customer ID |
| E Comm | Churn | Churn Flag |
| E Comm | Tenure | Tenure of customer in organization |
| E Comm | PreferredLoginDevice | Preferred login device of customer |
| E Comm | CityTier | City tier |
| E Comm | WarehouseToHome | Distance in between warehouse to home of customer |
| E Comm | PreferredPaymentMode | Preferred payment method of customer |
| E Comm | Gender | Gender of customer |
| E Comm | HourSpendOnApp | Number of hours spend on mobile application or website |
| E Comm | NumberOfDeviceRegistered | Total number of deceives is registered on particular customer |
| E Comm | PreferedOrderCat | Preferred order category of customer in last month |
| E Comm | SatisfactionScore | Satisfactory score of customer on service |
| E Comm | MaritalStatus | Marital status of customer |
| E Comm | NumberOfAddress | Total number of added added on particular customer |
| E Comm | Complain | Any complaint has been raised in last month |
| E Comm | OrderAmountHikeFromlastYear | Percentage increases in order from last year |
| E Comm | CouponUsed | Total number of coupon has been used in last month |
| E Comm | OrderCount | Total number of orders has been places in last month |
| E Comm | DaySinceLastOrder | Day Since last order by customer |
| E Comm | CashbackAmount | Average cashback in last month |


## Machine Learning Workflow
![Google Drive Image](https://drive.google.com/uc?export=view&id=1oHFeic_FP2p7W0Ffh_dce0xfAsXHup5N)
Dalam langkah Churn Prediction Analysis terbagi dalam beberapa Stage
1. Stage 0: Problem Statements, Goal, & Objective Analysis
2. Stage 1: EDA, Insights & Visialization (Data Understanding)
3. Stage 2: Data Processing (Data Cleansing & Feature Engineering)
4. Stage 3: Machine Learning Modelling & Model Evaluation

## Stage 0 :
### Problem Statements
Shoptify is an e-commerce company that is currently experiencing customer churn of 16.8%. This causes Shoptify to lose many customers, which will impact Shoptify's revenue. In addition, the costs of acquiring new customers are much greater than the costs of retaining old customers. Therefore, Shoptify needs to identify the causes of customer churn and solutions to overcome this problem. By predicting which customers are likely to churn, Shoptify can determine the right marketing strategy steps according to customer characteristics.

### Goal
Predict the types of customers who have the potential to churn by identifying features to minimize customer churn rates and get the right business decisions.

### Objective
1. Membuat model Machine Learning untuk memprediksi user yang berpotensi churn se1. Create a Machine Learning model to predict users who have the potential to churn and understand what features cause users to churn and features that stimulate the potential to minimize the churn rate
2. Optimize company revenue by grouping users who have the potential to churn so that they can be given different treatment so that the churn rate decreases.

### Business Metric
1. Customer churn rate which is the percentage of customers who stop using e-commerce.
2. Revenue is the main metric in the e-commerce business.

## Stage 1 :
### EDA & Insight Summary
1. There are 7 variables that have missing values.
2. The average customer spends 3 hours using e-commerce applications.
3. There are still many customers who do not use coupons when shopping.
4. Customers with locations closer to the warehouse (< 15 km) dominate more.
5. The number of customers who complain is quite large, around 1000 people. This must be a concern in future business development.
6. The Tenure variable is of concern because there are many customer churns with tenure < 2 months.
7. The Tenure & Complain variable has a fairly good correlation with the target variable (Churn), namely -0.35 and 0.25.
8. The customer churn rate is higher among customers who use a few coupons (only 1-2) or even customers who don't use coupons at all. A business decision that can be made is to provide coupons every weekend or on a certain date.
9. There is no guarantee that if the satisfaction score is high, the probability of churn will be lower.

## Stage 2 :
### Preprocessing
![Google Drive Image](https://drive.google.com/uc?export=view&id=182N3hLlIp2_OpGTlSVsPrDjeu2DaVIIO)
1. From the entire data there are still differences in data filling in certain categories, so the data is first replaced into one value to eliminate redundancies, namely in the PreferredLoginDevice and PreferredPaymentMode columns by replacing Phone to Mobile Phone, then CC to Credit Card, then Cash On Delivery becomes COD. To handle feature values ​​that are still empty, imputation is carried out by inputting the median value of each feature because the mean and median values ​​are not unequal and the median value is absolute.
2. After checking the dataset, there are no rows of data that have the same value for all the features.
3. With the z score method, around 0.2% of the outliers will be removed, namely 11 rows of data that will be dropped.
4. Categorical data which is an object/string data type needs to be converted into a numeric data type with feature encoding which is divided into two methods, for gender features label encoding is done and for data that has more than 2 categories one hot encoding is done.
5. The initial stage in feature transformation is classifying whether the feature has a normal distribution or not based on the skew and kurtosis values. After that, the overall data was split into a train set of 70% and a test set of 30%. Then, standardization is used to adjust the values ​​between features. The training data is then scaled using the Standard Scaler and then fit & transformed, while the testing data is only transformed.
6. Features that are less relevant in the modeling process will be dropped, namely the Customer ID feature so that the total features used are 5 numerical features, 13 categorical features and 1 target feature, namely 'Churn'.
7. In the target feature (Churn) there is a significant data imbalance, namely with a false value of 83.12% and a true value of 16.84%. To handle this condition, an oversampling process is carried out to equalize the ratio in the training data only using the SMOTE method, namely by generating new values ​​for the variables, based on the data distribution so that the data ratio is balanced.
## Stage 3 :
### Modeling
![Google Drive Image](https://drive.google.com/uc?export=view&id=15RM21tpRbpTwBcFhdBpRXpDL8M2-hzAF)
5 alternatives are used to determine a model with precision and roc auc cross train test as parameters. It was found that random forest was the chosen model because it had a minimum value for false positives and a gap of 0.01.
### Recommendation
1. Increase service levels in handling customer complaints by improving the products or services provided such as automation of customer service and live chat.
2. The Marketing Team can focus on customers who have been using the application for a long time in providing promotions and product recommendations in order to retain customers.
