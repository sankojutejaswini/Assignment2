# Assignment2
Assignment2_700726283
1.Numpy:
Using NumPy create random vector of size 15 having only Integers in the range 1-20.

1. Reshape the array to 3 by 5
2. Print array shape.
3. Replace the max in each row by 0


import numpy as np
arr = np.random.randint(1,20,15)
print("original array")
print(arr)
print("\nAfter reshaping the Array")
arr1 = arr.reshape(3,5)
print(arr1)
for i in arr1:
    i[np.where(i==i.max())]=0
print("\n",arr1)

Pandas
1. Read the provided CSV file ‘data.csv’. https://drive.google.com/drive/folders/1h8C3mLsso-R-sIOLsvoYwPLzy2fJ4IOF?usp=sharing
2. Show the basic statistical description about the data.
3. Check if the data has null values. a. Replace the null values with the mean
4. Select at least two columns and aggregate the data using: min, max, count, mean.
5. Filter the dataframe to select the rows with calories values between 500 and 1000.
6. Filter the dataframe to select the rows with calories values > 500 and pulse < 100.
7. Create a new “df_modified” dataframe that contains all the columns from df except for “Maxpulse”.
8. Delete the “Maxpulse” column from the main df dataframe
9. Convert the datatype of Calories column to int datatype.
10. Using pandas create a scatter plot for the two columns (Duration and Calories).

import pandas as pd

df = pd.read_csv('C:\\Users\\Rams\Downloads\\data.csv')
df.head(10)

df.describe()


df.isnull().any()

df.fillna(df.mean(), inplace=True)
print(df.head(20))

df.agg({'Duration':['min','max','count','mean'],'Pulse':['min','max','count','mean']})


df.loc[(df['Calories']>500)&(df['Calories']<1000)]


df.loc[(df['Calories']>500)&(df['Pulse']<100)]


df_modified = df.loc[:,df.columns!='Maxpulse']
print(df_modified)

del df['Maxpulse']


df.head()

df.dtypes


df['Calories'] = df['Calories'].astype(np.int64)
df.dtypes

a = df.plot.scatter(x='Duration',y='Calories',c='darkblue')
print(a)
Matplotlib
1. Write a Python programming to create a below chart of the popularity of programming Languages.
2. Sample data: Programming languages: Java, Python, PHP, JavaScript, C#, C++ Popularity: 22.2, 17.6, 8.8, 8, 7.7, 6.7

import matplotlib.pyplot as plt
# Data to plot
languages = 'Java', 'Python', 'PHP', 'JavaScript', 'C#', 'C++'
popularity = [22.2, 17.6, 8.8, 8, 7.7, 6.7]
colors = ["#1f77b4", "#ff7f0e", "#2ca02c", "#d62728", "#9467bd", "#8c564b"]
# explode 1st slice
explode = (0.1, 0, 0, 0,0,0)  
# Plot
plt.pie(popularity, explode=explode, labels=languages, colors=colors,
autopct='%1.1f%%', shadow=True, startangle=140)

plt.axis('equal')
plt.show()


