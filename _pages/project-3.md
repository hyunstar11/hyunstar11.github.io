layout: custom
title: Nuvilabs Food Classification Model 
permalink: /project-3/
---
# Nuvilabs Food Classification Model 

# Project Outline 

#### 1. Introduction
- 1.1. Why the topic?  
- 1.2. Description of the dataset 

#### 2. Project Progress 
- 2.1. EDA 
- 2.2. Modeling
- 2.3. Modeling results and analysis 
- 2.4. Other models considered  

#### 3. Limitations and Future Development 

# 1. Introduction 
### Why the topic? 

- Nubilab, a Korean food-tech startup, wanted to develop a diet recommendation system in addition to its current school lunch platform and provide it to nutritionists. 
- The goal was to provide insights into food trends by including foods that have recently appeared in school lunches in the recommendation system.  
- To do this, I wanted to develop a model that labels new menu items according to the different criteria. 
- For this project, I classified the 'meat' category, which is one of the important criteria for diet recommendation (classifying which meat is included in the menu).   

### Description of the dataset 

- Public data provided by the NICE Education Information Portal (school lunch data from the Seoul Metropolitan Office of Education)  
- Extracted the food names from the lunch menus, removed the duplicates

-링크: https://open.neis.go.kr/portal/data/service/selectServicePage.do?page=1&rows=10&sortColumn=&sortDirection=&infId=OPEN17320190722180924242823&infSeq=2

### 2. Project Progress 
### 2.1. EDA 

- Removed duplicate menus (660,000 -> 5.5K) 
  - Use the final 5.5K data 

<img width="906" alt="Screenshot 2022-07-13 11:36 09 pm" src="https://user-images.githubusercontent.com/90128775/178760402-e4c9a82e-a128-4fe7-a5e4-83dcf2792653.png">

- Went through the menus in the NEIS food data and created a Word List for each meat category (proceed with hand labeling) 
  - Word List: Organizeed a word list for each meat type 
    - Identified the keywords for each category after going through the menus in the diets 

### 2.2. Modeling 
- #### KoBERT 
  - Hypothesis: Categorize new food names with the KoBERT model 
  - Features
    - Follows the BERT structure
    - Predicts the next sentence word given the previous sentence/word 
    - Convenience: Ground truth + multiclassification can be done simultaneously 
  - Advantages: Korean-specific pre-learning model
  - Classification criteria: 5 types of meat classification (based on Nubi Lab's internal criteria)

### 2.3. Modeling process and results (1st case, 2nd case, KoBERT model training and results) 
- To check the model performance, I compared each model's accuracy with the dataset (1855 lunch menus) that Nubilab has already classified. 

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

- To conclude, the KoBERT model is not a good model for learning the characteristics of food menus. 
- The classification of the menus in the word list is easily accomplished, but when the model is run on a new menu that is not in the list, it does not perform well. 

- #### Word Cloud 
  - The most prominent words are 
    - duck, bulgogi, stir-fry sauce, smoked chicken, etc. 
    - Can also be seen through Most_Common

ㄴㅇㄹㄴㅇㄹㅇㄴㄹ

### 2.4. Other models considered 
- Models I tried and debugged, but couldn't implement due to the time constraints of the project
- #### Autokeras 
  - Why I considered it: AutoML program. Convenience UP
  - Pros: Built-in TextClassfier. Separate Tokenization (X).
    - Can do its own neural network search + Can handle many formats, be it text or images. 
  - Cons: Poor performance with specialized data or small data + Can't classify Korean text 

- #### Naive Bayes Classifier 
  - Classification technique based on Bayes' theorem (first trained on 'historical' data)
  - Why: Traditionally used classifier for text categorization 
  - Pros: Easy to implement + doesn't require a lot of data  
    - Tokenization via KoNLPy - a package that provides a Korean corpus 
- Result: No problems with tokenization, but errors occurred when specifying tokenized data as train data for the model.

# 3. Limitations and Future Developments 

### Limitations 
- Poor feature learning for food words; poor classification for new menu items  

### Strengths 
- Performance can be improved by updating the word list
- KoBERT is too complex a model to use for this classification task; need to see if there is a model that learns better on the word 'food' itself than KoBERT. 
- Filter and label in a different way than KoBERT (direct labeling) to create a model that recommends a diet based on the results. 

### Personal reflection 
- Modeling and debugging took time away from getting the desired results 
- Approach: I wish I had reviewed the available models before trying this or that one.
  - The models were new to me, so I was more inclined to try them out first.   
- I think there is definitely something to learn from this project in terms of trying out different models.
