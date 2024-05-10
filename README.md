# Diwali-sales-Analysis
Performed data cleaning and manipulation Performed exploratory data analysis (EDA) using pandas, matplotlib and seaborn libraries 
"""Diwali Sales Analysis .ipynb

Original file is located at https://colab.research.google.com/drive/1W3UdToWglkiF6hyKJ4k8PrSo6QtZpsUa """

import numpy as np import pandas as pd import matplotlib.pyplot as plt import seaborn as sns df=pd.read_csv('/content/Diwali Sales Data.csv',encoding='unicode_escape') df

"""# Data cleaning"""

df.shape

df.drop(['unnamed1','Status'],axis=1,inplace=True)

df.info()

df.head(10)

df.info()

df.isnull()

df.sum().isnull()

pd.isnull(df).sum()

df.dropna(inplace=True),

df.shape

df.head() df.rename(columns={'Marital_Status':'Marrage status'},inplace=True)

df.head()

df[['Age','State','Amount']].describe()

"""# **Exploratory Data Analysis **(EDA)*"""

df.columns

ax=sns.countplot(x='Gender',data=df) for bars in ax.containers: ax.bar_label(bars)

"""# Group By"""

sales_gen=df.groupby(['Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount',ascending=False)

sns.barplot(x='Gender',y='Amount',data=sales_gen)

"""# > For above graph we can se the most buyers are female and the parchsing power of female is greater as compare to male

Age group
"""

df.columns

sns.countplot(data=df ,x='Age Group',hue='Gender')

"""# >above graph show that in every age group female is greater than man and most of female in 26-35 age group"""

sales_age = df.groupby(['Age Group'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)

sns.barplot(x = 'Age Group',y= 'Amount' ,data = sales_age)

"""#From above graphs we can see that most of the buyers are of age group between 26-35 yrs female"""

df.columns

total no.of order from top 10 state
sales_state=df.groupby(['State'],as_index=False)['Orders'].sum().sort_values(by='Orders',ascending=False).head(10)

sns.barplot(x='State',y='Orders',data=sales_state)

sns.set(rc={'figure.figsize':(15,5)})

sns.barplot(x='State',y='Orders',data=sales_state)

"""# In above graph show top 10 state according to their order in which most of the order came from ◼ Uttar pradesh > maharastra > karnataka > delhi > madhya pradesh > andhara pradesh > himachal pradesh > kerala > haryana >gujrat

"""

ax = sns.countplot(data = df, x = 'Marrage status')

sns.set(rc={'figure.figsize':(7,5)}) for bars in ax.containers: ax.bar_label(bars)

df.columns

sales_state = df.groupby(['Marrage status', 'Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)

sns.set(rc={'figure.figsize':(6,5)}) sns.barplot(data = sales_state, x = 'Marrage status',y= 'Amount', hue='Gender')

"""# in above graph we can see most of the buyers are married (women) and they have high parchasing power"""

occoupation
sns.set(rc={'figure.figsize':(20,5)}) ax = sns.countplot(data = df, x = 'Occupation')

for bars in ax.containers: ax.bar_label(bars)

sv=df.groupby(['Occupation','Gender'])['Amount'].mean().reset_index()

sns.barplot(data=sv,x='Occupation',y='Amount',hue='Gender')

"""# in the above graph we can see every occupatin filled by male and female

product
"""

sns.set(rc={'figure.figsize':(20,5)}) ax = sns.countplot(data = df, x = 'Product_Category')

for bars in ax.containers: ax.bar_label(bars)

"""# in the above graph we can see most of parchasing product clothes"""

sales_state = df.groupby(['Product_Category'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False).head(10)

sns.set(rc={'figure.figsize':(20,5)}) sns.barplot(data = sales_state, x = 'Product_Category',y= 'Amount')

"""From above graphs we can see that most of the sold products are from Food, Clothing and Electronics category

top 10 most sold products (same thing as above)
"""

fig1, ax1 = plt.subplots(figsize=(12,7)) df.groupby('Product_ID')['Orders'].sum().nlargest(10).sort_values(ascending=False).plot(kind='bar')

sales_state = df.groupby(['Product_ID'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)

sns.set(rc={'figure.figsize':(20,5)}) sns.barplot(data = sales_state, x = 'Product_ID',y= 'Orders')
