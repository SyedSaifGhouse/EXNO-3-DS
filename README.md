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
Developed by: SYED SAIF SYED GHOUSE
Register no: 21224230286
```
```
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
# ORDINAL ENCODING
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
```
![IMG 1](https://github.com/user-attachments/assets/e4c28128-8160-4597-95af-d4f83ae38bb6)
```
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
```
![IMG 2](https://github.com/user-attachments/assets/81378c99-56f1-4d97-952b-8696473b9ea1)
```
# Label Encoder (Orders in Alphabetical order)
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
![IMG3](https://github.com/user-attachments/assets/9658e511-3987-412a-8d85-0734676074b9)
```
# ONE HOT ENCODING
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
df2=pd.concat([df2,enc],axis=1)
df
```
![image](https://github.com/user-attachments/assets/1bb46d3e-48bf-4968-8b73-66f89a2e25af)
```
pd.get_dummies(df2,columns=["nom_0"])
```
![image](https://github.com/user-attachments/assets/ee04565d-122f-4144-905b-6ef2a303b75b)
```
pip install --upgrade category_encoders
```
![image](https://github.com/user-attachments/assets/af8a70fd-22ce-43a2-91b4-0e75846c5493)
```
from category_encoders import BinaryEncoder
df = pd.read_csv("/content/data.csv")
df
```
![image](https://github.com/user-attachments/assets/810f92ea-1fb7-4ae0-a13f-354cedab1076)
```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
df
dfb=pd.concat([df,nd],axis=1)
dfb
```
![image](https://github.com/user-attachments/assets/acfd7b3b-92f0-463d-b4ad-a733585fee9c)
```
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
```
![image](https://github.com/user-attachments/assets/9c965984-f5e8-4a56-8af1-60d11e3ae3ba)
```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df
```
![437767864-10127f58-d6fc-4b2b-9509-e3e9f9416f0f](https://github.com/user-attachments/assets/60fa7342-c516-429b-af5e-025ae607016d)
```
df.skew()
```
![437767762-5b3ff74b-8862-4467-b49d-56593b84e688](https://github.com/user-attachments/assets/addfd7b5-e4b5-4b06-a9d8-ccd61c15e2b6)
```
np.log(df["Highly Positive Skew"])
```
![437767703-2f9323d9-4847-42c5-a2b9-bdbc60868e25](https://github.com/user-attachments/assets/0b34fa39-a6d7-4d76-811f-14c54d79d90d)
```
np.reciprocal(df["Moderate Positive Skew"])
```
![437767582-ab95bf6a-86c1-47b4-bdbb-6b154fc8c1b3](https://github.com/user-attachments/assets/a5d18d38-59f7-4098-aa27-8e90a458ab0e)
```
np.sqrt(df["Highly Positive Skew"])
```
![437767422-1ad2b943-3e31-4e1c-9a60-0ff896c99068](https://github.com/user-attachments/assets/33c929c9-65c4-40de-8749-833e02e2f70b)
```
np.square(df["Highly Positive Skew"])
```
![437767317-4428d192-63d9-46a5-a9d2-e798ec076a47](https://github.com/user-attachments/assets/5eb44649-3580-4231-87a3-34ddaa6a047c)
```
# POWER TRANSFORMATION
# BOX_COX
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
```
![437767288-ab2ba06a-5175-48f4-ad4e-e498319aa968](https://github.com/user-attachments/assets/8e487f92-aeb3-4963-a79b-ae8997beb459)
```
df.skew()
```
![437767222-23404996-049d-40b0-9e71-e9b6d0268ecd](https://github.com/user-attachments/assets/a2a8871a-eba2-46bf-85c8-0307b4c62236)
```
# YEO JOHNSON
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()
```
![437767148-0e976595-7a0b-4de6-b191-623b24a75c2f](https://github.com/user-attachments/assets/dea60a88-3b14-45ec-adb5-aab1479275b2)
```
# QUANTILE TRANSFORMATION
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
```
![437767095-47474b33-e694-4bd6-b16d-d8a9cb265720](https://github.com/user-attachments/assets/cf88c241-3532-4e41-874a-aa0160375a62)
```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
![437767036-1ec3f7e0-e516-427a-a378-8e9f0d3246ac](https://github.com/user-attachments/assets/1bb660bf-2ec2-4d63-bc39-00e612080502)
```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
![437766957-b7170c53-1186-4673-9258-4fe2d7e3f178](https://github.com/user-attachments/assets/9bdeb810-778d-4ecf-a419-d7b10ed8dea3)
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```
![437766819-76afa6e1-ad9e-490c-a360-aa3b77f3721d](https://github.com/user-attachments/assets/d6289f30-b163-405e-9bac-c0c47858d829)
```
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
```
![437766733-164fa91b-22d0-48f6-9a86-6a6e754fc925](https://github.com/user-attachments/assets/1684bbed-c0c7-4e94-8d43-22ca351b1a58)


# RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.
       
