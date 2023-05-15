# Ex-10-Data-Science-Process-on-Complex-Dataset
## AIM 
To Perform Data Science Process on a complex dataset and save the data to a file. 
## ALGORITHM
### STEP 1
Read the given Data
### STEP 2 
Clean the Data Set using Data Cleaning Process 
### STEP 3 
Apply Feature Generation/Feature Selection Techniques on the data set 
### STEP 4 
Apply EDA /Data visualization techniques to all the features of the data set
## PROGRAM
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
df = pd.read_csv("world_pop.csv")

# Data Cleaning
# Check for missing values
print(df.isnull().sum())

# Remove duplicates, if any
df = df.drop_duplicates()

# Handling missing values
# Assuming missing values as 0 (if appropriate)
df = df.fillna(0)

# Feature Selection
# Select columns for analysis
cols_to_keep = ['country', 'year_1960', 'year_1970', 'year_1980', 'year_1990', 'year_2000', 'year_2010', 'year_2020']
df_selected = df[cols_to_keep].copy()

# Feature Generation
# Calculate average population growth rate
df_selected['Average_Growth_Rate'] = df_selected.iloc[:, 1:-1].mean(axis=1).pct_change() * 100

# Exploratory Data Analysis (EDA)
# Compute the total population for each year
df_selected['Total_Population'] = df_selected.iloc[:, 1:].sum(axis=1)

# Line plot of population over the years
plt.figure(figsize=(10, 6))
plt.plot(df_selected['year_1960'], df_selected['Total_Population'])
plt.xlabel('Year')
plt.ylabel('Total Population')
plt.title('World Population Over the Years')
plt.show()

# Line plot of average population growth rate over the years
plt.figure(figsize=(10, 6))
plt.plot(df_selected['year_1960'], df_selected['Average_Growth_Rate'])
plt.xlabel('Year')
plt.ylabel('Average Growth Rate (%)')
plt.title('Average Population Growth Rate Over the Years')
plt.show()

# Bar plot of top 10 countries by population in 2020
df_selected['Total_Population_2020'] = df_selected['year_2020']
top_10_countries = df_selected.nlargest(10, 'Total_Population_2020')
plt.figure(figsize=(10, 6))
sns.barplot(x='Total_Population_2020', y='country', data=top_10_countries, palette='viridis')
plt.xlabel('Population in 2020')
plt.ylabel('Country')
plt.title('Top 10 Countries by Population in 2020')
plt.show()
```
## OUTPUT
![image](https://github.com/Siddarthan999/Ex-10-Data-Science-Process-on-Complex-Dataset/assets/91734840/5ff36765-6e47-4542-bd0d-66c303de103c)
![image](https://github.com/Siddarthan999/Ex-10-Data-Science-Process-on-Complex-Dataset/assets/91734840/886a43c7-c69f-4b7e-9750-5e57c00137f4)
![image](https://github.com/Siddarthan999/Ex-10-Data-Science-Process-on-Complex-Dataset/assets/91734840/97515ce7-1d81-4dec-84c6-3c7226fb45dc)

## RESULT
Thus, to Perform Data Science Process on a complex dataset and save the data to a file has been performed successfully.
