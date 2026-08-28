# Sales Data Analysis

Exploratory data analysis of the Sample Superstore sales dataset using Python, Pandas, and Seaborn/Matplotlib.

## 📌 Overview

This notebook (`sales.ipynb`) walks through a basic EDA workflow on retail sales data:

- Loading and inspecting the dataset
- Data cleaning (parsing `Order Date` and `Ship Date` as datetime)
- Feature engineering (`Delivery Days` — time between order and shipment)
- Checking for missing values and unique categories
- Aggregating total sales by product category
- Visualizing sales by category and overall sales distribution

## 🗂️ Dataset

The notebook expects a CSV file named `samplesuperstore.csv` (the "Sample Superstore" dataset, commonly used for retail analytics practice) at:

```
/content/samplesuperstore.csv
```

> **Note:** This path is set up for Google Colab. If running locally or elsewhere, update the path in the notebook, e.g.:
> ```python
> df = pd.read_csv("data/samplesuperstore.csv")
> ```

Typical columns include: `Order Date`, `Ship Date`, `Category`, `Sub-Category`, `Sales`, `Profit`, `Region`, etc.

## 🛠️ Requirements

- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn
```

## 🚀 Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```
2. Place `samplesuperstore.csv` in the appropriate directory (update the path in the notebook if needed).
3. Launch Jupyter Notebook / Jupyter Lab:
   ```bash
   jupyter notebook sales.ipynb
   ```
4. Run all cells to reproduce the analysis.

## 📊 Key Steps in the Notebook

| Step | Description |
|------|-------------|
| Data Loading | Reads the CSV into a Pandas DataFrame |
| Data Inspection | `head()`, `info()`, `shape`, `describe()` |
| Date Parsing | Converts `Order Date` and `Ship Date` to datetime |
| Feature Engineering | Calculates `Delivery Days` |
| Data Quality Check | Checks unique categories and null values |
| Aggregation | Total sales grouped by `Category` |
| Visualization | Bar chart of sales by category; histogram of sales distribution |

## 📈 Example: Code & Output

Below is a sample run showing the notebook's logic in action (numbers below are from a small demo dataset used to illustrate the workflow — your real output will reflect your own `samplesuperstore.csv`).

### 1. Load and inspect the data

```python
import pandas as pd
df = pd.read_csv("/content/samplesuperstore.csv")
df.info()
```

```
<class 'pandas.DataFrame'>
RangeIndex: 200 entries, 0 to 199
Data columns (total 5 columns):
 #   Column      Non-Null Count  Dtype  
---  ------      --------------  -----  
 0   Order Date  200 non-null    object
 1   Ship Date   200 non-null    object
 2   Category    200 non-null    object
 3   Region      200 non-null    object
 4   Sales       200 non-null    float64
dtypes: float64(1), object(4)
memory usage: 7.9 KB
```

### 2. Parse dates and engineer `Delivery Days`

```python
df['Order Date'] = pd.to_datetime(df['Order Date'], format="mixed")
df['Ship Date'] = pd.to_datetime(df['Ship Date'], format="mixed")
df['Delivery Days'] = (df['Ship Date'] - df['Order Date']).dt.days
df.head()
```

```
  Order Date  Ship Date         Category Region   Sales  Delivery Days
0 2023-01-01 2023-01-05        Furniture   West  164.34              4
1 2023-01-04 2023-01-09  Office Supplies   West   68.55              5
2 2023-01-07 2023-01-10  Office Supplies   West   51.77              3
3 2023-01-10 2023-01-15        Furniture  South  265.61              5
4 2023-01-13 2023-01-18  Office Supplies   East  193.44              5
```

### 3. Aggregate sales by category

```python
category_sales = df.groupby('Category')['Sales'].sum()
category_sales
```

```
Category
Furniture          15419.67
Office Supplies    28919.40
Technology         18756.14
Name: Sales, dtype: float64
```

### 4. Visualize

```python
import matplotlib.pyplot as plt

category_sales.plot(kind='bar', figsize=(8,5))
plt.title("Sales by Category")
plt.ylabel("Total Sales")
plt.show()
```

**Output:**

<img width="721" height="560" alt="image" src="https://github.com/user-attachments/assets/1eed901d-9595-4674-8ca3-4c8fba26e4e2" />


```python
import seaborn as sns

plt.figure(figsize=(8,5))
sns.histplot(df['Sales'], bins=30)
plt.title("Sales Distribution")
plt.show()
```

This produces a histogram showing how individual sale amounts are distributed (right-skewed, with most sales clustered at lower values and a long tail of higher-value orders).

## 🤝 Contributing

Feel free to fork this repo and submit a pull request with improvements or additional analysis (e.g., profit analysis, regional breakdowns, time-series trends).

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
