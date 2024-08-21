# Market_Campaign
This project involves the analysis of a marketing campaign dataset. The analysis includes data exploration, visualization, and some basic statistics.

Table of Contents
Overview
Data Description
Data Exploration
Visualizations
Conclusion
Overview
In this project, we explore a dataset containing information about customers' demographics and their response to various marketing campaigns. The goal is to derive insights that could help in understanding customer behavior.

Data Description
The dataset contains the following columns:

ID: Unique identifier for each customer
Year_Birth: Year of birth of the customer
Education: Education level of the customer
Marital_Status: Marital status of the customer
Income: Yearly income of the customer
Kidhome: Number of small children in customer's household
Teenhome: Number of teenagers in customer's household
Dt_Customer: Date of customer enrollment
Recency: Number of days since the last purchase
MntWines: Amount spent on wine
MntFruits: Amount spent on fruits
MntMeatProducts: Amount spent on meat products
MntFishProducts: Amount spent on fish products
MntSweetProducts: Amount spent on sweet products
MntGoldProds: Amount spent on gold products
NumDealsPurchases: Number of purchases made with a discount
NumWebPurchases: Number of purchases made through the company’s website
NumCatalogPurchases: Number of purchases made using a catalog
NumStorePurchases: Number of purchases made directly in stores
NumWebVisitsMonth: Number of visits to the company’s website in the last month
AcceptedCmp3: 1 if customer accepted the offer in the 3rd campaign, 0 otherwise
AcceptedCmp4: 1 if customer accepted the offer in the 4th campaign, 0 otherwise
AcceptedCmp5: 1 if customer accepted the offer in the 5th campaign, 0 otherwise
AcceptedCmp1: 1 if customer accepted the offer in the 1st campaign, 0 otherwise
AcceptedCmp2: 1 if customer accepted the offer in the 2nd campaign, 0 otherwise
Complain: 1 if customer complained in the last 2 years
Z_CostContact: Cost per contact (constant)
Z_Revenue: Revenue per contact (constant)
Response: 1 if customer accepted the offer in the last campaign, 0 otherwise
Data Exploration
Initial Data Loading
python
Copy code
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import warnings
warnings.filterwarnings('ignore')

# Load the dataset
df = pd.read_csv('/content/drive/MyDrive/marketing_campaign.csv')

# Display the first few rows of the dataset
df.head(5)
Data Summary
python
Copy code
# Summary statistics
df.describe()

# Data types and non-null values
df.info()

# Checking the shape of the dataset
df.shape

# Checking for null values
df.isnull().sum()

# Fill missing values with 0
df.fillna(0, inplace=True)

# Re-check for null values
df.isnull().sum()

# Checking for duplicate rows
df.duplicated().sum()
Data Exploration
python
Copy code
# List of columns
df.columns

# Number of unique values per column
df.nunique()

# Unique values in 'Year_Birth' column
df['Year_Birth'].unique()

# Statistical description of 'Year_Birth'
df['Year_Birth'].value_counts()
df['Year_Birth'].min()
df['Year_Birth'].max()
df['Year_Birth'].mean()
df['Year_Birth'].median()
df['Year_Birth'].mode()
df['Year_Birth'].std()
Visualizations
Marital Status Distribution
python
Copy code
# Pie chart for 'Marital_Status'
marital_status_counts = df['Marital_Status'].value_counts()

plt.figure(figsize=(7, 7))
plt.pie(marital_status_counts, labels=marital_status_counts.index, autopct='%1.1f%%', startangle=140)
plt.title('Distribution of Marital Status')
plt.show()
Count Plot of Marital Status
python
Copy code
plt.figure(figsize=(10, 6))
ax = sns.countplot(data=df, x='Marital_Status', palette='Set3')
plt.title('Count of Marital Statuses')
plt.xlabel('Marital Status')
plt.ylabel('Count')
plt.xticks(rotation=45)

for p in ax.patches:
    ax.annotate(f'{p.get_height()}',
                (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='bottom', fontsize=12, color='black', xytext=(0, 5),
                textcoords='offset points')

plt.show()
Count Plot of Education Levels
python
Copy code
plt.figure(figsize=(9, 7))
ax = sns.countplot(data=df, x='Education', palette='Set2')
plt.title('Count of Education Levels')
plt.xlabel('Education Level')
plt.ylabel('Count')
plt.xticks(rotation=45)

for p in ax.patches:
    ax.annotate(f'{p.get_height()}',
                (p.get_x() + p.get_width() / 2., p.get_height()),
                ha='center', va='center', fontsize=12, color='black', xytext=(0, 5),
                textcoords='offset points')

plt.show()
Average Year of Birth by Education Level
python
Copy code
plt.figure(figsize=(10, 6))
sns.barplot(data=df, x='Education', y='Year_Birth', palette='viridis')
plt.title('Average Year of Birth by Education Level')
plt.xlabel('Education Level')
plt.ylabel('Average Year of Birth')
plt.xticks(rotation=45)

plt.show()
Conclusion
This project provides an overview of the initial data exploration and visualization of a marketing campaign dataset. Further analysis could involve more advanced statistical techniques and predictive modeling to derive deeper insights.

