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
