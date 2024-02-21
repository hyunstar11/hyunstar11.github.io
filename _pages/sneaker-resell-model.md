---
layout: custom
title: Sneaker Resell Price Prediction Model
permalink: /sneaker-resell-model/
---

# Sneaker Resell Price Prediction Model
Revised in November 2023

[Click Here for the Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/ML/%ED%95%9C%EC%A0%95%ED%8C%90%20%EC%8B%A0%EB%B0%9C%20%EB%A6%AC%EC%85%80%EA%B0%80%20%EC%98%88%EC%B8%A1%20%EB%AA%A8%EB%8D%B8/Sneaker_ResellPred_Model_Edit.ipynb)

# Project Outline 

#### 1. Introduction 
 - 1.1. Problem Statement
 - 1.2. Description of the dataset 

#### 2. Project Methodology
- 2.1. EDA and Data Analysis 
- 2.2. Modeling & Selection   
- 2.3. Feature Importance 
- 2.4. Interpreting Coefficients (PDP Plot) 

# 1. Introduction 
### 1.1. Problem Statement 
- The sneaker resale market has seen significant growth since 2010. This project aims to leverage data analysis to predict sneaker resale prices, a topic of personal interest from childhood.

### 1.2. Description of the dataset  
- The project utilizes a dataset of 100,000 transactions from StockX, covering 53 limited edition shoes, including Adidas Yeezy and Nike Off-White models.

![StockX Data](https://user-images.githubusercontent.com/90128775/184078928-c0470835-e453-448e-b325-7afa42aeeb9d.png)

# 2. Steps
### 2.1. EDA and Data Analysis 
- Overview of My Data Processing Pipeline
- For the project, I worked with a dataset of sneaker sales, focusing on enhancing the data to make it suitable for advanced analysis and machine learning. Below is an overview of the steps I took to preprocess and transform the data:
- **Data Loading**: I started by loading the sneaker sales data from a CSV file into a pandas DataFrame.
- **Date Preprocessing**: The dataset included date fields ('Order Date' and 'Release Date'), which I converted into a more standardized format (MM-DD-YYYY).
- **Feature Engineering** – Color and Sneaker Type: I added new features to the dataset based on the names of the sneakers. For instance, if a sneaker name contained a color like 'Black' or 'White', I created a corresponding feature (column) for it. Similarly, I identified different sneaker types (like 'Yeezy-Boost-350', 'Air-Jordan') from the sneaker names and created binary features for these as well.
 - Region-Based Features: Recognizing the importance of geographical influence on sneaker sales, I created features based on the buyer's region, like 'California', 'New York', etc.
 - Normalizing Shoe Size Data: I normalized the shoe sizes to understand their distribution in the dataset better. This helps in analyzing the popularity or rarity of certain shoe sizes.
 - Converting Price Fields: The 'Sale Price' and 'Retail Price' fields were formatted as strings with currency symbols. I converted them into numerical values for analysis purposes.
 - Additional Feature Computation: I computed a 'Colorful' feature, indicating the number of colors mentioned in each sneaker's name. I also calculated the 'Number of Sales' per order date to understand sales volume trends.
 - Cleaning the Data:
 - Finally, I removed unnecessary columns like 'Brand' and 'Buyer Region', which were either redundant or not required for my analysis.

#### Questions Explored: 

- **Price Premium Over Time**: Analysis shows a rising floor price of resell premiums over time.

<img width="778" alt="스크린샷 2022-07-21 오전 12 51 17" src="https://user-images.githubusercontent.com/90128775/180027876-3aa4f8e6-03b8-4135-8b16-79101c514fe1.png">

- **Shoe Size Impact on Resale Value**: Findings indicate little correlation between shoe size and resale value.

<img width="413" alt="스크린샷 2022-07-21 오전 12 56 23" src="https://user-images.githubusercontent.com/90128775/180028084-83eed031-0aca-4f1d-a93a-9a0209ce9352.png">

- Confirming that shoe size has little to do with resale value

### 2.2. Modeling & Selection 
<img width="456" alt="스크린샷 2023-11-27 오전 2 35 54" src="https://github.com/hyunstar11/hyunstar11.github.io/assets/90128775/ef3464f7-0e7e-41b4-ad02-9abfe0b5c7a2">

![스크린샷 2023-11-12 오후 11 58 40](https://github.com/hyunstar11/Portfolio/assets/90128775/b74de6d6-297d-4114-8a1f-671854fa879e)

- Results from the baseline model provided limited insights into the underlying data structure. The metrics suggested that the baseline model's predictive performance is poor, potentially no better than a model that would make random predictions or simply predict the average outcome without any input features.
- Given the possible limitations of simpler models, a progression to more complex models such as Linear Regression, Random Forest, XGBoost, LightGBM, and an Ensemble Model was considered. These models are known for their ability to handle complex datasets with sophisticated feature interactions.
- To mitigate the risk of overfitting, various feature selection methods were employed. A careful comparison between the MAE and cross-validation MAE (MAE CV) for each model was conducted, ensuring that the models not only fit the training data well but also generalize effectively to new data.
- Among the models tested, the Ensemble Model demonstrated superior performance. It achieved a lower MAE in cross-validation (20.25 for MAE CV compared to 31.90 for the Ensemble's standard MAE), which indicates that the model has strong generalization capabilities across different data subsets, an essential quality for robust predictive modeling.

### 2.3. Feature Importance 

![Feature Importance](https://github.com/hyunstar11/hyunstar11.github.io/assets/90128775/acd3c069-f267-49bc-9ac6-cc59f2b90be2)

- The chart above indicates that the features such as 'airjordan', 'Release Day' and 'yeezy350' are the most influential features in predicting the resale price of sneakers.
  
### 2.4. Interpreting Coefficients (PDP Plot)

![PDP Plot_Jordan](https://github.com/hyunstar11/hyunstar11.github.io/assets/90128775/1a6abc97-50a4-4ada-a733-a35cba9c2a1d)
- PDP Plot for the feature 'airjordan' indicates that the shoe being and Air Jordan model is positively correleated with having a higher resell price
  
![PDP_ReleaseDate](https://github.com/hyunstar11/hyunstar11.github.io/assets/90128775/f86ffcb7-8ae3-41ec-a53b-2c6c20bd3dd0)
- PDP Plot for the feature 'Release Day', on the other hand, shows a bit of variability on the outcome, as it peaks around 9th~11th days, indicating that releases on these days have a higher predicted outcome on average 
