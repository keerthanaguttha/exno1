# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
## Reading the data set:
```
import pandas as pd
import seaborn as sns
import numpy as np

df=pd.read_csv("SAMPLEIDS.csv")
df
```
## Output:
![image](https://github.com/user-attachments/assets/e1414327-a310-4419-adcb-aa0061af7a95)

## Initializing id=column
```
id=df['M4']
id
```
## Output:
![image](https://github.com/user-attachments/assets/e9dd05f7-d57c-4ad9-8b10-072b884dad00)

## sns graphs:
![image](https://github.com/user-attachments/assets/66babd06-f5ac-44e7-bdd5-59fcc608a158)
![image](https://github.com/user-attachments/assets/fa3fea71-1192-40b9-8902-95208d3023a4)
![image](https://github.com/user-attachments/assets/a74935ca-09fb-4db9-b063-972dc8c81866)

## Quantile and IQR:
```
q1=id.quantile(0.25)
q2=id.quantile(0.5)
q3=id.quantile(0.75)
iqr=q3-q1
iqr
```
## Output:
![image](https://github.com/user-attachments/assets/daaa2f2f-a20d-4f29-af27-b82ed66129e5)

## Declaring bounds:
```
lower_bound=q1-1.5*iqr
upper_bound=q3+1.5*iqr
lower_bound,upper_bound
```
## Output:
![image](https://github.com/user-attachments/assets/b5e46297-99e6-45cc-852c-ca2e06447980)

## Outliers:
```
outliers=[x for x in id if x<lower_bound or x>upper_bound]
print("Outliers:",outliers)
```
## Output:
![image](https://github.com/user-attachments/assets/0d87ea97-6aa9-49e4-a93e-51e40a2bfc9b)

## Dropna function to remove any null values:
id.dropna()
## Output:
![image](https://github.com/user-attachments/assets/0263ba00-3863-4e33-993b-6dda510f08d8)

## Printing all requird values:
```
print("Q1:",q1)
print("Q2:",q2)
print("Q3:",q3)
print("IQR:",iqr)
print("lower_bound:",lower_bound)
print("upper_bound:",upper_bound)
print("Outliers",outliers)
```
## Output:

![image](https://github.com/user-attachments/assets/84e329b8-41f1-4fcc-aafa-bda61e36817f)

## Checking for any outliers at the end:
sns.boxplot(id)
## Output:

![image](https://github.com/user-attachments/assets/be54dcec-ff63-4f11-91fa-5cd40c111dd6)

## Calculating Z_score:
```
import scipy.stats as stats
import pandas as pd
import numpy as np


mean = df['M4'].mean()
std_dev = df['M4'].std()

df['z_score'] = (df['M4'] - mean) / std_dev

print(df)

z = np.abs(stats.zscore(df['M4']))
z
```
## Output:
![image](https://github.com/user-attachments/assets/2109c2d0-c973-472f-b90e-9ed5653b1da4)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
