---
layout: custom
title: Nuvilabs Food Classification Model 
permalink: /nuvilabs-food-classification/
---

# Nuvilabs Food Classification Model 

[Click Here for the Code](https://github.com/hyunstar11/Portfolio/blob/main/ML%26DL/DL/%EA%B8%89%EC%8B%9D%20%EC%8B%9D%EB%8B%A8%20%EC%B6%94%EC%B2%9C%20%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%9D%84%20%EC%9C%84%ED%95%9C%20%EC%9D%8C%EC%8B%9D%20%EB%A9%94%EB%89%B4%20%EB%B6%84%EB%A5%98%EB%AA%A8%EB%8D%B8%20%EA%B0%9C%EB%B0%9C%20/AI_10_%E1%84%8B%E1%85%B5%E1%86%B7%E1%84%80%E1%85%B2%E1%84%92%E1%85%A7%E1%86%AB_CS2_%E1%84%82%E1%85%AE%E1%84%87%E1%85%B5%E1%84%85%E1%85%A2%E1%86%B8.ipynb)

# Project Outline 

#### 1. Introduction
- 1.1. Problem Statement 
- 1.2. Description of the dataset 

#### 2. Steps
- 2.1. EDA 
- 2.2. Modeling
- 2.3. Results and Analysis 
- 2.4. Other Models Considered  

#### 3. Limitations and Suggestions for Improvement  

# 1. Introduction 
### 1.1. Problem Statement 
Nuvilabs, a Korean food-tech startup, aimed to enhance its school lunch service by integrating a diet recommendation system. The objective was to analyze diverse school meal menus using public datasets and develop a model capable of categorizing new items based on specific dietary criteria, focusing on meat types to assist school nutritionists with dietary planning.

### 1.2. Description of the dataset 
The project utilized public data from the NICE Education Information Portal, detailing school lunch menus provided by the Seoul Metropolitan Office of Education. This dataset was processed to extract unique food items, significantly reducing redundancy and enabling a focused analysis.
- Link: https://open.neis.go.kr/portal/data/service/selectServicePage.do?page=1&rows=10&sortColumn=&sortDirection=&infId=OPEN17320190722180924242823&infSeq=2

### 2. Steps

### 2.1. Data Exploration and Preprocessing
<img width="906" alt="Screenshot 2022-07-13 11:36 09 pm" src="https://user-images.githubusercontent.com/90128775/178760402-e4c9a82e-a128-4fe7-a5e4-83dcf2792653.png">

The initial data comprised over 660,000 menu items, which was refined to 5,500 unique entries through careful deduplication. Each menu item was then classified into categories based on its meat content, using a comprehensive keyword list derived from the dataset.

### 2.2. Modeling 
- #### KoBERT Model
Leveraging the KoBERT model, known for its effectiveness in Korean language tasks, I aimed to categorize food items into five distinct meat categories. This model was chosen for its sophisticated understanding of Korean syntax and semantics, and its capability for multi-class classification.

### 2.3. Results (1st case, 2nd case, KoBERT model training and results) 
- The KoBERT model's performance was evaluated against a pre-categorized set of 1,855 school lunch menus provided by Nuvilabs. Despite achieving high accuracy in certain categories, the model exhibited limitations in generalizing to menus not included in the training set. The analysis revealed the model's strengths in identifying specific meat types but highlighted challenges in classifying items without clear meat indicators.
 
- #### 1st Case 
  - Used the dataset labeled with meat types 1~5 (except for label 0, which is the case of no meat)
  - Label 0 is a non-meat category  
  - Total number of data ~ 10,000
  - **`Results`**: Returns meat type when menu name is entered 
  - Problem: 'non-meat' menus that should be labeled as 0 are labeled as meat 
  - Based on Epoch 5 **`train acc.`** = 0.999, **`test acc.`** = 0.998 

- #### 2nd Case 
  - Used the dataset labeled with meat types 0-5 (deduplication O, amplification X, sampling 10k out of 50k)
  - Results were not significantly different with amplification (to address class imbalance)  
  - As of Epoch 4, **`train acc.`** = 0.999, **`test acc.`** = 0.998 <- possible overfitting? 
  - Declared the **`Predict()`** function 
    - Menu input to the model -> Output labeling results 
  - Compared the results with 'Nuvi_Foods' data via **`Predict()`** function (labeling completed for 595/1855 meats)
    - 'Nuvi_Foods' data is a dataset of 1855 datasets that Nubi Labs has already categorized before the collaboration.
    - Words already in the word list are labeled 
    - Words not in the list were labeled as 0 (not categorized) 
    - Not as good as the 'correct' (considered as correct) Nuvi Foods data  
    - Performance comparison 
      - Pig: 50% classification compared to Nuvi_Foods 
      - Cows: 80% classification
      - Chicken: 100%
      - Duck: 80%
      - Fish: 60%
    - Result of using the function 
  
![Screenshot 2022-08-03 1 16 19 PM](https://user-images.githubusercontent.com/90128775/182523089-07a1f4d2-3994-4a4a-8856-195d4f69ea47.png)

- #### Word Cloud 
  - The most prominent words are:
    - duck, bulgogi, stir-fry sauce, smoked chicken, etc. 
    - Can also be seen through Most_Common
      
![단어리스트](https://user-images.githubusercontent.com/90128775/182775833-5879fae0-91c9-4ba5-8c71-b35f1a0519e7.png)

# 3. Limitations and Next Steps 
- The project faced challenges in model generalization and feature learning for new menu items. Future work will focus on enhancing the word list for better classification, exploring alternative models more suited to food-related tasks, and developing a more dynamic classification approach that can adapt to new menu items more effectively.

### Personal Reflection 
- This project underscored the importance of model selection and pre-processing in machine learning tasks. The experience gained from experimenting with different models and debugging provided valuable insights into the complexities of text classification, especially in the context of food menus.
