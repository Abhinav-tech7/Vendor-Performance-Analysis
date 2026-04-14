🏪 Vendor Performance Analysis
A comprehensive end-to-end data analysis project to evaluate vendor performance, inventory efficiency, and profitability for a retail/wholesale business. This project covers data ingestion, SQL-based transformation, exploratory data analysis, and an interactive Power BI dashboard.

```
📁 Repository Structure
├── logs/                          # Log files for ingestion and summary scripts
├── notebooks/
│   ├── Exploratory_Data_Analysis.ipynb
│   └── Vendor_Performance_Analysis.ipynb
├── reports/
│   └── Vendor_Performance_Report.pdf
|   |__ dashboard.png              # Power BI Dashboard Image
├── scripts/
│   ├── ingestion_db.py            # Loads raw CSVs into SQLite database
│   └── get_vendor_summary.py      # Merges tables and creates vendor summary
├── .gitignore
└── vendor_sales_summary.csv       # Final cleaned summary (exported from DB)
```

⚠️ Note: The inventory.db SQLite database (~2GB) is excluded from this repository via .gitignore. Raw CSV files are available via the Google Drive link below.

📦 Raw Data
The raw CSV files hosted on Google Drive:

📂 Download Raw Data : https://drive.google.com/drive/folders/1E8KIWXc3C-LhAE7Si7iFJMKA31FJXv1m?usp=drive_link

After downloading, place the CSV files inside a data/ folder in the project root before running the ingestion script.

⚙️ Setup & Usage

1. Clone the Repository
bashgit clone https://github.com/Abhinav-tech7/vendor-performance-analysis.git
cd vendor-performance-analysis
2. Install Dependencies
bashpip install pandas sqlalchemy
3. Add Raw Data
Download the raw CSV files from the Google Drive link and place them in a data/ folder:
data/
├── purchases.csv
├── purchase_prices.csv
├── sales.csv
└── vendor_invoice.csv
|__ brgin_inventory.csv
|__ end_inventory.csv
5. Run the Ingestion Script
Loads all CSV files from the data/ folder into inventory.db:
bashpython scripts/ingestion_db.py
6. Generate the Vendor Summary
Runs SQL joins across tables, engineers new features, and saves the result as the vendor_sales_summary table:
bashpython scripts/get_vendor_summary.py
7. Explore the Notebooks
Open either notebook in Jupyter to reproduce the full analysis:
bashjupyter notebook notebooks/

🔍 Key Findings

- 198 brands have low sales but high profit margins — candidates for targeted promotions or pricing adjustments.
- Top 10 vendors account for 65.69% of total purchases, indicating over-reliance and supply chain risk.
- Bulk purchasing yields a 72% lower unit cost ($10.78 vs $39.06 for small orders).
- $2.71M is locked in slow-moving, unsold inventory.
- Hypothesis testing confirms a statistically significant difference in profit margins between top-performing (mean: 31.17%) and low-performing vendors (mean: 41.55%).

📝 Logs
Execution logs are saved under the logs/ directory:

logs/ingestion_db.log — CSV ingestion activity
logs/get_vendor_summary.log — Summary table creation activity

📄 Report
The full analysis report with charts, statistical validation, and recommendations is available at:
reports/Vendor_Performance_Report.pdf
