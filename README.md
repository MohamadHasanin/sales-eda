# Sales Data Analysis

Data cleaning and analysis project for B2B sales data covering 2003-2005, examining revenue patterns, geographic distribution, and operational issues across 307 orders.

## Dataset

| Dataset                    | Rows  | Focus                              |
|----------------------------|-------|------------------------------------|
| `sales_data_sample.csv`    | 2,823 | Order line items (B2B sales)       |

**Scope:** 307 unique orders, 92 customers, 19 countries, 7 product lines  
**Period:** January 2003 - May 2005 (2005 incomplete)

## What's Done

**Data Cleaning**
- No duplicates found (verified at row and order+line level)
- Null values in optional address fields (ADDRESSLINE2, STATE, POSTALCODE, TERRITORY) filled with empty strings
- ORDERDATE converted to datetime64, validated against YEAR_ID, MONTH_ID, QTR_ID (0 mismatches)
- Dtype optimisation (float64 → uint8/uint16 for 7 columns)
- PRICEEACH data quality issue identified and corrected (recalculated from SALES ÷ QUANTITYORDERED)

**Analysis**
- Year-over-year growth: +34.3% from 2003 to 2004
- Seasonality identified: Q4 sales approximately double Q3 sales
- Geographic breakdown: USA leads at 36.5% of orders, Madrid top city ($1.08M revenue)
- Product concentration: Classic Cars dominate at 39% of revenue
- Customer concentration: Healthy distribution, top customer at 9% (no dependency risk)
- Operational anomaly: 81.82% of fulfillment issues concentrated in Q2 2005 (3.6× higher failure rate than baseline)

## Key Findings

**Q2 2005 Operational Disruption**  
Despite Q2 representing only 22.8% of typical order volume, 81.82% of all fulfillment issues (Cancelled, Disputed, On Hold) occurred in Q2 2005. This represents a systemic operational problem requiring investigation of Q2 2005 logs, staffing, and supply chain events.

**Revenue Drivers**  
Classic Cars product line drives 39% of revenue with no customer over-concentration (top customer = 9%). Strong Q4 seasonality pattern consistent across years suggests holiday-driven demand.

## Project Structure

```
sales-eda/
├── data/
│   ├── sales_data_sample.csv
│   └── generated/
│       └── sales_data_sample_Clean.csv
├── notebooks/
│   ├── sales-cleaning.ipynb
│   └── sales-analysis.ipynb
└── README.md
```

## Setup

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

Then open notebooks in order:
1. `sales-cleaning.ipynb` — data quality checks, dtype optimisation, PRICEEACH correction
2. `sales-analysis.ipynb` — revenue trends, geographic breakdown, operational issues

## Stack

Python · pandas · numpy · matplotlib · seaborn

## Data Source

Sample sales dataset from [Kaggle](https://www.kaggle.com/datasets/kyanyoga/sample-sales-data)
