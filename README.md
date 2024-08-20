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
            Coding
###Data Cleaning
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/c2f8b967-4bbc-4f96-a736-e502636f0289)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/c83924d0-f161-4909-942b-d7819c490b74)

```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/1f30c5b5-ca36-4655-a169-f4be12f3df60)

```
df.dropna()
```
![image](https://github.com/user-attachments/assets/b5f0885f-9729-4250-b214-ff4a2c2974e6)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/170ba850-88b1-4cc4-8e63-89fa5f52bef3)

```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/51dc4417-ab7d-43de-88a7-753d2d5b89fe)

```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/0a9f1606-aec2-4563-85ce-eeedbe273451)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/77c2f821-bad3-4b93-ab16-10000c08f306)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/fa171d77-48fe-4865-9265-5e4d45a025e1)


###IQR(Inter Quartile Range)
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/8e9c2206-03ab-4811-a790-71b0e2170a70)

```
ir.describe()
```
![image](https://github.com/user-attachments/assets/b5fd0447-fcab-4e84-8612-302bce1415fa)

```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/fbfe44a7-90d4-4689-ab86-bf094649e30c)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/e7686fa3-ef11-456c-8ac7-0f0df1b2a2e2)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/e5cba4fd-0e12-4999-8eb9-44ca2df815bd)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/3f9bdaf0-9d46-4cc2-907e-97ec2a70aa7a)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/5b238522-a248-4aba-932a-20597f7aa129)


###Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/35ccb515-2d60-4976-8bd9-b626fc6331d7)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/9c41d724-4134-462d-b3b2-4b610f0505d7)

```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/17baf7db-23aa-4a8d-9337-558abaa31363)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/33cfa566-d6cf-40ac-8f63-94da54da97a2)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/09f1c80d-7587-4b05-ac30-3147bf7a5e9b)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/a0fae905-68eb-4f55-b472-58601ee21888)

```df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/2bc49648-74d6-445c-b8da-d29204b96f4a)

# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
