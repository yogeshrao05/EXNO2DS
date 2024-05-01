# EX-02 Exploratory Data Analysis

## AIM:
  To perform Exploratory Data Analysis on the given data set.
      
## EXPLANATION:
 The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
## ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
### Developed by: YOGESH RAO S D
### Register no: 212222110055
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns  
df=pd.read_csv("titanic_dataset.csv")
df
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/1f4f577b-f5e3-4319-9da6-810bb3aace2b)


```py
df.info()
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/200a4ebc-f651-48eb-8264-041aebc88921)


```py
df.shape
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/69371368-3ced-4319-8f4e-fcbf78e1a7c7)


```py
df.set_index("PassengerId",inplace=True)
df.describe()
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/2896cfba-fb60-4c31-89a7-081436c6253b)


```py
df.shape
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/79f63e92-df32-4cd3-8058-27ca3bc42559)


### Categorical data analysis
```py
df.nunique()
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/55e3d278-e798-48f8-b6e4-df16fb0ae2a2)


```py
df["Survived"].value_counts()
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/6178a162-2d6c-420e-8acc-f099c97b6dd6)

```py
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/c225e93f-3430-4035-b39c-d5b4db4ff75f)

```py
sns.countplot(data=df,x="Survived")
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/4ee40260-565e-4436-9a65-2b5e6a424248)

```py
df
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/bbfc2df8-164e-4ed8-b075-1623ec0f0670)

```py
df.Pclass.unique()
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/d81daba1-6e35-4370-b1bb-11f296d62aa4)


```py
df.rename(columns={'Sex':'Gender'},inplace=True)
df
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/2d0fdd66-0e6e-49f9-b640-33c248e3c7b6)


### Bivariate Analysis
```py
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/c4a6e13b-4b3f-4b09-bf26-ba105701d819)


```py
sns.catplot(x="Survived",hue="Gender",data=df,kind="count")
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/0b3600b9-828b-4cd5-8eeb-2919add72f7a)


```py
df.boxplot(column="Age",by="Survived")
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/8e8540f8-61f3-4b63-93f8-1f075e2d6ed3)

```py
sns.scatterplot(x=df["Age"],y=df["Fare"])
```

![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/6f218041-2cbe-423f-9537-27970c338d83)


```py
sns.jointplot(x="Age",y="Fare",data=df)
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/98c7591d-de9d-4687-8a8f-2859b32b925d)


### Multivariate Analysis
```py
fig, ax1 = plt.subplots(figsize=(8,5))
plt = sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/28b066d7-2542-41b8-8ed0-8a4fc037e7d8)


```py
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
```

![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/62f9d2df-51a1-487a-bd55-b820486f9b29)


# Co-relation
```py
corr=df.corr()
sns.heatmap(corr,annot=True)
```

![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/0b15ea25-7106-4f4f-97c8-149c28ebf6d6)


```py
sns.pairplot(df)
```
![image](https://github.com/DINESH18032004/EXNO2DS/assets/119477784/acff34d4-dbc5-43bd-8653-796044c1b7bf)


## RESULT
We have performed Exploratory Data Analysis on the given data set successfully.
