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

## 📈 Sample Outputs

- **Sales by Category** — bar chart comparing total sales across product categories
- **Sales Distribution** — histogram showing the spread of individual sale amounts

## 🤝 Contributing

Feel free to fork this repo and submit a pull request with improvements or additional analysis (e.g., profit analysis, regional breakdowns, time-series trends).

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
