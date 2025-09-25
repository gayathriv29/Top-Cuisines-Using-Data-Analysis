


# 🍽️ Top Cuisines Using Data Analysis

  🧠 Project Overview

  This project explores global cuisine preferences using data analysis and visualization techniques. By examining food ratings, review counts, and regional trends, it identifies the most popular and highly rated cuisines across different countries. The goal is to uncover insights that can guide restaurant planning, food delivery platforms, and culinary tourism.

  Using Python and libraries like pandas, seaborn, matplotlib, and plotly, the project transforms raw food review data into actionable intelligence. It highlights not only the top cuisines but also underrated gems and regional biases in taste.





🌟 Key Features
- Clean and reproducible data pipeline
- Rich visualizations for storytelling
- Insightful summaries for decision-making
- Modular code structure for easy extension



## 🧰 Prerequisites

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn plotly
```

---

## 📁 Project Structure

```
Top-Cuisines-Analysis/
│
├── data/                  # Raw and cleaned datasets
├── notebooks/             # Jupyter notebooks for analysis
├── outputs/               # Charts and summary tables
├── utils/                 # Helper functions
└── README.md              # Documentation
```

---

## 📝 Step-by-Step Process

### 1. 📥 Load the Dataset

```python
import pandas as pd

df = pd.read_csv('data/cuisine_reviews.csv')
df.head()
```

**Output**: Displays columns like `Cuisine`, `Rating`, `Country`, `Review_Count`.

---

### 2. 🧹 Clean the Data

```python
df.dropna(inplace=True)
df['Cuisine'] = df['Cuisine'].str.title().str.strip()
df['Rating'] = df['Rating'].astype(float)
```

**Result**: Cleaned and standardized dataset ready for analysis.

---

### 3. 📊 Analyze Top-Rated Cuisines

```python
top_cuisines = df.groupby('Cuisine')['Rating'].mean().sort_values(ascending=False).head(10)

import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(10,6))
sns.barplot(x=top_cuisines.values, y=top_cuisines.index, palette='viridis')
plt.title('Top 10 Cuisines by Average Rating')
plt.xlabel('Average Rating')
plt.ylabel('Cuisine')
plt.show()
```

**Output**: Bar chart showing the highest-rated cuisines globally.

---

### 4. 📈 Analyze Most Reviewed Cuisines

```python
popularity = df['Cuisine'].value_counts().head(10)

plt.figure(figsize=(8,6))
sns.barplot(x=popularity.values, y=popularity.index, palette='magma')
plt.title('Most Reviewed Cuisines')
plt.xlabel('Number of Reviews')
plt.ylabel('Cuisine')
plt.show()
```

**Result**: Reveals cuisines with the highest visibility and review volume.

---

### 5. 🌍 Explore Regional Preferences

```python
regional = df.groupby(['Country', 'Cuisine'])['Rating'].mean().unstack().fillna(0)

plt.figure(figsize=(12,6))
sns.heatmap(regional, cmap='coolwarm')
plt.title('Cuisine Ratings by Country')
plt.show()
```

**Output**: Heatmap showing how different countries rate various cuisines.

---

### 6. 📦 Export Summary Tables

```python
top_cuisines.to_csv('outputs/top_cuisines.csv')
popularity.to_csv('outputs/most_reviewed.csv')
```

**Result**: Saves key insights for reporting or dashboard integration.

---

## ✅ Final Results

### 🔝 Top-Rated Cuisines
- Italian, Japanese, Indian, Thai, Mediterranean

### 📈 Most Reviewed Cuisines
- American, Chinese, Mexican

### 💎 Underrated Gems
- Lebanese and Korean cuisines show high ratings but low review counts

### 🌐 Regional Biases
- Europe: French, Mediterranean
- Asia: Japanese, Indian
- North America: Mexican, American

---

## 📚 References

- [Seaborn Documentation](https://seaborn.pydata.org/)
- [Plotly Express](https://plotly.com/python/plotly-express/)
- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [Pandas Documentation](https://pandas.pydata.org/docs/)

---

## 👤 Author

   Gayathri V  

   Data Analyst & Machine Learning Enthusiast  
📍  Focused on practical data science, visualization, and explainable AI.


