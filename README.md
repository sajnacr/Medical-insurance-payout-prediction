# Medical-insurance-payout-prediction

### Table of contents
---
- [Project Overview](#Project-Overview)
- [Data Sources](#Data-Sources)
- [Tools](#Tools)
- [EDA](#EDA)
- [Data Preprocessing](#Data-Preprocessing)
- [Model](#Model)
- [Conclusion](#Conclusion)

### Project Overview
---
This study aim to find a correlation between medical expenses and different factors using insurance data of different people with attributes such as smoking, age, number of children, region and BMI.  
The main objectives were:  
- Predict the future medical expenses of subjects based on certain features.
- Identifying the factors affecting the medical expenses of the subjects based on the model output.

### Data Sources
---
The data set used here is the medical cost personal dataset from Kaggle which consists of people’s anonymous information and annual insurance premiums given to them. 
[Link](https://www.kaggle.com/datasets/harshsingh2209/medical-insurancepayout)
The dataset contains 1338 rows and 7 columns. The attributes in this dataset as follows: 

|COLUMN|DESCRIPTION|
|------|-----------|
|AGE|Age of primary beneficiary|
|SEX|Insurance contractor gender. Female /Male|
|BMI|Body mass index, provides an understanding of body.|
|CHILDREN|Number of children covered by insurance|
|SMOKER|If insurance primary smokes|
|REGION|The beneficiary’s residential area in the US| 
|CHARGES|Individual medical costs billed by health insurance.|

### Tools
---
Utilized Python libraries such as Pandas, Numpy, Seaborn, Matplotlib, Scikit-learn for Data analysis and model building.

### EDA
---
1. Used a pie chart to plot the Smoker Column, as the Smoker column has only two values: Yes and No.found 20.5% of the 
subjects are smokers and 79.5 % are non-smoker.
2. Using a Bar plot to show the subjects having children ranging from 0 to 5 and it has been computed and observed from the count plot that those who are having no children are highest in number.
3. Scatter plots have been used to show the variation of expenses with age. It has been noticed that with an increase in age the medical expenses have increased but some people are of higher age but have lower medical expenses. It was observed that the expense and age have a linear relationship.
4. Also plotted the scatterplot between BMI and expenses and it has been noticed that most of the data is situated at the bottom of the trend line indicating that people with high, low, and medium BMI can have low expenses, which is an 
irregular pattern, but if we take a look at the trend line we can notice that people with high BMI, their medical expense will be high, so we can conclude that for people with high BMI the expenses may be increased but in rare case.
5. plotted the box plot between the children and expenses and it has been noticed people with a greater number of children the expense is more, as with more children parents need to take care of the health of all of them rather those 
who have no children or one child, but as there is very a smaller number of people who are having more than 2 or 3 children so for them the expense is almost same so we capped them. The people with 2 or 3 children have the highest expenses among them. 
6. Also seen the relationship between smokers and expenses through box plots and it has been noticed that for smokers the expense is much high than nonsmokers as it is obvious because smoking is injurious to health so smokers 
are likely to have health issues than nonsmokers causing their medical expenses to increase.

### Data Preprocessing
---
1. The variable age and BMI are continuous variables, the variables sex, smoker and region are categorical variables. 
The Expenses column is the target column and the rest others are independent columns.
2. There are no missing values in the data set.
3. The skewness is greater than one for the target column,log transformation has been applied to make this distribution normal so it doesn’t create any problem while predicting.
4. Converted the categorical variables into dummy variables.
5. Data splitting and feature scaling.

### Model
---
1. **Huber Regression**
Since the data is right skewed and have outliers in the data, first i adopted huber regression for model building.

By using this method, we got the model as: 
Y= 8.697727 + 0.04620422 X1 + 0.9194101 X2 + -0.05833624 X3 + 1.57307141    X4 + -0.01352694 X5 
 
Y = Charges,  
X1 = BMI,  
X2 = AGE,  
X3 = SEX,  
X4 = SMOKER, 
X5 = REGION

The coefficients of variables and their respective t-values and p-values are given in the following table: 

|VARIABLES|COEFFICIENTS|t-value|p-value|
|---------|------------|-------|-------|
|X1|0.04620422002882137|3.584063230903335|0.0| 
|X2|0.9194140051382169|38.93819599803457|0.0| 
|X3|-0.0583362401081861|-3.611021640544449|2.0| 
|X4|1.5730714104254961|34.184906811040086|0.0| 
|X5|-0.0135269353033179|-0.948509594437264|1.658|

By analyzing p-values we can see that p values of X3 and X5 are greater than 0.05. Hence, accept the null hypothesis that their regression coefficients are zero.it implies that the variables Sex and region are insignificant. 
And if we look at t- values it’s clear that absolute t values for age and smoker are higher. so, conclude that Age and Smoker variables are more significant than others. 

For checking model performance, wcomputed R-squared score and Root mean square error (RMSE).

R-squared (R2) score: 0.5165  
It implies that approximately 51.6% of the variance in the target variable (charges) is explained by the independent variables (features).  

Root Mean Squared Error (RMSE): 8419.59  
The RMSE represents the average deviation of the predicted values from the true values.  

The model is not performing well in prediction.So for better prediction i tried Random forest regression.

2. **Random Forest Regression**

R-squared (R2) score: 0.8663733659172578  
Root Mean Squared Error (RMSE): 4426.388227280083  
Mean absolute Error (MAE: 2149.95465459179  

- 86% of the variance in the target variable (charges) is explained by the independent variables (features).
- mean of the charges column is 13270,and our MAE is 2123.implies there is 15% error in the model prrediction.

## Conclusion
---
- The Most Important Factor to Predict the Medical Expenses of a subject is Smoking Behaviour and Age, that means, smoking 
is Bad for Health, as already know that and which inevitably increases medical expenses as due to smoking one is likely to fall ill more than the nonsmokers. 
- With increasing of age, one needs to take some more care and precautions for your health as with the increase of age health becomes fragile so they go for frequent medical check-up, likely to fall ill quickly as with the increase of age immunity falls so they adopt measures to stay healthy by taking medicines and engaging in some physical activities like jogging, walking, Yoga which causes an increase of medical expenses. 
- for the medical expense prediction, random forest regression performed much better than huber regression model.
