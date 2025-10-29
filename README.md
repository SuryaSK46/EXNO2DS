# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

df=pd.read_csv(r"C:\Users\acer\Downloads\titanic_dataset (4).csv")
dp=pd.DataFrame(df)
print(dp.head(5))
dp.info()
print(dp.isnull().sum())
#data cleaning
dp['Age'].fillna(dp['Age'].median(),inplace=True)
dp['Embarked'].fillna(dp['Embarked'].mode()[0],inplace=True)
dp.drop('Cabin',axis=1,inplace=True)
#univrate Analysis
sns.countplot(x='Survived',data=dp)
plt.title("Survival Count")
plt.show()
```
![alt text](https://github.com/ALLEN-AJ2007/EXNO2DS/blob/main/Screenshot%202025-10-14%20135559.png)
```
sns.histplot(dp['Age'],bins=30,kde=True)
plt.title('Age Distribution')
plt.show()
```
![alt text](https://github.com/ALLEN-AJ2007/EXNO2DS/blob/main/Screenshot%202025-10-14%20135908.png)
```
sns.countplot(x='Pclass',data=dp)
plt.title('Passenger Class Distribution')
plt.show()
```
![alt text](https://github.com/ALLEN-AJ2007/EXNO2DS/blob/main/Screenshot%202025-10-14%20135921.png)
```
#Bivariate Analysis

sns.barplot(x='Pclass',y='Survived',data=dp)
plt.title("Survival Rate by Sex")
plt.show()
```
![alt text](https://github.com/ALLEN-AJ2007/EXNO2DS/blob/main/Screenshot%202025-10-14%20135944.png)
```
sns.barplot(x='Pclass',y='Survived',data=dp)
plt.title("Survival rate by Class")
plt.show()
```
![alt text](https://github.com/ALLEN-AJ2007/EXNO2DS/blob/main/Screenshot%202025-10-14%20135956.png)
```
sns.boxplot(x='Survived',y='Age',data=dp)
plt.title("Age vs Survival")
plt.show()
```
![alt text](https://github.com/ALLEN-AJ2007/EXNO2DS/blob/main/Screenshot%202025-10-14%20140033.png)
```
#correlation Heatmap

plt.figure(figsize=(12,7))
sns.heatmap(dp.corr(),annot=True,cmap='coolwarm')
plt.title('Feature Correlation')
plt.show()
```
![alt text](https://github.com/ALLEN-AJ2007/EXNO2DS/blob/main/Screenshot%202025-10-14%20140058.png)


# RESULT
The EDA revealed that survival on the Titanic was strongly influenced by gender, passenger class, and whether the passenger was traveling alone.
