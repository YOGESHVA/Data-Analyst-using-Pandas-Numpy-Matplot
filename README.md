📊 Data Analyst Practice – Pandas & NumPy

Project Overview

This repository contains hands-on Data Analyst practice using Python, Pandas, and NumPy. It focuses on exploring, cleaning, transforming, validating, and analyzing real-world-style E-commerce and Hospital datasets.

The project is designed to strengthen practical skills for an entry-level Data Analyst role.

Technologies Used

- Python
- Pandas
- NumPy
- Google Colab

import pandas as pd
import numpy as np

Project Structure

Data-Analyst-Practice/
│
├── da_practise_.py
└── README.md

Setup

1. Clone or download this repository.
2. Open "da_practise_.py" in a Python environment or Google Colab.
3. Install the required libraries if needed:

pip install pandas numpy

4. Load a dataset with Pandas:

df = pd.read_csv("dataset.csv")

Dataset Details

The practice includes:

- E-commerce dataset
- Hospital dataset

The datasets are used to practice data loading, inspection, cleaning, transformation, validation, and exploratory analysis.

Key Analyses

Data Inspection

The following Pandas methods are used:

df.head()
df.tail()
df.shape
df.info()
df.describe()
df.columns
df.dtypes
df.nunique()

Data Cleaning

Missing values:

df.isna()
df.isna().sum()

Examples:

df["City"] = df["City"].fillna("Unknown")
df["Age"] = df["Age"].fillna(df["Age"].mean())

Duplicate records:

df.duplicated().sum()
df = df.drop_duplicates()

Text cleaning:

df["City"] = df["City"].astype(str)
df["City"] = df["City"].str.title()
df["City"] = df["City"].str.strip()

Categorical Analysis

Categorical columns include:

- Gender
- City
- Payment Method
- Diagnosis
- Department
- Insurance Provider
- Discharge Status

df["Gender"].unique()
df["City"].nunique()

Numerical Analysis

Numerical columns include:

- Age
- Treatment Cost
- Heart Rate
- Length of Stay
- Satisfaction Score

df["Treatment_Cost"].mean()
df["Treatment_Cost"].sum()
df["Treatment_Cost"].median()
df["Treatment_Cost"].min()
df["Treatment_Cost"].max()
df["Treatment_Cost"].count()

Outlier Detection

Outliers are identified using the IQR method:

Q1 = df["Treatment_Cost"].quantile(0.25)
Q3 = df["Treatment_Cost"].quantile(0.75)
IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

outliers = df[
    (df["Treatment_Cost"] < lower_bound) |
    (df["Treatment_Cost"] > upper_bound)
]

Date and Time Analysis

df["Visit_Date"] = pd.to_datetime(df["Visit_Date"])

df["Visit_Year"] = df["Visit_Date"].dt.year
df["Visit_Month"] = df["Visit_Date"].dt.month_name()
df["Day"] = df["Visit_Date"].dt.day
df["Day_Name"] = df["Visit_Date"].dt.day_name()
df["Hour"] = df["Visit_Date"].dt.hour
df["Quarter"] = df["Visit_Date"].dt.quarter

Feature Engineering

df["Cost_Per_Day"] = (
    df["Treatment_Cost"] / df["Length_of_Stay"]
)

df["Age_Group"] = pd.cut(
    df["Age"],
    bins=[0, 18, 40, 60, 100],
    labels=["Child", "Young Adult", "Middle Age", "Senior"]
)

df["Stay_Category"] = pd.cut(
    df["Length_of_Stay"],
    bins=[0, 3, 7, 30, float("inf")],
    labels=["Short", "Medium", "Long", "Very Long"]
)

df["Cost_Per_Age"] = (
    df["Treatment_Cost"] / df["Age"]
)

Filtering

df[df["Age"] > 60]
df[df["Treatment_Cost"] > 50000]
df[df["Length_of_Stay"] > 7]
df[df["Gender"] == "Female"]
df[df["Department"] == "Cardiology"]
df[df["Satisfaction_Score"] < 3]

Grouping and Aggregation

df.groupby("Department")["Treatment_Cost"].sum()
df.groupby("Department")["Treatment_Cost"].mean()
df.groupby("Gender")["Patient_ID"].count()
df.groupby("Gender")["Age"].mean()

Multiple aggregations:

df.groupby(["Department", "Gender"]).agg(
    Patient_count=("Patient_ID", "count"),
    Average_Treatment_Cost=("Treatment_Cost", "mean")
)

Sorting and Ranking

df.sort_values("Treatment_Cost")
df.sort_values("Treatment_Cost", ascending=False)

df.sort_values(
    ["Department", "Treatment_Cost"],
    ascending=False
)

Top and bottom records:

df.nlargest(5, "Treatment_Cost")
df.nsmallest(5, "Treatment_Cost")
df.nlargest(10, "Length_of_Stay")

Data Validation

df[df["Length_of_Stay"] < 0]
df[df["Age"] < 0]
df[df["Heart_Rate"] > 200]

Basic Python String Practice

name = "Python is easy"
words = name.split()
rev = words[::-1]
s = " ".join(rev)
words = "".join(reversed(name))

Learning Outcomes

Through this project, I am developing the ability to:

- Load and inspect datasets using Pandas
- Work with DataFrames and Series
- Handle missing values and duplicates
- Clean categorical and text data
- Perform categorical and numerical analysis
- Detect outliers using the IQR method
- Analyze date and time data
- Create calculated features
- Filter and sort records
- Group and aggregate data
- Identify top and bottom records
- Validate data quality
- Apply NumPy and Pandas to practical analysis tasks

Skills Practiced

Skill| Practice
Python| ✅
Pandas| ✅
NumPy| ✅
Data Loading| ✅
Data Inspection| ✅
Data Cleaning| ✅
Missing Value Handling| ✅
Duplicate Removal| ✅
Categorical Analysis| ✅
Numerical Analysis| ✅
Outlier Detection| ✅
Date and Time Analysis| ✅
Feature Engineering| ✅
Filtering| ✅
GroupBy and Aggregation| ✅
Sorting| ✅
Data Validation| ✅

Future Improvements

Planned extensions include:

- Creating visualizations with Matplotlib and Seaborn
- Practicing advanced Pandas operations
- Combining multiple datasets
- Developing business-focused analysis questions
- Building an end-to-end exploratory data analysis project
- Creating dashboards with Power BI
- Connecting Python analysis with SQL

Project Purpose

This project is part of my Data Analyst learning and practice journey. Its goal is to build a strong foundation in Python, Pandas, and NumPy through practical work with real-world-style datasets.

Note

This is a practice project, not a production application. The Python file contains hands-on exercises completed while learning and applying Data Analyst concepts.
