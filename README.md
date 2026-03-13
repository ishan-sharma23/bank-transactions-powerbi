# 🏦 Bank Transactions Report — Power BI Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Power Query](https://img.shields.io/badge/Power%20Query-217346?style=for-the-badge&logo=microsoft&logoColor=white)

A comprehensive 3-page interactive Power BI dashboard for analyzing bank transactions, detecting fraudulent activity, and drilling into transaction-level details.

---

## 📊 Dashboard Pages

### 1. 🏠 Home — Bank Transaction Report
![Home Dashboard](screenshots/home-dashboard.png)

Overview of all transactions with key KPIs, time-series trends, and geographic distribution.

**Visuals Used:**
- 📌 **Card** — Total Transactions (1,000) & Transaction Amount (771.17K)
- 📈 **Line Chart** — Transactions over Time
- 🍩 **Doughnut Charts** — Fraud Flag distribution & Transaction Type breakdown
- 📊 **Bar Chart** — Transaction Status (Failed vs Success)
- 🗺️ **Map Visual** — Regional transaction distribution
- 🔽 **Slicers** — Transaction Type, Transaction Status, Device Used

---

### 2. 🔍 Fraud Detection Report
![Fraud Detection](screenshots/fraud-detection.png)

Focused view on fraudulent transactions with network and bandwidth breakdowns.

**Visuals Used:**
- 📌 **Card** — Fraudulent Transactions count & Amount
- 📊 **Bar Charts** — Bandwidth Group & Network Slice by Fraudulent Transactions
- 🍩 **Doughnut Chart** — Transaction Type
- 📊 **Stacked Bar** — Transaction Status
- 🗺️ **Map Visual** — Fraud by Region

---

### 3. 📋 Transaction Details
![Transaction Details](screenshots/transaction-details.png)

Granular transaction-level table with conditional formatting for quick fraud identification.

**Features:**
- Full transaction table with IDs, accounts, amounts, and metadata
- 🟢🔴 **Conditional Formatting** on Fraud Flag & Transaction Status columns
- **Drillthrough** enabled for deep-dive analysis

---

## ✨ Key Features & Techniques

| Feature | Description |
|---|---|
| **Data Cleaning** | Power Query transformations — removed nulls, standardized types, renamed columns |
| **DAX Measures** | Custom measures for Total Transactions, Fraud Rate, Success Rate, Amount aggregations |
| **Page Navigator** | Seamless navigation between all 3 report pages |
| **Drillthrough** | Right-click drill from summary to transaction-level detail |
| **Conditional Formatting** | Color-coded Fraud Flag (TRUE = red, FALSE = green) and Status columns |
| **Custom Background** | Designed in PowerPoint, exported as PNG and applied as canvas background |
| **Slicers** | Cross-page filters: Transaction Type, Status, Device Used |

---

## 📐 DAX Measures

```dax
-- Total Transactions
Total Transactions = COUNTROWS('Transactions')

-- Fraudulent Transactions
Fraudulent Transactions = CALCULATE(COUNTROWS('Transactions'), 'Transactions'[Fraud Flag] = TRUE())

-- Fraud Rate %
Fraud Rate % = DIVIDE([Fraudulent Transactions], [Total Transactions], 0)

-- Total Transaction Amount
Total Amount = SUM('Transactions'[Transaction Amount])

-- Success Rate
Success Rate % = 
DIVIDE(
    CALCULATE(COUNTROWS('Transactions'), 'Transactions'[Transaction Status] = "Success"),
    [Total Transactions],
    0
)
```

---

## 🔄 Power Query Transformations

- ✅ Removed duplicate Transaction IDs
- ✅ Changed data types (Amount → Decimal, Time → Time, Fraud Flag → Boolean)
- ✅ Replaced null values in Bandwidth Group with "Unknown"
- ✅ Extracted Hour from timestamp for time-series analysis
- ✅ Trimmed whitespace from categorical text columns

---

## 📁 Repository Structure

```
bank-transactions-powerbi/
│
├── 📊 BankTransactionsReport.pbix     # Main Power BI file
├── 📄 README.md                        # Project documentation
│
├── 📁 screenshots/
│   ├── home-dashboard.png              # Page 1 — Home
│   ├── fraud-detection.png             # Page 2 — Fraud Detection
│   └── transaction-details.png        # Page 3 — Transaction Details
│
└── 📁 data/
    └── bank_transactions.csv           # Source dataset (if shareable)
```

---

## 🚀 Getting Started

### Prerequisites
- [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free download)

### Steps to Open
1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/bank-transactions-powerbi.git
   ```
2. Open `BankTransactionsReport.pbix` in Power BI Desktop
3. If prompted, update the data source path to your local `data/` folder
4. Click **Refresh** to reload data

---

## 📈 Key Insights

- 📌 Out of **1,000 total transactions**, **51.9%** were flagged as fraudulent
- ❌ **513 transactions failed** vs ✅ 487 succeeded
- 💰 Total transaction volume: **$771.17K**
- 🌐 Fraudulent activity concentrated in **North America** and **Europe**
- 📡 Bandwidth group **150–250 Mbps** had the highest fraud count (481)
- 🔀 Transaction types nearly evenly split: Transfer (37.4%), Withdrawal (31.6%), Deposit (31%)

---

## 🛠️ Tools & Technologies

- **Microsoft Power BI Desktop**
- **Power Query (M Language)** — data transformation
- **DAX (Data Analysis Expressions)** — calculated measures & columns
- **Microsoft PowerPoint** — custom background design
- **Bing Maps** — geographic visuals

---

## 👤 Author

**Your Name**  
📧 your.email@example.com  
🔗 [LinkedIn](https://linkedin.com/in/yourprofile)  
🐙 [GitHub](https://github.com/YOUR_USERNAME)

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

⭐ **If you found this project helpful, please consider giving it a star!**
