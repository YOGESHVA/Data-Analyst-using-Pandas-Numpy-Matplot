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

# 📊 Matplotlib & Seaborn – Data Visualization

This repository contains my learning and practice of **Matplotlib** and **Seaborn** for **Data Analysis and Exploratory Data Analysis (EDA)**.

I learned how to create different types of charts, understand when to use each visualization, compare categories, identify trends, understand distributions, analyze relationships, and visualize multiple variables.

---

# 📚 Table of Contents

1. [Introduction to Data Visualization](#1-introduction-to-data-visualization)
2. [Matplotlib](#2-matplotlib)
3. [Basic Matplotlib Structure](#3-basic-matplotlib-structure)
4. [Figure and Subplot](#4-figure-and-subplot)
5. [Comparison Charts](#5-comparison-charts)
6. [Line Plot](#6-line-plot)
7. [Bar Plot](#7-bar-plot)
8. [Grouped Bar Plot](#8-grouped-bar-plot)
9. [Stacked Bar Plot](#9-stacked-bar-plot)
10. [Horizontal Bar Plot](#10-horizontal-bar-plot)
11. [Distribution](#11-distribution)
12. [Histogram](#12-histogram)
13. [Box Plot](#13-box-plot)
14. [Violin Plot](#14-violin-plot)
15. [Relationship Charts](#15-relationship-charts)
16. [Scatter Plot](#16-scatter-plot)
17. [Multiple Line Plot](#17-multiple-line-plot)
18. [Composition Charts](#18-composition-charts)
19. [Pie Chart](#19-pie-chart)
20. [Donut Chart](#20-donut-chart)
21. [Area Chart](#21-area-chart)
22. [Stacked Area Chart](#22-stacked-area-chart)
23. [Heatmap](#23-heatmap)
24. [3D Visualizations](#24-3d-visualizations)
25. [Seaborn](#25-seaborn)
26. [Seaborn Count Plot](#26-seaborn-count-plot)
27. [Seaborn Bar Plot](#27-seaborn-bar-plot)
28. [Seaborn Histogram](#28-seaborn-histogram)
29. [Seaborn Box Plot](#29-seaborn-box-plot)
30. [Seaborn Violin Plot](#30-seaborn-violin-plot)
31. [Seaborn Scatter Plot](#31-seaborn-scatter-plot)
32. [Hue](#32-hue)
33. [Seaborn Heatmap](#33-seaborn-heatmap)
34. [Pair Plot](#34-pair-plot)
35. [Joint Plot](#35-joint-plot)
36. [Pivot Table + Heatmap](#36-pivot-table--heatmap)
37. [Advanced EDA](#37-advanced-eda)
38. [Chart Selection Cheat Sheet](#38-chart-selection-cheat-sheet)
39. [Learning Outcome](#39-learning-outcome)

---

# 1. Introduction to Data Visualization

**Data Visualization** means representing data using charts, graphs, and other visual elements.

Instead of looking at hundreds or thousands of rows of data, visualization helps us understand:

* Trends
* Comparisons
* Distributions
* Relationships
* Patterns
* Outliers
* Categories
* Changes over time

### Example

Suppose we have sales data:

```text
Year     Sales
2022      70
2023      95
2024     135
2025     150
2026     120
```

A chart can make the change in sales much easier to understand.

---

# 2. Matplotlib

**Matplotlib** is a Python library used to create data visualizations.

The most commonly used module is:

```python
import matplotlib.pyplot as plt
```

`pyplot` provides functions for creating and displaying charts.

---

# 3. Basic Matplotlib Structure

A basic Matplotlib chart usually follows this structure:

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [10, 20, 15, 30, 25]

plt.plot(x, y)

plt.title("Simple Plot")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")

plt.show()
```

### Important functions

| Function        | Purpose               |
| --------------- | --------------------- |
| `plt.plot()`    | Line plot             |
| `plt.bar()`     | Bar chart             |
| `plt.scatter()` | Scatter plot          |
| `plt.hist()`    | Histogram             |
| `plt.pie()`     | Pie chart             |
| `plt.title()`   | Chart title           |
| `plt.xlabel()`  | X-axis label          |
| `plt.ylabel()`  | Y-axis label          |
| `plt.legend()`  | Display legend        |
| `plt.show()`    | Display chart         |
| `plt.figure()`  | Create figure         |
| `plt.subplot()` | Create multiple plots |

---

# 4. Figure and Subplot

## Figure

A **figure** is the overall canvas where charts are displayed.

```python
plt.figure(figsize=(12, 8))
```

`figsize` controls the width and height of the figure.

---

## Subplot

`subplot()` allows us to display multiple charts in one figure.

Syntax:

```python
plt.subplot(rows, columns, position)
```

Example:

```python
plt.subplot(2, 3, 1)
```

Meaning:

```text
2     → rows
3     → columns
1     → first position
```

Example:

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.plot([1, 2, 3], [10, 20, 30])
plt.title("Line Plot")

plt.subplot(2, 2, 2)
plt.bar(["A", "B", "C"], [10, 20, 30])
plt.title("Bar Plot")

plt.subplot(2, 2, 3)
plt.scatter([1, 2, 3], [20, 10, 30])
plt.title("Scatter Plot")

plt.subplot(2, 2, 4)
plt.hist([10, 20, 20, 30, 30, 30])
plt.title("Histogram")

plt.tight_layout()
plt.show()
```

`plt.tight_layout()` helps prevent charts and labels from overlapping.

---

# 5. Comparison Charts

**Comparison** means comparing values between different categories.

Common comparison charts:

* Bar chart
* Horizontal bar chart
* Grouped bar chart
* Line chart

### Example

```text
Product       Sales
Laptop         500
Mobile         800
Earphones      300
```

A bar chart can clearly compare these products.

---

# 6. Line Plot

A **line plot** is mainly used to show **trends or changes**, especially over time.

### Example

```python
import matplotlib.pyplot as plt

years = [2022, 2023, 2024, 2025, 2026]
sales = [70, 95, 135, 150, 120]

plt.plot(years, sales)

plt.title("Sales Trend")
plt.xlabel("Year")
plt.ylabel("Sales")

plt.show()
```

### Usage

Use a line chart when you want to understand:

* Trends
* Growth
* Decline
* Changes over time

### Easy memory

**Line = Trend**

---

# 7. Bar Plot

A **bar plot** is used to compare different categories.

```python
import matplotlib.pyplot as plt

products = ["Laptop", "Mobile", "Earphone"]
sales = [500, 800, 300]

plt.bar(products, sales)

plt.title("Product Sales")
plt.xlabel("Product")
plt.ylabel("Sales")

plt.show()
```

### Usage

Use a bar chart for:

* Product comparison
* Sales comparison
* Employee comparison
* Category comparison

### Easy memory

**Bar = Comparison**

---

# 8. Grouped Bar Plot

A grouped bar chart compares multiple groups across the same categories.

```python
import matplotlib.pyplot as plt

products = ["Laptop", "Mobile", "Tablet"]

online = [500, 800, 400]
offline = [300, 600, 350]

x = range(len(products))

plt.bar(x, online, width=0.4, label="Online")
plt.bar([i + 0.4 for i in x], offline, width=0.4, label="Offline")

plt.xticks([i + 0.2 for i in x], products)

plt.xlabel("Product")
plt.ylabel("Sales")
plt.title("Online vs Offline Sales")

plt.legend()
plt.show()
```

### Usage

Useful for comparing:

```text
Online vs Offline
Male vs Female
2025 vs 2026
Region A vs Region B
```

---

# 9. Stacked Bar Plot

A stacked bar chart displays multiple categories on top of each other.

```python
import matplotlib.pyplot as plt

products = ["Laptop", "Mobile", "Tablet"]

online = [500, 800, 400]
offline = [300, 600, 350]

plt.bar(products, online, label="Online")
plt.bar(products, offline, bottom=online, label="Offline")

plt.title("Total Sales")
plt.xlabel("Product")
plt.ylabel("Sales")

plt.legend()
plt.show()
```

### Usage

Useful when we want to see:

**Total + contribution of each category**

---

# 10. Horizontal Bar Plot

A horizontal bar chart uses `barh()`.

```python
import matplotlib.pyplot as plt

products = ["Laptop", "Mobile", "Earphone"]
sales = [500, 800, 300]

plt.barh(products, sales)

plt.title("Product Sales")
plt.xlabel("Sales")
plt.ylabel("Product")

plt.show()
```

### Usage

Horizontal bars are useful when category names are long.

---

# 11. Distribution

**Distribution** means understanding how data values are spread.

For example:

```text
Age:
18, 20, 21, 21, 22, 25, 30, 35, 40
```

We can ask:

* Where are most values?
* Are values spread out?
* Are there unusual values?
* Is the data concentrated in one area?

Common distribution charts:

* Histogram
* Box plot
* Violin plot

### Easy memory

**Distribution = How data is spread**

---

# 12. Histogram

A histogram shows the distribution of numerical data using bins.

```python
import matplotlib.pyplot as plt

ages = [18, 20, 21, 21, 22, 25, 25, 28, 30, 35, 40]

plt.hist(ages, bins=5)

plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Frequency")

plt.show()
```

### What is `bins`?

Bins divide numerical values into groups.

```python
plt.hist(ages, bins=5)
```

means the data is divided into approximately 5 intervals.

### Usage

Use histogram to understand:

* Frequency
* Distribution
* Concentration of values

### Easy memory

**Histogram = Distribution + Frequency**

---

# 13. Box Plot

A box plot helps understand:

* Median
* Spread
* Quartiles
* Outliers

```python
import matplotlib.pyplot as plt

salary = [20000, 22000, 25000, 28000, 30000, 32000, 90000]

plt.boxplot(salary)

plt.title("Salary Distribution")
plt.ylabel("Salary")

plt.show()
```

### Usage

Box plots are especially useful for identifying **outliers**.

---

# 14. Violin Plot

A violin plot combines information about distribution and density.

```python
import matplotlib.pyplot as plt

salary = [20000, 22000, 25000, 28000, 30000, 32000, 90000]

plt.violinplot(salary)

plt.title("Salary Distribution")
plt.ylabel("Salary")

plt.show()
```

### Usage

Use violin plots when you want to understand:

* Distribution
* Density
* Spread

---

## `xticks()`

We can change the labels on the X-axis.

```python
plt.xticks([1, 2, 3], ["A", "B", "C"])
```

Meaning:

```text
1 → A
2 → B
3 → C
```

---

# 15. Relationship Charts

A **relationship** means understanding how two or more variables are connected.

Example:

```text
Study Hours → Marks
Experience → Salary
Age → Salary
Advertising → Sales
```

Common relationship charts:

* Scatter plot
* Line plot
* Pair plot
* Joint plot

### Easy memory

**Relationship = How variables are connected**

---

# 16. Scatter Plot

A scatter plot shows the relationship between two numerical variables.

```python
import matplotlib.pyplot as plt

experience = [1, 2, 3, 4, 5]
salary = [25000, 30000, 35000, 42000, 50000]

plt.scatter(experience, salary)

plt.title("Experience vs Salary")
plt.xlabel("Experience")
plt.ylabel("Salary")

plt.show()
```

### Usage

Useful for identifying:

* Relationships
* Patterns
* Clusters
* Possible outliers

---

# 17. Multiple Line Plot

Multiple lines can be used to compare trends.

```python
import matplotlib.pyplot as plt

years = [2022, 2023, 2024, 2025, 2026]

sales_a = [50, 60, 70, 80, 90]
sales_b = [40, 55, 65, 75, 85]

plt.plot(years, sales_a, label="Product A")
plt.plot(years, sales_b, label="Product B")

plt.title("Product Sales Trend")
plt.xlabel("Year")
plt.ylabel("Sales")

plt.legend()
plt.show()
```

### Usage

Useful for comparing trends between multiple categories.

---

# 18. Composition Charts

**Composition** means understanding how a total is divided into different parts.

Example:

```text
Total Sales = 100%

Laptop    → 40%
Mobile    → 30%
Tablet    → 20%
Other     → 10%
```

Common composition charts:

* Pie chart
* Donut chart
* Stacked bar
* Stacked area

### Easy memory

**Composition = Parts of a Whole**

---

# 19. Pie Chart

A pie chart shows how categories contribute to a total.

```python
import matplotlib.pyplot as plt

subjects = ["Python", "Java", "C", "C++"]
students = [20, 30, 10, 40]

plt.pie(
    students,
    labels=subjects,
    autopct="%1.1f%%"
)

plt.title("Students by Course")

plt.show()
```

### `autopct`

```python
autopct="%1.1f%%"
```

displays percentages on the pie chart.

### Usage

Best for showing simple part-to-whole relationships.

---

# 20. Donut Chart

A donut chart is basically a pie chart with a hole in the center.

```python
import matplotlib.pyplot as plt

labels = ["Python", "Java", "C", "C++"]
values = [20, 30, 10, 40]

plt.pie(
    values,
    labels=labels,
    autopct="%1.1f%%",
    wedgeprops={"width": 0.4}
)

plt.title("Course Distribution")

plt.show()
```

---

# 21. Area Chart

An area chart is useful for showing trends while emphasizing the magnitude.

```python
import matplotlib.pyplot as plt

years = [2022, 2023, 2024, 2025, 2026]
sales = [70, 95, 135, 150, 120]

plt.fill_between(years, sales)

plt.title("Sales Area Chart")
plt.xlabel("Year")
plt.ylabel("Sales")

plt.show()
```

---

# 22. Stacked Area Chart

A stacked area chart shows how multiple categories contribute to a total over time.

```python
import matplotlib.pyplot as plt

years = [2022, 2023, 2024, 2025]

product_a = [20, 30, 40, 50]
product_b = [30, 35, 45, 55]

plt.stackplot(
    years,
    product_a,
    product_b,
    labels=["Product A", "Product B"]
)

plt.title("Product Contribution")
plt.xlabel("Year")
plt.ylabel("Sales")

plt.legend()
plt.show()
```

---

# 23. Heatmap

A heatmap represents values using different levels of intensity.

In Data Analytics, heatmaps are commonly used for:

* Correlation
* Pivot tables
* Comparing two categorical dimensions

Example:

```python
import seaborn as sns
import matplotlib.pyplot as plt

data = [
    [10, 20, 30],
    [20, 40, 60],
    [30, 60, 90]
]

sns.heatmap(data, annot=True)

plt.title("Heatmap")
plt.show()
```

### `annot=True`

Displays the actual values inside the cells.

---

# 24. 3D Visualizations

Matplotlib can also create 3D visualizations.

## 3D Scatter Plot

```python
import matplotlib.pyplot as plt

fig = plt.figure()

ax = fig.add_subplot(111, projection="3d")

x = [1, 2, 3, 4]
y = [10, 20, 15, 30]
z = [5, 10, 8, 15]

ax.scatter(x, y, z)

ax.set_xlabel("X")
ax.set_ylabel("Y")
ax.set_zlabel("Z")

plt.show()
```

A 3D scatter plot can show the relationship between three numerical variables.

---

# 25. Seaborn

**Seaborn** is a Python visualization library built on top of Matplotlib.

It is especially useful for:

* Statistical visualization
* Exploratory Data Analysis
* Distribution analysis
* Relationship analysis
* Categorical data

Import:

```python
import seaborn as sns
import matplotlib.pyplot as plt
```

---

# 26. Seaborn Count Plot

A count plot counts the number of observations in each category.

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.countplot(data=df, x="Gender")

plt.title("Gender Count")
plt.show()
```

### Usage

Useful for categorical variables.

Example:

```text
Male     → 50
Female   → 45
```

---

# 27. Seaborn Bar Plot

A Seaborn bar plot can show an aggregated value such as the mean.

```python
sns.barplot(
    data=df,
    x="Gender",
    y="Salary"
)

plt.title("Average Salary by Gender")
plt.show()
```

This can be used to compare average salary between categories.

---

# 28. Seaborn Histogram

```python
sns.histplot(
    data=df,
    x="Salary",
    bins=10
)

plt.title("Salary Distribution")
plt.show()
```

It helps understand how numerical values are distributed.

---

# 29. Seaborn Box Plot

```python
sns.boxplot(
    data=df,
    x="Gender",
    y="Salary"
)

plt.title("Salary Distribution by Gender")
plt.show()
```

This helps compare distributions and identify possible outliers between categories.

---

# 30. Seaborn Violin Plot

```python
sns.violinplot(
    data=df,
    x="Gender",
    y="Salary"
)

plt.title("Salary Distribution by Gender")
plt.show()
```

It provides information about the distribution and density of the numerical variable.

---

# 31. Seaborn Scatter Plot

```python
sns.scatterplot(
    data=df,
    x="Age",
    y="Salary"
)

plt.title("Age vs Salary")
plt.show()
```

This is useful for understanding the relationship between two numerical variables.

---

# 32. Hue

`hue` is used in Seaborn to divide the visualization based on another categorical variable.

Example:

```python
sns.scatterplot(
    data=df,
    x="Age",
    y="Salary",
    hue="Gender"
)

plt.title("Age vs Salary by Gender")
plt.show()
```

Here:

```text
X       → Age
Y       → Salary
Hue     → Gender
```

So the same chart can show different categories separately.

### Easy memory

**hue = category separation**

---

# 33. Seaborn Heatmap

A common use of a heatmap is visualizing a correlation matrix.

```python
import seaborn as sns
import matplotlib.pyplot as plt

corr = df.corr(numeric_only=True)

sns.heatmap(
    corr,
    annot=True
)

plt.title("Correlation Heatmap")
plt.show()
```

### Usage

A correlation heatmap helps identify relationships between numerical variables.

---

# 34. Pair Plot

A **pair plot** is useful when we want to examine relationships between multiple numerical variables at the same time.

```python
import seaborn as sns

sns.pairplot(df)

plt.show()
```

### With `hue`

```python
sns.pairplot(
    df,
    hue="Gender"
)

plt.show()
```

### What does pair plot show?

It creates multiple plots showing relationships between numerical columns.

It can help us identify:

* Relationships
* Distributions
* Clusters
* Patterns

### Easy memory

**Pair Plot = Many variable relationships together**

---

# 35. Joint Plot

A **joint plot** shows the relationship between two variables along with their individual distributions.

```python
import seaborn as sns

sns.jointplot(
    data=df,
    x="Age",
    y="Salary"
)

plt.show()
```

### Usage

Useful when we want to study:

```text
Variable 1
     +
Variable 2
     +
Their distributions
```

### Easy memory

**Joint Plot = Relationship + Distribution**

---

# 36. Pivot Table + Heatmap

A pivot table summarizes data across categories.

For example:

```python
pivot = df.pivot_table(
    values="Sales",
    index="Gender",
    columns="Department",
    aggfunc="mean"
)

print(pivot)
```

We can visualize the pivot table using a heatmap:

```python
sns.heatmap(
    pivot,
    annot=True
)

plt.title("Average Sales by Gender and Department")
plt.show()
```

### Why use this?

It allows us to analyze two categorical dimensions and one numerical measure.

Example:

```text
Gender × Department → Average Sales
```

---

# 37. Advanced EDA

Seaborn becomes very useful during advanced Exploratory Data Analysis.

The important visualizations studied are:

### 1. Heatmap

Used to understand:

* Correlation
* Pivot-table values
* Patterns

```python
sns.heatmap(data, annot=True)
```

---

### 2. Pair Plot

Used to understand:

* Multiple variable relationships
* Distributions
* Patterns

```python
sns.pairplot(df)
```

---

### 3. Joint Plot

Used to understand:

* Relationship between two variables
* Individual distributions

```python
sns.jointplot(data=df, x="Age", y="Salary")
```

---

### 4. Pivot Table + Heatmap

Used to summarize data and visualize the summary.

```python
pivot = df.pivot_table(
    values="Sales",
    index="Gender",
    columns="Department",
    aggfunc="mean"
)

sns.heatmap(pivot, annot=True)
plt.show()
```

### Advanced EDA Question

These visualizations help answer:

> **"Can I understand many aspects of my dataset through visualization?"**

---

# 38. Chart Selection Cheat Sheet

| Question                                        | Chart                 |
| ----------------------------------------------- | --------------------- |
| Want to compare categories?                     | Bar Chart             |
| Want to compare horizontal categories?          | Barh                  |
| Want to see a trend?                            | Line Plot             |
| Want to compare multiple trends?                | Multiple Line         |
| Want to see frequency/distribution?             | Histogram             |
| Want to identify outliers?                      | Box Plot              |
| Want distribution + density?                    | Violin Plot           |
| Want relationship between two variables?        | Scatter Plot          |
| Want parts of a whole?                          | Pie / Donut           |
| Want contribution over time?                    | Area / Stacked Area   |
| Want correlation?                               | Heatmap               |
| Want many variable relationships?               | Pair Plot             |
| Want two-variable relationship + distributions? | Joint Plot            |
| Want category-based visualization?              | `hue`                 |
| Want summarized categorical data?               | Pivot Table + Heatmap |

---

# 🧠 Easy Visualization Memory Rule

### 1. Comparison

**"Which is bigger?"**

➡️ Bar Chart

### 2. Trend

**"How is it changing?"**

➡️ Line Chart

### 3. Distribution

**"How is the data spread?"**

➡️ Histogram / Box / Violin

### 4. Relationship

**"How are two variables connected?"**

➡️ Scatter Plot

### 5. Composition

**"What are the parts of the total?"**

➡️ Pie / Donut / Stacked Charts

### 6. Correlation / Matrix

**"How do many numerical variables relate?"**

➡️ Heatmap

### 7. Many Relationships

**"Can I explore many variables together?"**

➡️ Pair Plot

### 8. Two Variables + Distribution

**"Can I see the relationship and distributions together?"**

➡️ Joint Plot

---

# 39. Learning Outcome

Through this Matplotlib and Seaborn practice, I learned:

* Basic data visualization
* Different types of charts
* When to use different charts
* Comparison visualization
* Trend visualization
* Distribution visualization
* Relationship visualization
* Composition visualization
* Correlation visualization
* Multiple charts using subplots
* Axis labels and titles
* Legends
* Figure sizing
* `xticks()`
* Seaborn `hue`
* Heatmaps
* Pair plots
* Joint plots
* Pivot tables with heatmaps
* Visualization techniques for EDA

These concepts will help me create meaningful visualizations and extract insights from datasets as part of my **Data Analyst journey**.

---

## 🛠️ Libraries Used

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
```

---

## 📌 Project Focus

**Data Visualization → Exploratory Data Analysis → Business Insights**

> Learning how to convert raw data into meaningful visual information using Python.
