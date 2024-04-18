
## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
  ```
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/bd1324af-f47f-4d54-a05a-6699aa14369d)
```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/eccfe2e0-e213-4011-9187-1bd11162a0bd)
```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/d2fae3b3-109d-4d95-b2c5-5205e5cd32d8)
```
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/f9c1cae8-754e-4097-b6de-3700b13ae143)
```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/75072fbd-e118-4da3-986d-a32436cd9518)

```
df2=pd.concat([df2,enc],axis=1)
df2
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/a147c299-bea9-4aa6-ac02-08900a60a11b)
```
pd.get_dummies(df2,columns=["nom_0"])
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/84b3ee3c-672b-4082-b21f-c7f7431b2a8a)
```
pip install --upgrade category_encoders
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/c817945c-ed35-4364-b3b3-ed9e08a7f1c3)
```
from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
df
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/58578bf2-c0b8-4b15-8c8e-33361d94bbdf)
```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
df
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/c989221a-34ab-406e-b822-b70343249c7a)
```
dfb=pd.concat([df,nd],axis=1)
dfb
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/b00a32bd-97da-46c7-ad85-266929ea4774)
```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/95df5a37-21a9-49e3-b8ba-15b6756a0c0b)
```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/d8f3e388-95ec-444a-9d16-d8e064785968)
```
df.skew()
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/e428b1f0-3529-41e9-96ea-7933f3d2f55f)
```
np.log(df["Highly Positive Skew"])
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/e44e43e8-e4c2-4222-923b-8e703b3a90f2)
```
np.reciprocal(df["Moderate Positive Skew"])
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/c90dbabb-fa48-4d13-87c4-313c462f525f)
```
np.sqrt(df["Highly Positive Skew"])
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/3dc6d748-9a7a-4622-b1eb-0670bfac103f)
```
np.square(df["Highly Positive Skew"])
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/983509e9-045e-4d0d-92f0-fb08b2425ad0)
```
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/59b88eab-ad13-49b2-a769-5a937aad39ee)
```
df.skew()
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/212f5fb0-fecf-40e9-9e77-1873b7b683d9)
```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df
```
![image](https://github.com/Munimadhuriganji/EXNO-3-DS/assets/138849444/0451fb7c-e01a-4d57-a33c-d7d19f9b6f7a)

```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)

df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])

sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
```

## OUTPUT
![ds_exp3_1](https://github.com/Thirukaalathessvarar-S/EXNO-3-DS/assets/121166390/6632f2eb-f757-4f92-84ba-e37d1550ffd9)
![ds_exp3_2](https://github.com/Thirukaalathessvarar-S/EXNO-3-DS/assets/121166390/5a949314-8706-49e0-aa3d-7b39e891239e)
![ds_exp3_3](https://github.com/Thirukaalathessvarar-S/EXNO-3-DS/assets/121166390/58aa9bb8-8f27-4249-a398-c1089376b17d)


# RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.
       
