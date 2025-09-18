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
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.preprocessing import LabelEncoder

data=pd.read_csv("C:/Users/admin/Documents/AIML/SEM 5/ds/exp2/amazon.csv")
data.shape
data=data.iloc[:500,]
data.shape
data.head()
data.tail()
data.info()
data.columns
data.isnull()
data.describe()
data.isnull().sum()

plt.figure(figsize=(25, 10))
sns.heatmap(data.isnull(),cbar=False,cmap='viridis')

plt.figure(figsize=(25, 10))
sns.countplot(x='rating',data=data)

data['rating'].value_counts()

data['actual_price'] = data['actual_price'].str.replace("₹",'')
data['actual_price'] = data['actual_price'].str.replace(",",'')
data['actual_price'] = data['actual_price'].astype('float64')

sns.histplot(data['actual_price'].dropna(), kde=False, bins=40)

data.isnull().sum().sort_values(ascending = False)

data[data['rating_count'].isnull()].head()

data['rating_count'] = data['rating_count'].str.replace(',', '').astype('float64')
data['rating_count'] = data.rating_count.fillna(value=data['rating_count'].median())

plt.figure(figsize=(25, 10))
sns.heatmap(data.isnull(),cbar=False,cmap='viridis')

data.duplicated().any()

encoder=LabelEncoder()
data['category'] = encoder.fit_transform(data['category'])

data['category'].value_counts()

data['discounted_price'] = data['discounted_price'].astype(str)
data['discounted_price'] = data['discounted_price'].str.replace("₹", "", regex=True)
data['discounted_price'] = data['discounted_price'].str.replace(",", "", regex=True)
data['discounted_price'] = data['discounted_price'].astype(float)

data['discount_percentage'] = data['discount_percentage'].str.replace("%",'')
data['discount_percentage'] = data['discount_percentage'].astype('float64')

le_product_id = LabelEncoder()
le_category = LabelEncoder()
le_review_id = LabelEncoder()
le_review_content = LabelEncoder()
le_product_name = LabelEncoder()
le_user_name = LabelEncoder()
le_about_product = LabelEncoder()
le_user_id = LabelEncoder()
le_review_title = LabelEncoder()
le_img_link = LabelEncoder()
le_product_link = LabelEncoder()

data['product_id'] = le_product_id.fit_transform(data['product_id'])
data['category'] = le_category.fit_transform(data['category'])
data['review_id'] = le_review_id.fit_transform(data['review_id'])
data['review_content'] = le_review_content.fit_transform(data['review_content'])
data['product_name'] = le_product_name.fit_transform(data['product_name'])
data['user_name'] = le_user_name.fit_transform(data['user_name'])
data['about_product'] = le_about_product.fit_transform(data['about_product'])
data['user_id'] = le_user_id.fit_transform(data['user_id'])
data['review_title'] = le_review_title.fit_transform(data['review_title'])
data['img_link'] = le_img_link.fit_transform(data['img_link'])
data['product_link'] = le_product_link.fit_transform(data['product_link'])

corr_mat=data.corr()
plt.figure(figsize=(25, 25))
sns.heatmap(corr_mat,annot=True)

```
## Data description

<img width="1125" height="466" alt="image" src="https://github.com/user-attachments/assets/46f091eb-c7dc-4af1-bfd6-d2fcc23258ad" />

<img width="462" height="502" alt="image" src="https://github.com/user-attachments/assets/76bff451-ed97-4bd1-8d08-ed3b52dfeede" />

<img width="683" height="141" alt="image" src="https://github.com/user-attachments/assets/6692c6d3-60e4-405c-8e4e-d7bdc34ce70e" />

<img width="1143" height="432" alt="image" src="https://github.com/user-attachments/assets/cf06925b-af29-43f4-9b76-20f96725d006" />

<img width="1134" height="248" alt="image" src="https://github.com/user-attachments/assets/2bc28dc7-1512-41f8-acf6-b20bd16b6da9" />


## Checking Null Values

<img width="256" height="375" alt="image" src="https://github.com/user-attachments/assets/b77f062e-9f4b-4629-bf76-290cbc29ae39" />

## Heatmap of Null Values

<img width="1128" height="564" alt="image" src="https://github.com/user-attachments/assets/08fe2f64-3d3c-4f34-8fda-38cc34147fbd" />

## Count Plot for Rating

<img width="1123" height="559" alt="image" src="https://github.com/user-attachments/assets/966ced35-018f-485e-8165-4717e8e2c8e9" />

## Unique Value Count for Rating

<img width="310" height="434" alt="image" src="https://github.com/user-attachments/assets/c3486a2d-5a82-4ee0-aca8-f949b7d5b61c" />

## Histogram for Actual Price

<img width="670" height="491" alt="image" src="https://github.com/user-attachments/assets/c55e2bda-7b46-42bf-91b4-a3d40e19cf55" />

## Displaying Null Values

<img width="1132" height="278" alt="image" src="https://github.com/user-attachments/assets/9cbdc3d8-5cef-4536-9615-bc3e33cb3512" />

## Heatmap of Missing Values After Handling it

<img width="1131" height="559" alt="image" src="https://github.com/user-attachments/assets/0413305f-51cd-441c-9887-8a26b788e6ea" />

## Correlation Matrix

<img width="723" height="809" alt="image" src="https://github.com/user-attachments/assets/f2180066-d4df-450c-b4b0-e25b3eaae229" />

# RESULT
Therefore, Exploratory Data Analysis on the given data set is performed.

# SUMMARY
Amazon Sales dataset from Kaggle is uploaded and loaded in the python notebook. 
Details about the dataset are displayed using shape, head, tail, info, columns functions.
Null values is checked and it is seen that there are two null values in one column. 
Displaying the null values in a heatmap.
These null values are handled by replacing them with the median of the column.
Count plot for rating is displayed, it is infered that 4.2 rating has occurred the maximum number of times.
The column actual_price has characters like '₹' and ','. These are removed and then the values are converted to float datatype.
The column rating_count also has character ',' and it is removed then converted to float datatype.
Characters '₹' and '%' are removed from discounted_price and discount_percentage columns. They are converted to float datatype.
Now, label encoder is used on all non numerical columns.
Finally, correlation matrix is computed and displayed. 
