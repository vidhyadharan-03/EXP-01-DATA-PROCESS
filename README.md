# EXP-01-DATA CLEANING PROCESS
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

## Data Cleaning Process
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/varshasharon/exno1/assets/98278161/792962ae-74e2-467f-b239-66d6a3b1fad6)

```
df.head(10)
```
![image](https://github.com/varshasharon/exno1/assets/98278161/459e1284-94c5-427b-aa17-10f452c34bd9)

```
df.tail(10)
```
![image](https://github.com/varshasharon/exno1/assets/98278161/f1921df1-c8a4-4aca-b547-dd0c8aae9ab6)

```
df.info()
```
![image](https://github.com/varshasharon/exno1/assets/98278161/9d8a183f-79b0-42fc-b6b7-d790fb4321a8)

```
df.describe()
```
![image](https://github.com/varshasharon/exno1/assets/98278161/de034941-e97e-4eed-9cdb-bd8f05ce8daa)

```
df.isnull().sum()
```
![image](https://github.com/varshasharon/exno1/assets/98278161/19684aa0-d7e1-4b0f-8198-16f0cbf4e2c4)

```
df.nunique()
```
![image](https://github.com/varshasharon/exno1/assets/98278161/bdb28f9b-a0f4-418b-8847-a07427ecd9bc)

```
df['GENDER'].value_counts()
```
![image](https://github.com/varshasharon/exno1/assets/98278161/61529e50-bd7d-4f13-956f-4831bd60e499)

```
mn=df.TOTAL.mean()
mn
```
![image](https://github.com/varshasharon/exno1/assets/98278161/ad0351fe-902e-4d8a-822e-acc1f2fce67f)

```
df.TOTAL.fillna(mn,inplace=True)
df
```
![image](https://github.com/varshasharon/exno1/assets/98278161/4c6525d5-a70e-4667-bc77-b60fe386e176)

```
mins=df.M4.min()
mins
```
![image](https://github.com/varshasharon/exno1/assets/98278161/eda5aab9-ccb7-449f-9884-c53a8e3eb3fd)

```
df.M4.fillna(mins,inplace=True)
df
```
![image](https://github.com/varshasharon/exno1/assets/98278161/79201328-8bff-4ed9-b0ad-25e96c55edf1)

```
df.isnull()
```
![image](https://github.com/varshasharon/exno1/assets/98278161/aa801c39-7cfc-48d3-aa8d-c4a949b820cc)

```
df.notnull()
```
![image](https://github.com/varshasharon/exno1/assets/98278161/31413190-ee68-4fb2-bc52-2b2ba09a896f)

```
df['cd']=pd.to_datetime(df['DOB'])
df['cd']
```
![image](https://github.com/varshasharon/exno1/assets/98278161/6d711caf-12f8-4c67-8713-6e44ef92fc32)

## Outlier Detection and Removal

```
import pandas as pd
import seaborn as sns
age=[1,3,18,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/varshasharon/exno1/assets/98278161/5abe20ee-e8e3-4bef-95c8-e38cecc672f5)

```
sns.boxplot(data=af)
```
![image](https://github.com/varshasharon/exno1/assets/98278161/bb2ebe0f-4745-4854-80a9-bcb0351c95b7)

```
sns.scatterplot(data=af)
```
![image](https://github.com/varshasharon/exno1/assets/98278161/41f485af-c28f-459c-8213-03d5f05bc2b5)

```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```

![image](https://github.com/varshasharon/exno1/assets/98278161/6780ed80-f9fc-48c4-91cf-380672ed47d2)


![image](https://github.com/varshasharon/exno1/assets/98278161/210d55fa-036f-4586-be71-2edf133b3d3b)


![image](https://github.com/varshasharon/exno1/assets/98278161/6b6087c8-7759-497d-8b81-440332329687)

```
af=af[((af>=low)&(af<=high))]
af
```

![image](https://github.com/varshasharon/exno1/assets/98278161/bea4aba9-eab2-428e-8ba8-bc31b34d2a88)

```
af.dropna()
```

![image](https://github.com/varshasharon/exno1/assets/98278161/052d5468-8517-4055-a573-85f00593a3ab)



![image](https://github.com/varshasharon/exno1/assets/98278161/e977abca-633d-47e7-bb03-4118190edad9)


![image](https://github.com/varshasharon/exno1/assets/98278161/ddb7efdc-3768-42b3-ac6f-7f71a3360c2d)

```
data=[1,45,23,47,22,13,10,67,85,34,82,19,60,56,44,21,18,90,43,27,97,7,15,2,59,147,241,11,74,38,130,23,98,4,88]
df=pd.DataFrame(data)
df
```

![image](https://github.com/varshasharon/exno1/assets/98278161/9a4533cb-a11b-4bcd-85ce-4f5fa00b283d)

![image](https://github.com/varshasharon/exno1/assets/98278161/7ffa6ae4-f06b-44f8-b2e6-1aaf92ef243a)

```
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
z
```

![image](https://github.com/varshasharon/exno1/assets/98278161/f481d761-7083-4c96-be0b-043fb65ddd17)


![image](https://github.com/varshasharon/exno1/assets/98278161/6ec5fe2c-b020-44fc-8bd0-ba7b7d17ea72)


# Result
Thus the Data Cleaning Process and Detecting and Removal of Outliers is executed successfully.
