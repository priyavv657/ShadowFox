# 📊 Visualization Guide: Matplotlib & Seaborn  

This guide explains how to create different types of plots using **Matplotlib** and **Seaborn**. It is designed for beginners who want to quickly learn the basics of Python visualization.  

---

# Graph Types in Matplotlib

## 1. Line Plot  
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
```

---

## 2. Scatter Plot  
**Use Case:** Show relationships or correlations between two variables.  

```python
import matplotlib.pyplot as plt

x = [5, 7, 8, 7, 6, 9, 5, 6, 7, 8]
y = [99, 86, 87, 88, 100, 86, 103, 87, 94, 78]

plt.scatter(x, y, color='red')
plt.title("Scatter Plot Example")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.show()
```

---

## 3. Bar Chart  
**Use Case:** Compare different categories.  

```python
import matplotlib.pyplot as plt

categories = ['A', 'B', 'C', 'D']
values = [4, 7, 2, 9]

plt.bar(categories, values, color='blue')
plt.title("Bar Chart Example")
plt.xlabel("Categories")
plt.ylabel("Values")
plt.show()
```

---

## 4. Histogram  
**Use Case:** Show the distribution of a dataset.  

```python
import matplotlib.pyplot as plt

data = [22, 87, 5, 43, 56, 73, 55, 54, 11, 20, 51, 5]

plt.hist(data, bins=5, color='green', edgecolor='black')
plt.title("Histogram Example")
plt.xlabel("Bins")
plt.ylabel("Frequency")
plt.show()
```

---

## 5. Pie Chart  
**Use Case:** Show proportions of a whole.  

```python
import matplotlib.pyplot as plt

sizes = [40, 25, 20, 15]
labels = ['Apples', 'Bananas', 'Cherries', 'Dates']

plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90)
plt.title("Pie Chart Example")
plt.show()
```

---

# Seaborn  

## Overview  
Seaborn is a high-level Python data visualization library built on top of Matplotlib. It provides a cleaner, simpler syntax and beautiful default themes.  

- **Key Features:**  
  - Built-in themes for beautiful plots.  
  - Works seamlessly with Pandas DataFrames.  
  - Easy functions for statistical plots.  
  - Great for data exploration and quick insights.  

- **Typical Use Cases:**  
  - Statistical data visualization.  
  - Exploratory data analysis (EDA).  

---

## 1. Line Plot  

```python
import seaborn as sns
import matplotlib.pyplot as plt

# Example data
tips = sns.load_dataset("tips")

sns.lineplot(x="size", y="total_bill", data=tips)
plt.title("Seaborn Line Plot Example")
plt.show()
```

---

## 2. Scatter Plot  

```python
import seaborn as sns
import matplotlib.pyplot as plt

tips = sns.load_dataset("tips")

sns.scatterplot(x="total_bill", y="tip", hue="time", data=tips)
plt.title("Seaborn Scatter Plot Example")
plt.show()
```

---

## 3. Bar Plot  

```python
import seaborn as sns
import matplotlib.pyplot as plt

tips = sns.load_dataset("tips")

sns.barplot(x="day", y="total_bill", data=tips)
plt.title("Seaborn Bar Plot Example")
plt.show()
```

---

## 4. Histogram  

```python
import seaborn as sns
import matplotlib.pyplot as plt

tips = sns.load_dataset("tips")

sns.histplot(tips["total_bill"], bins=10, kde=True)
plt.title("Seaborn Histogram Example")
plt.show()
```

---

## 5. Heatmap  

```python
import seaborn as sns
import matplotlib.pyplot as plt

flights = sns.load_dataset("flights")
pivot_table = flights.pivot("month", "year", "passengers")

sns.heatmap(pivot_table, annot=True, fmt="d", cmap="YlGnBu")
plt.title("Seaborn Heatmap Example")
plt.show()
```

---

## 🔎 Comparison: Matplotlib vs Seaborn

| Feature            | Matplotlib                                                                 | Seaborn                                                                 |
|--------------------|-----------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **Ease of Use**    | Very flexible but requires more code for styling and setup.                 | Simpler, with built-in themes and functions for common plots.           |
| **Customization**  | Highly customizable (low-level control over every element).                 | Less customizable (inherits from Matplotlib, but can tweak if needed). |
| **Interactivity**  | Mostly static plots; interactivity possible with extra tools (e.g., mpld3). | Limited interactivity; mostly for static, publication-ready visuals.    |
| **Performance**    | Handles large datasets efficiently.                                         | Works well with medium datasets; slower for very large data.            |
| **Best For**       | Complex, highly customized plots.                                           | Quick, beautiful, statistical plots.                                    |



## 📚 Resources

Here are the official documentation and tutorials for further learning:

- [Matplotlib Quick Start Guide](https://matplotlib.org/stable/users/explain/quick_start.html#quick-start)  
- [Seaborn Introduction](https://seaborn.pydata.org/tutorial/introduction.html)  
- [Plotly Python Graphing Library](https://plotly.com/python/)  
- [Bokeh User Guide](https://docs.bokeh.org/en/latest/docs/user_guide/basic.html)  
- [Pandas Visualization Guide](https://pandas.pydata.org/docs/user_guide/visualization.html)  
