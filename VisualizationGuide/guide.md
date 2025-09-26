# Matplotlib

## Overview
Matplotlib is one of the most widely used Python libraries for creating static, animated, and interactive visualizations.  
- **Key Features:**
  - Low-level library that gives full control over plots.
  - Supports 2D and limited 3D plots.
  - Highly customizable (titles, labels, colors, styles).
  - Useful for creating publication-quality figures.
- **Typical Use Cases:**  
  - Quick exploratory data visualization.  
  - Scientific research and academic publications.  
  - Building plots from scratch with fine-grained control.  

---

## Graph Types in Matplotlib

### 1. Line Plot
**Use Case:** Show trends over time or continuous variables.  

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

plt.plot(x, y, marker='o')
plt.title("Line Plot Example")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.show()

2. Scatter Plot

Use Case: Show relationships or correlations between two variables.

```python
import matplotlib.pyplot as plt

x = [5, 7, 8, 7, 6, 9, 5, 6, 7, 8]
y = [99, 86, 87, 88, 100, 86, 103, 87, 94, 78]

plt.scatter(x, y, color='red')
plt.title("Scatter Plot Example")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.show()

Bar Chart

Use Case: Compare categories or groups.

import matplotlib.pyplot as plt

categories = ['A', 'B', 'C', 'D']
values = [3, 7, 5, 6]

plt.bar(categories, values, color='green')
plt.title("Bar Chart Example")
plt.xlabel("Categories")
plt.ylabel("Values")
plt.show()

Histogram

Use Case: Show the distribution of data values.

import matplotlib.pyplot as plt

data = [1,1,2,3,3,3,4,4,4,4,5,5,6,7,8,9,10]

plt.hist(data, bins=5, color='purple', edgecolor='black')
plt.title("Histogram Example")
plt.xlabel("Bins")
plt.ylabel("Frequency")
plt.show()

Pie Chart

Use Case: Show proportions of a whole.

import matplotlib.pyplot as plt

sizes = [40, 25, 20, 15]
labels = ['Apples', 'Bananas', 'Cherries', 'Dates']

plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90)
plt.title("Pie Chart Example")
plt.show()




# Seaborn  

## Overview  
Seaborn is a high-level Python data visualization library built on top of Matplotlib. It provides a cleaner, simpler syntax and comes with attractive default styles and color themes.  

- **Key Features:**  
  - Built-in themes for beautiful plots.  
  - Works seamlessly with Pandas DataFrames.  
  - Easy functions for statistical plots.  
  - Great for data exploration and quick insights.  

- **Typical Use Cases:**  
  - Statistical data visualization.  
  - Exploratory data analysis (EDA).  
  - Creating heatmaps, categorical plots, and regression plots.  

---

## Graph Types in Seaborn  

### 1. Scatter Plot  
**Use Case:** Visualize relationships between two numerical variables.  

```python
import seaborn as sns
import matplotlib.pyplot as plt

tips = sns.load_dataset("tips")
sns.scatterplot(x="total_bill", y="tip", data=tips, hue="sex")
plt.title("Scatter Plot Example")
plt.show()

Bar Plot

Use Case: Compare mean/aggregate values across categories.

import seaborn as sns
import matplotlib.pyplot as plt

tips = sns.load_dataset("tips")
sns.barplot(x="day", y="total_bill", data=tips)
plt.title("Bar Plot Example")
plt.show()

Histogram (Displot)

Use Case: Show distribution of numerical data.

import seaborn as sns
import matplotlib.pyplot as plt

tips = sns.load_dataset("tips")
sns.displot(tips["total_bill"], bins=10, kde=True)
plt.title("Histogram Example")
plt.show()

Box Plot

Use Case: Show data spread and detect outliers.

import seaborn as sns
import matplotlib.pyplot as plt

tips = sns.load_dataset("tips")
sns.boxplot(x="day", y="total_bill", data=tips)
plt.title("Box Plot Example")
plt.show()

Heatmap

Use Case: Visualize correlations or matrix data.

import seaborn as sns
import matplotlib.pyplot as plt

flights = sns.load_dataset("flights").pivot("month", "year", "passengers")
sns.heatmap(flights, annot=True, fmt="d", cmap="YlGnBu")
plt.title("Heatmap Example")
plt.show()

