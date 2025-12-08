
    Student Data Analysis
    Loading the CSV dataset

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv('StudentsPerformance.csv')  # Place the CSV in the same folder

print("\nFirst five rows (Preview of Data):")
print(df.head())

print("\nDataset info (Column types, non-null counts):")
print(df.info())

print("\nStatistical summary (Numerical and Categorical stats):")
print(df.describe(include='all'))

print("\nCount of missing values per column:")
print(df.isnull().sum())

# For simplicity, drop any rows with missing values
df = df.dropna()

print("\nCount of missing values after dropping nulls (Should be zero):")
print(df.isnull().sum())

print("\nColumn summary statistics:")
for col in ['math score', 'reading score', 'writing score']:
    print(f"{col}:")
    print(df[col].describe())

print("\nAverage scores by lunch type (Do students with standard lunch score better?):")
print(df.groupby('lunch')[['math score', 'reading score', 'writing score']].mean())

print("\nMost common demographic combinations (Top 5):")
combo = df.groupby(['gender', 'race/ethnicity', 'parental level of education', 'lunch', 'test preparation course']).size().reset_index(name='count')
print(combo.sort_values('count', ascending=False).head())

print("\nCreating total_score column (sum of all scores per student):")
df['total_score'] = df['math score'] + df['reading score'] + df['writing score']

print("\nTop 10 scoring students:")
print(df.sort_values('total_score', ascending=False).head(10)[['gender', 'race/ethnicity', 'parental level of education', 'lunch', 'test preparation course', 'math score', 'reading score', 'writing score', 'total_score']])

print("\nCorrelation matrix (How are scores related?):")
print(df[['math score','reading score','writing score']].corr())

# Visualizations
print("\nPlotting total score distribution (Histogram)...")
sns.histplot(df['total_score'], kde=True)
plt.title('Total Score Distribution')
plt.xlabel('Total Score')
plt.ylabel('Frequency')
plt.show()
