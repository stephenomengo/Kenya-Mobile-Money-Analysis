# Kenya-Mobile-Money-Analysis
# Kenya Mobile Money Transactions Analysis

## 📊 Project Overview

This project analyzes **6,000 mobile money transactions** from Kenya spanning **January 1, 2024 to December 31, 2024**. The dataset captures real-world mobile money activity across multiple platforms (M-Pesa, Airtel Money, Equitel, T-Kash), providing insights into transaction patterns, customer behavior, revenue trends, and regional activity across Kenya's 47 counties.

The analysis is performed using **Python** with **Pandas**, **Matplotlib**, and **Seaborn** in the accompanying Jupyter Notebook (`analysis.ipynb`).

---

## 📁 Repository Structure

```
├── Data/
│   └── kenya_mobile_money_transactions.csv    # Raw transaction dataset
├── analysis.ipynb                             # Jupyter Notebook with full analysis
├── .gitignore                                 # Excludes virtual environment
└── README.md                                  # Project documentation
```

---

## 🗂️ Dataset Description

The dataset contains **16 columns** covering transaction details, customer demographics, and channel information:

| Column | Description |
|---|---|
| `transaction_id` | Unique transaction identifier (e.g., TXN0000142) |
| `transaction_timestamp` | Date and time of transaction (2024) |
| `customer_id` | Unique customer identifier |
| `customer_name` | Customer's full name |
| `gender` | Male / Female |
| `age` | Customer age |
| `county` | Kenyan county of transaction |
| `phone_number` | Customer phone number |
| `channel` | Mobile money platform (M-Pesa, Airtel Money, Equitel, T-Kash) |
| `transaction_type` | Buy Goods, Send Money, Withdraw Cash, Deposit Cash, Pay Bill, Airtime, Reversal |
| `merchant_category` | e.g., Hardware, Restaurant, Fuel Station, Pharmacy, Insurance, School Fees |
| `device_type` | Feature Phone, Android, iOS |
| `amount_kes` | Transaction amount in Kenyan Shillings |
| `transaction_fee_kes` | Fee charged for the transaction |
| `balance_after_kes` | Account balance after transaction |
| `status` | Completed, Failed, Reversed |

**Note:** `merchant_category` contains **3,551 missing values** — these correspond to non-merchant transaction types (e.g., Send Money, Deposit, Withdraw).

---

## 🔍 Analysis Performed

### 1. Monthly Fee Revenue & MoM Growth
- Aggregated `transaction_fee_kes` by calendar month (Completed transactions only).
- Computed month-over-month percentage change using `pct_change()`.
- **Finding:** The fastest-growing month was **May 2024 (+11.18%)**, while **June 2024 saw the steepest decline (−14.81%)**.

### 2. Day-of-Week × Hour Transaction Heatmap
- Built a pivot table of transaction counts by weekday and hour.
- **Finding:** The single busiest hour block is **Wednesday at 9 AM (69 transactions)**.

### 3. Top 3 Customers per County
- Ranked customers within each county by total `amount_kes` using `groupby().rank()`.
- **Finding:** Top spenders include **Mumbi Karanja (Nairobi, KES 552,653)**, **Njeri Kamau (Kajiado, KES 552,341)**, and **Anyango Onyango (Mombasa, KES 555,051)**.

### 4. Daily Volume vs. 7-Day Rolling Average
- Resampled transactions to daily counts and computed a 7-day rolling mean.
- Flagged days where daily volume exceeded **1.5× the rolling average**.

---

## 🛠️ Technologies Used

- **Python 3.13**
- **Pandas** — data manipulation & time-series analysis
- **Matplotlib** — static visualizations
- **Seaborn** — statistical plots
- **Jupyter Notebook** — interactive analysis

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas matplotlib seaborn jupyter
```

### Running the Analysis
1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/kenya-mobile-money-analysis.git
   cd kenya-mobile-money-analysis
   ```
2. Launch Jupyter:
   ```bash
   jupyter notebook analysis.ipynb
   ```
3. Run all cells to reproduce the analysis and visualizations.

---

## 📈 Key Insights Summary

- **Channels:** M-Pesa dominates transaction volume, followed by Airtel Money, Equitel, and T-Kash.
- **Peak Activity:** Weekday mornings (6 AM – 9 AM) and lunch hours show the highest transaction density.
- **Geographic Hotspots:** Nairobi, Mombasa, Kisumu, and Nakuru account for the highest transaction values.
- **Transaction Success:** The vast majority of transactions are **Completed**, with a small portion **Failed** or **Reversed**.
- **Age Range:** Customers span from teenagers (18) to seniors (72+), with the bulk in the 30–60 age range.
