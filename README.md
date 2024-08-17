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

DATA CLEANING
```
import pandas as pd
df = pd.read_csv('/content/SAMPLEIDS.csv')
df
```
![image](https://github.com/user-attachments/assets/186d4517-f77f-4feb-bb54-55cd29431d93)

df.isnull().sum()

![image](https://github.com/user-attachments/assets/5159ed94-b36a-43e4-9abe-e8cf3cd304cc)

df.isnull().any()

![image](https://github.com/user-attachments/assets/4cf4ed0b-c88a-4460-a8bc-dddac11e1678)

df.dropna()

![image](https://github.com/user-attachments/assets/8511ba10-92cd-4250-a988-b0909a74e0fb)

df.fillna(0)

![image](https://github.com/user-attachments/assets/ce2f688f-1889-44ba-b341-aa8fb2c8e6f9)

df.fillna(method = 'ffill')

![image](https://github.com/user-attachments/assets/03bb3f1e-2706-4d75-abf4-b1dda1bf5063)

df.fillna(method = 'bfill')

![image](https://github.com/user-attachments/assets/397abb07-46c1-466c-9b99-a9ccfe5d3529)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/4a71f020-ea66-4d89-a560-0a102fbb16d8)

 df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})

 ![image](https://github.com/user-attachments/assets/5c86f251-639f-45ce-b484-8de47e4f6566)

 ```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/f82a2cee-68af-4ff6-b432-94b43af3137b)

 ir.describe()

 ![image](https://github.com/user-attachments/assets/9f9a5abb-47d4-4db7-bc85-c632937512d5)

 ```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/40a0a1a0-08f8-4532-ad24-6569723adc5c)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/78791c70-0672-4783-b53c-19cd584ba6f1)

```
 rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
 rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/637a8947-46fa-42b3-a7b9-95b387563f57)

```
 delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
 delid
```
![image](https://github.com/user-attachments/assets/735d3c64-c975-47ea-83ae-8184e8b50cab)

sns.boxplot(x='sepal_width',data=delid)

![image](https://github.com/user-attachments/assets/27d88393-9527-4fb8-9391-6afd0852b2ee)

Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/4887f9e9-24f5-4e17-bcc9-ec2d6ce70720)

```
 df = pd.read_csv("heights.csv")
 q1 = df['height'].quantile(0.25)
 q2 = df['height'].quantile(0.5)
 q3 = df['height'].quantile(0.75)
 iqr = q3-q1
 iqr
```
![image](https://github.com/user-attachments/assets/6bcc55ce-d6ca-41eb-80a4-e877dc3f746d)
```
 low = q1- 1.5*iqr
 low
```
![image](https://github.com/user-attachments/assets/ea16d330-cdfa-4d46-b107-86d9abd732e7)

```
 high = q3 + 1.5*iqr
 high
```
![image](https://github.com/user-attachments/assets/432d09ab-4119-4bc2-be99-ff52342593d7)

```
 df1 = df[((df['height'] >=low)& (df['height'] <=high))]
 df1
```
![image](https://github.com/user-attachments/assets/ceac4eb8-0509-4ff4-a13f-a57a16bea8f1)

```
 z = np.abs(stats.zscore(df['height']))
 z
```
![image](https://github.com/user-attachments/assets/4bd0c17c-61d4-421c-b9fc-615872cf4aae)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/d030d459-b876-4cc8-91f4-610f9c7feadc)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
