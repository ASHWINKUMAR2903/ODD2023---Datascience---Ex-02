# Ex02-Outlier
# AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them
# ALGORITHM:
## STEP 1:
Read the given data
## STEP 2:
Get the information about the data
## STEP 3:
Detect the outlier using IQR method and Zscore.
## step 4:
Remove the outliers.
## STEP 5:
Plot the datas using boxplot.
# PROGRAM:
DEVELOPED BY : A.ASHWIN KUMAR
REG.NO : 212222100006
### You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,
### (1) Remove outliers using IQR
### (2) After removing outliers in step 1, you get a new dataframe.
```
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns

data=pd.read_csv("/content/bhp.csv")
df=pd.DataFrame(data)

sns.boxplot(data=df)
sns.scatterplot(data=df)

q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
low=q1-1.5*iqr
high=q3+1.5*iqr

dff=df[((df>=low)&(df<=high))]
dff

df1_new=df[((df>=q1-1.5*iqr)&(df<=q3+1.5*iqr))]
df1_new

sns.boxplot(data=df1_new)
sns.scatterplot(data=df1_new)
```
![1](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/ca675b0a-4158-4e4c-b6f6-f09e7d7d6b30)
![2](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/9d29a5c1-d188-4107-8b51-d520fd5fbbab)
![3](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/b7d98e29-79aa-43c2-bf09-0e51e81e5d97)
![4](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/79725711-1725-475c-bf85-adcc0538b397)
![5](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/4e2f0733-baec-4b13-acdf-bb767f2e0a15)
![6](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/5edd5326-d658-4a36-a7fc-b058cc49b8c6)

### (3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result
```
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns

data=pd.read_csv("/content/bhp.csv")
df=pd.DataFrame(data)

z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)

outlier2=df[(z_score>=3)]
print(outlier2)

newdata2.shape

sns.boxplot(x="price_per_sqft",data=newdata2)
```
![1](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/7c1effc3-16d8-4aa8-9f7e-7aeeea30809e)
![2](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/93750615-0ba6-4158-9f79-516e40e1f642)
![3](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/a1b91c41-f0da-49bc-a6fe-524fe2fda97b)

### (4) for the data set height_weight.csv find the following
### (i) Using IQR detect height outliers and print them
```
import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns

data=pd.read_csv("/content/height_weight.csv")
df=pd.DataFrame(data)
df.shape
df.describe()
df.info()

sns.boxplot(data=df)
sns.scatterplot(data=df)

sns.boxplot(x='height',data=df)

q1h=df['height'].quantile(0.25)
q2h=df['height'].quantile(0.5)
q3h=df['height'].quantile(0.75)
iqr_height=q3h-q1h
l_h=q1h-1.5*iqr_height
u_h=q3h+1.5*iqr_height

outlier_h=df[(df['height']<l_h)|(df['height']>u_h)]
print(outlier_h)

newdata_h=df[(df['height']>=l_h) & (df['height']<=u_h)]
print(newdata_h)

sns.boxplot(x='height',data=newdata_h)
```
![1](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/f3194507-b379-4c92-8d1f-4863909e2e0d)
![2](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/ed932a5a-fc47-4ba8-8f97-ab9dbe22d307)
![3](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/624ce8b4-4b5d-4dec-8c22-3a46ea3e25b5)
![4](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/a0229c05-084e-47d0-bb51-1747aa35e995)
![5](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/028826d8-0acf-47f6-b0b0-371011fda0ba)
![6](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/697610ef-2d5a-47b2-9fdf-5d1dcef583ba)

### (ii) Using IQR, detect weight outliers and print them
```
sns.boxplot(x='weight',data=df)

q1w=df['weight'].quantile(0.25)
q2w=df['weight'].quantile(0.5)
q3w=df['weight'].quantile(0.75)
iqr_weight=q3w-q1w
l_w=q1w-1.5*iqr_weight
u_w=q3w+1.5*iqr_weight

outlier_w=df[(df['weight']<l_w)|(df['weight']>u_w)]
print(outlier_w)

newdata_w=df[(df['weight']>=l_w) & (df['weight']<=u_w)]
print(newdata_w)

sns.boxplot(x='weight',data=newdata_w)
```
![6 1](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/90aa92f5-3fb4-4b9a-a624-c00c6cc7b2ec)
![6 2](https://github.com/ASHWINKUMAR2903/ODD2023---Datascience---Ex-02/assets/119407186/8971303d-92b7-414a-b8ee-6f0aed0eb7b3)
# RESULT :
the given datasets are read and outliers are detected and are removed using IQR and Z-score methods.
