# EX-06 ANALYZING A DATASET WITH VARIOUS STAGES OF DATA SCIENCE
### AIM:
To Analyze a data set with Various stages of data science. &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**DATE :15-11-2024**
### ALGORITHM:
Step 1: Include the necessary python Library.<BR>
Step 2: Choose your own dataset and read it.<BR>
Step 3: Implement Data analysis using the necessary columns.<BR>
Step 4: Perform Data Preprocessing steps for the necessary columns.<BR>
Step 5: Perform Feature Engineering process for the categorical columns.<BR>
Step 6: Implement Advanced data Visualization for the columns necessary.<BR>
### PROGRAM:
```
Name: Nemaleshwar H
reg no:212223230142
```
##### Importing Libraries
```Python
import pandas as pd
from sklearn.preprocessing import LabelEncoder
from sklearn.preprocessing import MinMaxScaler
import statsmodels.api as sm
import matplotlib.pyplot as plt
```
##### Reading DataSet
```Python
df=pd.read_csv("Toyota.csv")
df
```
![387350826-b1692d7b-0ada-4867-80ae-57447c7eafb6](https://github.com/user-attachments/assets/268a1f4a-56a7-40b8-a6a7-9b475ea5ad1f)

##### Data Analysis
```Python
df.isnull().sum()
df.info()
```
![387350985-3315457f-d62f-48fe-b220-1b94d90f3b5b](https://github.com/user-attachments/assets/1b245021-ebfa-4e97-b511-a49eeba72ee5)



##### Data Preprocessing
```Python
df=df.drop(df[df['KM'] == '??'].index)
df=df.drop(df[df['HP']=='????'].index)
df=df.drop('Unnamed: 0',axis=1)
df['Doors']=df['Doors'].replace({'three':3,'four':4,'five':5}).astype(int)
df[['FuelType','MetColor']]=df[['FuelType','MetColor']].fillna(method='ffill')
df[['Age']]=df[['Age']].fillna(df['Age'].mean()).astype(int)
df[['KM','HP']]=df[['KM','HP']].astype(int)
```
![387351208-4d35e580-ae0b-4d6e-bb61-2c77a47b57b2](https://github.com/user-attachments/assets/a6fafd06-931c-401b-b99c-9db1164a5772)

##### Feature Engineering
```Python
scl=MinMaxScaler()
df[['Age']]=scl.fit_transform(df[['Age']])

le=LabelEncoder()
df['FuelType']=le.fit_transform(df['FuelType'])
```
![387351542-4c9c63c1-024a-481d-a358-fed1db050e77](https://github.com/user-attachments/assets/7fe2faa4-cf02-4161-9599-e7fa1e44866f)



##### Data Visualization
```Python
#CORRELATION MATRIX
cormat=df.corr()
plt.figure(figsize=(5, 3))
plt.imshow(cormat,cmap='coolwarm',interpolation='nearest')
plt.colorbar()
plt.xticks(range(len(cormat.columns)),cormat.columns,rotation=90)
plt.yticks(range(len(cormat.columns)),cormat.columns)
plt.title('Correlation Matrix', fontsize=16)
plt.show()

#SCATTER PLOT
plt.figure(figsize=(7, 4))
plt.scatter(df['Age'],df['Price'],alpha=0.3,color='red')
plt.title('Car Age vs Price')
plt.xlabel('Age (Years)')
plt.ylabel('Price')
plt.show()
```
![387351863-c9c6efdd-610c-467a-ba92-a28a4644377f](https://github.com/user-attachments/assets/db7dc6fc-a8a4-4421-8288-afa4c48814ef)
![387351967-e735f659-70a1-4b76-b74a-228d16af8b7d](https://github.com/user-attachments/assets/9872cfb2-a9f5-4b93-8bd5-a1618fffb93d)


### RESULT:
Thus, the analyzing the dataset with various stages of data science is implemented successfully.


