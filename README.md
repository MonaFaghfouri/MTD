
# 📊 Monthly Sales Summary (Persian Calendar)

This repository provides a Python script for generating **monthly and comparative sales summaries** based on data retrieved from a SQL Server `SaleInvoice` table.  
The logic is fully aligned with the Persian (Jalali) calendar and is designed for **real-world sales analytics**, including:

- 📌 Comparing the current month vs. the previous month  
- 📌 Comparing the current month vs. three custom user-selected months  
- 📌 Calculating month-to-date performance  
- 📌 Generating growth rates and performance indicators  
- 📌 Exporting a detailed report to Excel  

---

## 🚀 Features

### ✔ 1. Fetches Sales Data from SQL Server  
The script connects to SQL Server using SQLAlchemy and retrieves:

- `SalesChannelCode`  
- `SalesChannelName`  
- `InvoiceSDate` (Jalali)  
- `SaleCartonQuantity`  

### ✔ 2. User Selects Three Persian Months  
Input format: `YYYY/MM`  
Example: `1404/03`

### ✔ 3. Automatic Date Logic (Jalali)  
- Detects today's Persian date  
- Computes previous month (including year rollover)  
- Defines comparable time windows:  
  - Previous month full  
  - Previous month up to today's day  
  - Current month to date  

### ✔ 4. Per-Channel Aggregations  
For each `SalesChannel`:

- Sales in selected Month1 / Month2 / Month3  
- Sales in previous month (full & comparable)  
- Sales in current month until today  

### ✔ 5. KPIs and Growth Rates  
The script computes:

- **3-month average**  
- **Growth vs. last month**  
- **Growth vs. 3-month average**  
- **Current share vs. full previous month**  

### ✔ 6. Export to Excel  
The final summary is saved as:

```

Summary.xlsx

````

---

## 📁 File: `sales_summary.py`

The script contains:

- SQL Server connection  
- Jalali date logic  
- Grouped aggregations  
- KPI calculations  
- Excel export  

Sanitized SQL connection for GitHub:

```python
engine = create_engine(
    "mssql+pyodbc://<USERNAME>:<PASSWORD>@<SERVER>/<DATABASE>?driver=ODBC+Driver+17+for+SQL+Server"
)
````

---

## 🧮 Required Python Libraries

```bash
pip install pandas jdatetime sqlalchemy pyodbc
```

Optional (for Excel output):

```bash
pip install xlsxwriter
```

---

## ▶️ How to Run

1. Clone the repository
2. Update SQL connection placeholders
3. Run the script:

```bash
python sales_summary.py
```

4. Enter the Persian months when prompted:

```
🔹 Enter three Persian months (example 1404/03)
First month (oldest): 1403/12
Second month: 1404/01
Third month (latest): 1404/02
```

5. The final report will be generated as:

```
Summary.xlsx
```

---

## 📊 Output Columns

| Column                          | Description                         |
| ------------------------------- | ----------------------------------- |
| `TotalCarton_Month1/2/3`        | Cartons sold in selected months     |
| `TotalCarton_LastMonth`         | Previous month up to same day       |
| `TotalCarton_LastMonthFull`     | Previous month full                 |
| `TotalCarton_CurrentMonth`      | Current month up to today           |
| `Avg_Selected3Months`           | Average of selected months          |
| `GrowthRate_vs_LastMonth`       | % growth vs previous month          |
| `GrowthRate_vs_Selected3Months` | % growth vs 3-month average         |
| `Share_vs_LastMonthFull`        | Contribution vs previous full month |
| `TodayFa`                       | Today's Jalali date                 |
| `SelectedMonth1–3`              | User-selected Persian months        |

---

## 👤 Author

**Mona Faghfouri Azar**
Data Analyst & NLP Researcher 
GitHub: [@MonaFaghfouri](https://github.com/MonaFaghfouri)

---

## 📜 License

This project is released under the **MIT License**.

```
 

