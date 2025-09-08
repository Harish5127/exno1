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
# Reading the file:
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
# Output

<img width="1009" height="809" alt="Screenshot 2025-09-08 101248" src="https://github.com/user-attachments/assets/16d54c0d-5554-4274-af88-801f86213308" />



```
df.head()
```

# Output
<img width="1003" height="249" alt="image" src="https://github.com/user-attachments/assets/fb1ec6fa-98db-4e9a-8306-81ccab7c3e88" />



```
df.tail()
```

# Output
<img width="1013" height="237" alt="image" src="https://github.com/user-attachments/assets/388fbd2a-cc05-47df-bc04-81427499b8cf" />



```
df.isnull()
```

# Output
<img width="803" height="836" alt="image" src="https://github.com/user-attachments/assets/91fd5c63-759b-4c37-894e-76f2908d0932" />



```
df.isnull().sum()
```

# Output
<img width="164" height="571" alt="Screenshot 2025-08-27 201718" src="https://github.com/user-attachments/assets/b5185c5a-f7c0-46c3-9d76-7fdb5532604e" />


```
df.isnull().any()
```

# Output
<img width="194" height="571" alt="image" src="https://github.com/user-attachments/assets/45b6b57f-31d1-492c-80b1-a4037546e11e" />


```
df.dropna(axis=0)
```

# Output
<img width="1054" height="559" alt="image" src="https://github.com/user-attachments/assets/b1a22af4-c3ed-41d9-a605-982e1f238304" />


```
df.fillna(2)
```

# Output
<img width="1019" height="855" alt="image" src="https://github.com/user-attachments/assets/7c68897c-0d7d-4168-a5d0-62f0273b387d" />


```
df.fillna(method='ffill')
```

# Output
<img width="1012" height="856" alt="image" src="https://github.com/user-attachments/assets/18789853-cb5b-4b8f-a547-c42d3f89bd3c" />


```
df.fillna(method='bfill')
```

# Output
<img width="1011" height="855" alt="image" src="https://github.com/user-attachments/assets/a096446b-09b4-4236-93bd-0c47ca39f56b" />


```
ir=pd.read_csv("iris.csv")
ir
```

# Output
<img width="677" height="515" alt="image" src="https://github.com/user-attachments/assets/367d26cd-274b-490b-abd9-ae8b431654b1" />


```
ir.describe()
```

# Output
<img width="615" height="367" alt="image" src="https://github.com/user-attachments/assets/c087ed60-7187-4766-87a6-b4871949e92e" />


```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

# Output
<img width="707" height="579" alt="image" src="https://github.com/user-attachments/assets/9468e6b2-b675-4cd4-9059-812f38978e9d" />


```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```

# Output
<img width="65" height="43" alt="image" src="https://github.com/user-attachments/assets/294e3793-ace0-4717-848c-70c9e1f99200" />


```
bound=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
bound['sepal_width']
```

# Output
<img width="196" height="260" alt="image" src="https://github.com/user-attachments/assets/fc4b233b-969d-4a0b-90ca-7997fc4cbbcf" />


```
debound=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
debound
```

# Output
<img width="688" height="516" alt="image" src="https://github.com/user-attachments/assets/d103fcaa-3e78-4bad-837d-44fd9ef85def" />


```
sns.boxplot(x='sepal_width',data=debound)
```

# Output
<img width="700" height="574" alt="image" src="https://github.com/user-attachments/assets/a92a4aa7-40dc-4395-96b4-e56d50309d8a" />


```
import scipy.stats as stats
import numpy as np
z=np.abs(stats.zscore(ir['sepal_width']))
z
```

# Output
<img width="715" height="667" alt="image" src="https://github.com/user-attachments/assets/f15410a5-9e74-4d7d-8e22-ddf4e4c11fe3" />


```
ir1=ir[z<3]
ir1
```

# Output
<img width="665" height="519" alt="image" src="https://github.com/user-attachments/assets/bedf21e5-26a6-468c-bf93-dd61e1fb2856" />

# Result
Thus, we have read the given data and performed data cleaning and saved the cleaned data to a file successfully.
