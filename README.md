![image](https://github.com/user-attachments/assets/72305de1-44f2-4ae9-ad03-2994b082d9a0)# Exno:1
Data Cleaning Process

### Name: SATHYAA R
### Reg Number: 212223100052

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

```
import pandas as pd
data=pd.read_csv("SAMPLEIDS.csv")
data
```

![image](https://github.com/user-attachments/assets/f83515e4-a20e-44bc-9dec-2e992c3ef9f4)


```
data.head(9)
```

![image](https://github.com/user-attachments/assets/0da5d7c8-6d2c-4dd4-bd47-951f7e2872a5)


```
data.tail(7)
```

![image](https://github.com/user-attachments/assets/42e52a60-985d-4d0d-a63b-2106c966e31b)


```
data.isnull()
```

![image](https://github.com/user-attachments/assets/216ebe4a-4fe7-4622-b41a-8d5050262cf8)


```
data.notnull()
```

![image](https://github.com/user-attachments/assets/2c833aab-7b0d-4bd6-8096-d9ffc4f83d82)


```
data.isnull().sum()
```

![image](https://github.com/user-attachments/assets/03f54554-ee9b-430d-8d80-ef19e56307ef)


```
data.isnull().any()
```

![image](https://github.com/user-attachments/assets/b27a27bd-742b-471b-9407-4bf95abb8aa9)


```
data.dropna()
```

![image](https://github.com/user-attachments/assets/a919f6f5-1465-4e98-8cda-08a3c0de0039)


```
data.fillna(0)
```

![image](https://github.com/user-attachments/assets/ae160184-c703-466d-a34e-2344d9b262a0)


```
data.fillna(method = 'ffill')
```

![image](https://github.com/user-attachments/assets/ef53f890-ccd3-48e0-b29f-2c2afe15cf54)


```
data.fillna(method = 'bfill')
```

![image](https://github.com/user-attachments/assets/16275a86-e9da-42de-bf11-81e1464c56cf)


```
data_dropped = data.dropna()
data_dropped
```

![image](https://github.com/user-attachments/assets/441c21e6-86b7-4a53-a50f-b58f95d3fd84)


```
data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```

![image](https://github.com/user-attachments/assets/23d83b93-da6a-4467-9c93-494c651c271d)


```
ir = pd.read_csv("iris.csv")
ir
```

![image](https://github.com/user-attachments/assets/4cf06bd6-efb5-444f-a416-9529f7c605ab)


```
ir.describe()
```

![image](https://github.com/user-attachments/assets/358ac61e-444a-452b-b758-ca5e8202933e)


```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/user-attachments/assets/ff16f848-efe7-4468-a14c-354a1e2660fd)


```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```

![image](https://github.com/user-attachments/assets/0716aad0-7977-4445-8d5e-e26f75f011c3)


```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```

![image](https://github.com/user-attachments/assets/ebe1ee90-5977-47e9-adca-ceb524ecd50e)


```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid
```

![image](https://github.com/user-attachments/assets/13e88310-64b3-41a8-8a57-c0426de3f124)


```
sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/user-attachments/assets/a10773d2-7edd-4c48-95e2-a6d7748bd219)


```
import matplotlib.pyplot as plt
import numpy as np
import scipy.stats as stats
```

```
dataset=pd.read_csv("heights.csv")
dataset
```

![image](https://github.com/user-attachments/assets/6fb10e73-0254-4852-b906-e6e3357761aa)


```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```

```
iqr = q3-q1
iqr
```

![image](https://github.com/user-attachments/assets/ac57517f-a786-4601-a756-efc11ad1ce7b)


```
low = q1- 1.5*iqr
low
```

![image](https://github.com/user-attachments/assets/a0cf84d8-0ebc-4d3f-9565-7f077fdf7e46)


```
high = q3 + 1.5*iqr
high
```

![Screenshot 2025-03-04 105505](https://github.com/user-attachments/assets/d8ea31b0-82b3-45cc-aa11-a03bf0460336)


```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![image](https://github.com/user-attachments/assets/1f79cba1-14e9-4cc7-9745-fb9257e15c4d)


```
z = np.abs(stats.zscore(df['height']))
z
```

![image](https://github.com/user-attachments/assets/35d42d31-c944-440f-8d6a-d30b6b4dfa32)


```
df1 = df[z<3]
df1
```

![image](https://github.com/user-attachments/assets/708e3975-aec6-4c8d-ba4d-a661039b8e13)


# Result

Thus to read the given data and perform data cleaning and save the cleaned data to a file done successfully.
