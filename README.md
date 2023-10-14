# ODD2023-Datascience-Ex-04
## AIM:
To perform Multivariate EDA on the given data set.
## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
## ALGORITHM:
### STEP 1:
Import the built libraries required to perform EDA and outlier removal.
### STEP 2:
Read the given csv file
### STEP 3:
Convert the file into a dataframe and get information of the data.
### STEP 4:
Return the objects containing counts of unique values using (value_counts()).
### STEP 5:
Plot the counts in the form of Histogram or Bar Graph.
### STEP 6:
Use seaborn the bar graph comparison of data can be viewed.
### STEP 7:
Find the pairwise correlation of all columns in the dataframe.corr()
### STEP 8:
Save the final data set into the file.
## PROGRAM:
```
Name : KARTHICK P
Register Number : 212222100021
```
### SuperStore.csv file:
```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
data=pd.read_csv("/content/SuperStore (1).csv")
df=pd.DataFrame(data)
df.head()
df.info()
df.describe()
df.isnull().sum()
df['Postal Code']=df['Postal Code'].fillna(df['Postal Code'].mode()[0])
df.isnull().sum()

sns.scatterplot(x=df['Region'],y=df['Sales'])

states=df.loc[:,["State","Sales"]]
states=states.groupby(by=["State"]).sum().sort_values(by="Sales")
plt.figure(figsize=(12,5))
plt.xticks(rotation=90)
sns.barplot(x=states.index,y="Sales",data=states)

states=df.loc[:,["Ship Mode","Row ID"]]
states=states.groupby(by=["Ship Mode"]).sum().sort_values(by="Row ID")
sns.barplot(x=states.index,y="Row ID",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("SHIP MODE")
plt.ylabel=("ROW ID")
plt.show()

sns.boxplot(x=df['Ship Date'],y=df['Sales'])
sns.displot(df, x="Region", hue="Category")
df.corr()
sns.heatmap(df.corr(),annot=True)
```

## OUTPUT:
## SUPERSTORE:
### DATA FRAME OF SUPERSTORE

![273436811-04da1d1e-4305-4abf-825d-effe43521a9f](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/de61042d-0b7f-4a14-b337-ba101874647c)


### Data information
![273436436-c443883f-8cf6-4f5f-b4ee-eef401730a59](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/804f4c37-ec0c-4dd1-b715-c12f08cf2db1)

### Data describing

![273436443-51b07f4d-77eb-4482-a5c8-fe68ec112bc2](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/d6cb02eb-52ff-4d61-99ba-4783ed0f5959)

### Sum of null values

![273436449-f0958e9d-36fe-4745-93cf-3885d67e855b](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/376da7b7-93ab-476e-a5ff-c1a1c64dcc2c)

### After removing null values
![273436456-c29779d4-e3d8-4391-a59a-b65b8cc25e9f](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/653bcca5-bf0c-4a1b-8c71-43bbf0b7caae)


### Scatter plot
![273436476-cd55d233-5f25-4451-9eac-1270557c5c14](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/fd79a334-0c2c-4c45-8b3a-fcc34a0bd227)


### Bar plot

![273436479-a1ba9121-6cc4-4a13-93cc-c884491218dd](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/d969f081-805b-4d4c-a732-27887a8d6610)

![273436485-1fb3fb81-f2a7-4c34-9cc5-84dc2d8a9501](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/a65dead8-0db3-4098-94f1-0ab537d12631)



### Box plot
![273436511-92fa18b4-46e9-4e75-abbf-208ea3dea94c](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/28320c6c-942a-471e-bf7e-079166eb0f76)


### Dist plot
![273436520-6582fd54-083b-482a-9670-40ce01d38e7f](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/4acfb9bd-e72c-4caf-a134-2136f3e5482a)

### Correlation coefficient interpretation
![273436530-80d97153-1912-40ca-9a7c-875c63ae7486](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/04f992b6-dca5-4842-966f-7a38a8a70712)

### Heat map
![273436537-4204da31-bbfc-4051-842a-bd3b8e0a3cbb](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/72cf0665-4f83-4c3c-aed6-982d3afb1c16)


## DIABETES

### diabetes.csv file:
```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
df=pd.read_csv("/content/diabetes.csv")
df
df.describe()
df.info
df.isnull().sum()

sns.scatterplot(x=df['Glucose'],y=df['BloodPressure'])

sns.scatterplot(x=df['Glucose'], y=df['BloodPressure'], hue=df['Outcome'])

Age=df.loc[:,["Age","BMI"]]
Age=Age.groupby(by=["Age"]).sum().sort_values(by="BMI")
plt.figure(figsize=(12,5))
plt.xticks(rotation=90)
sns.barplot(x=Age.index,y="BMI",data=Age)

Age=df.loc[:,["BloodPressure","Glucose"]]
Age=Age.groupby(by=["BloodPressure"]).sum().sort_values(by="Glucose")
sns.barplot(x=Age.index,y="Glucose",data=Age)
plt.xticks(rotation = 90)
plt.xlabel=("BloodPressure")
plt.ylabel=("Glucose")
plt.show()

sns.boxplot(x=df['DiabetesPedigreeFunction'],y=df['Insulin'])

sns.displot(df, x="Glucose", hue="Outcome")

df.corr()

sns.heatmap(df.corr(),annot=True)
```

### DATA FRAME FOR DIABETES

![273436553-d4d5c50b-015f-4d2a-bb29-39370301a9ce](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/665047fb-3302-4905-b488-a4c9599b7526)

### Data information

![273436559-e267215f-0108-4655-8a4e-3e3e6117f257](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/a680fe04-890a-4d1c-81cf-839393ce2c05)

### Data describing
![273436564-13ff73a9-97ea-485f-a799-45edb43d6e6a](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/c421e0ff-1b93-4c3b-ba7d-900a4e3d2bc6)


### Sum of null values

![273436571-c1e2954b-2fe8-4e63-935f-fcf168d03e20](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/11ef7688-90fe-4aa1-966e-a3f448a923b8)

### Scatter plot
![273436579-7e7e1712-2305-4cb4-afcb-ea4f42e0c9a7](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/e81e1aad-a67d-425c-9032-034cf9bfa624)
![273436583-bb3781f1-5fa4-4194-b16c-03ba3a662fb4](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/e7b7ab7e-3295-49a9-a733-67d6783cc3f5)

### Bar plot
![273436590-c93a6716-2d38-4268-aeae-b3fee90409fd](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/598b60c0-44d4-4587-adb8-17df497f5821)
![273436599-10b80b0f-af9a-4d60-8284-22d682c724e3](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/f544532d-3b21-44fa-960d-f6bc5f21d4e1)

### Box plot
![273436607-aaf4bb9d-1541-4ad0-b5ef-a389d7bd0adb](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/6f68bf74-9ae9-45b9-a337-ba039fd23d0e)

### Dist plot
![273436614-a8b71f2b-e474-4f80-a354-8e6e1aa15062](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/24b7f2d6-c4f2-40f5-a54d-4b229f577dbd)

### correlation coefficient interpretation

![273436624-5b89025c-0179-4741-934c-6ef20fe8e3df](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/f822df95-9b58-4578-aca5-1aa3494a49fc)


### Heat map
![273436634-71fa8088-79a1-4896-853b-cccb9a47d230](https://github.com/KRISHNARAJ-D/ODD2023-Datascience-Ex-04/assets/119559695/66089101-5e41-4a62-bcb4-a74d0ce7f843)

## RESULT:
Thus we have read the given data and performed the multivariate analysis with different types of plots.
