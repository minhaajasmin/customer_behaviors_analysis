# Data Analytics Project

End-to-end data analytics pipeline — from raw data to interactive dashboard and executive presentation.

-----

## Overview

This project demonstrates a complete data analytics workflow, covering data ingestion, exploratory data analysis (EDA), data cleaning, SQL-based querying, interactive dashboard creation in Power BI, and a final business report and presentation. It is designed to reflect real-world analytics practices and showcases both technical and communication skills.

-----

## Dataset

|Attribute|Details                                     |
|---------|--------------------------------------------|
|Name     |Sales Transactions Dataset                  |
|Source   |Kaggle / Company Database / Open Data Portal|
|Format   |CSV / Excel / Database Table                |
|Size     |50,000 rows x 15 columns                    |
|Domain   |Retail / Finance / Healthcare               |

Raw data is stored in the /data/raw/ folder. Cleaned data is saved to /data/cleaned/.

-----

## Tools and Technologies

|Category       |Tools Used                      |
|---------------|--------------------------------|
|Language       |Python 3.x                      |
|Data Analysis  |Pandas, NumPy                   |
|Visualization  |Matplotlib, Seaborn             |
|Database       |PostgreSQL / MySQL / SQL Server |
|SQL Client     |pgAdmin / MySQL Workbench / SSMS|
|BI Dashboard   |Microsoft Power BI              |
|Report         |Microsoft Word / PDF            |
|Presentation   |Gamma                           |
|Notebook       |Jupyter Notebook                |
|Version Control|Git and GitHub                  |

-----

## Project Steps

### Step 1 - Load the Dataset

- Imported the dataset using Pandas
- Previewed structure with .head(), .info(), .describe()
- Checked data types, column names, and row count

```python
import pandas as pd

df = pd.read_csv('data/raw/dataset.csv')
print(df.shape)
df.head()
```

-----

### Step 2 - Exploratory Data Analysis (EDA)

- Analyzed distributions, trends, and outliers
- Generated visualizations using Matplotlib and Seaborn
- Identified key patterns and business insights

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.heatmap(df.corr(), annot=True, cmap='coolwarm')
plt.show()
```

Full EDA notebook: notebooks/01_EDA.ipynb

-----

### Step 3 - Data Cleaning

- Handled missing values (imputation / removal)
- Removed duplicate rows
- Standardized data types and formats
- Renamed columns for consistency
- Exported cleaned data for further analysis

```python
df.drop_duplicates(inplace=True)
df['date_column'] = pd.to_datetime(df['date_column'])
df.to_csv('data/cleaned/cleaned_dataset.csv', index=False)
```

Cleaning notebook: notebooks/02_Data_Cleaning.ipynb

-----

### Step 4 - SQL Analysis

- Loaded the cleaned dataset into PostgreSQL / MySQL / SQL Server
- Wrote queries to answer key business questions
- Performed aggregations, joins, window functions, and CTEs

```sql
-- Top 5 categories by total revenue
SELECT
    category,
    SUM(sales_amount) AS total_revenue,
    RANK() OVER (ORDER BY SUM(sales_amount) DESC) AS revenue_rank
FROM sales
GROUP BY category
ORDER BY total_revenue DESC
LIMIT 5;
```

All SQL scripts are in the /sql/ folder.

-----

### Step 5 - Power BI Dashboard

- Connected Power BI to the cleaned dataset / database
- Built interactive visuals: bar charts, KPI cards, slicers, line charts, and maps
- Applied DAX measures for calculated metrics
- Published the dashboard for stakeholder use

Dashboard file: dashboard/Sales_Dashboard.pbix

-----

### Step 6 - Report

- Summarized methodology, findings, and recommendations in a structured report
- Included charts, tables, and key takeaways

Report: report/Analytics_Report.pdf

-----

### Step 7 - Presentation (Gamma)

- Built an executive-ready slide deck using Gamma
- Covered: problem statement, approach, key insights, and recommendations
- Designed for a non-technical business audience

-----

## Key Results and Insights

- Region X contributed 42% of total revenue in Q4
- Product category Y showed a 28% year-over-year growth trend
- 3 customer segments account for 70% of repeat purchases
- Data quality improved by 35% after the cleaning pipeline

Full findings are documented in the Analytics Report.

-----

## Project Structure

```
data-analytics-project/
├── data/
│   ├── raw/                    # Original dataset
│   └── cleaned/                # Cleaned and processed data
├── notebooks/
│   ├── 01_EDA.ipynb            # Exploratory Data Analysis
│   └── 02_Data_Cleaning.ipynb  # Data Cleaning
├── sql/
│   ├── create_tables.sql
│   ├── analysis_queries.sql
│   └── aggregations.sql
├── dashboard/
│   └── Sales_Dashboard.pbix    # Power BI file
├── report/
│   └── Analytics_Report.pdf
├── requirements.txt
└── README.md
```

-----

## How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/data-analytics-project.git
cd data-analytics-project
```

### 2. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the Notebooks

```bash
jupyter notebook
```

Run in this order:

- notebooks/01_EDA.ipynb
- notebooks/02_Data_Cleaning.ipynb

### 4. Set Up the Database

- Create a database in PostgreSQL / MySQL / SQL Server
- Run the scripts in /sql/ in this order:
1. create_tables.sql
1. analysis_queries.sql

### 5. Open the Power BI Dashboard

- Open dashboard/Sales_Dashboard.pbix in Power BI Desktop
- Refresh the data source connection if needed

-----

## Requirements

```
pandas
numpy
matplotlib
seaborn
jupyter
sqlalchemy
psycopg2
pymysql
pyodbc
```

Install all at once:

```bash
pip install -r requirements.txt
```

-----

## Author

Name: minhaa jasmin
Email: minhajasmin94@gmail.com
LinkedIn: [linkedin.com/in/minhaajasmin](https://www.linkedin.com/in/minhaa-jasmin-7681a7323/)
GitHub: [github.com/minhaajasmin](https://github.com/minhaajasmin)

-----

## License

This project is licensed under the MIT License.
