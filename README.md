# E-Commerce Sales and Customer Analysis

A Python analysis of the UCI Online Retail transactions dataset. The notebook cleans transaction records, measures sales performance, explores products and countries, and creates customer segments with Recency, Frequency, and Monetary (RFM) metrics.

## Project snapshot

| Metric | Result |
|---|---:|
| Source rows | 541,909 |
| Rows retained after cleaning | 397,884 |
| Unique customers | 4,338 |
| Unique invoices | 18,532 |
| Sales revenue in the cleaned data | £8,911,407.90 |
| Average revenue per invoice | £480.87 |

The dataset covers December 2010 through December 2011. Revenue is calculated as `Quantity × UnitPrice` for positive-quantity, positive-price records. Rows without a CustomerID are excluded, and negative quantities (including returns) are not netted against sales. The results therefore describe the retained positive-sales records, not net revenue after returns.

## Business questions

- How does monthly revenue change over the observed period?
- Which countries contribute the most revenue?
- Which products lead by units sold and by revenue?
- How concentrated is revenue among customers?
- How do customers differ by recency, frequency, and monetary value?

## Key findings

- The United Kingdom is the largest market in the cleaned data, contributing about **£7.31M** of **£8.91M** revenue.
- November 2011 is the highest-revenue month in the analysis at **£1.16M**.
- Product rankings differ by metric: the notebook compares units sold separately from sales revenue.
- RFM scoring segments 4,338 customers into **1,965 Average**, **1,673 At Risk**, **573 Best**, and **127 Loyal** customers. “At Risk” is a rule-based segment from this notebook’s recency score, not a validated churn prediction.

![Monthly revenue trend](https://erskm.github.io/assets/projects/ecommerce-monthly-revenue.png)

## Analysis workflow

1. Load the transaction data with Pandas.
2. Exclude rows without CustomerID and remove non-positive quantity or price records.
3. Parse invoice dates and calculate revenue.
4. Summarize invoices, customers, monthly revenue, countries, and products.
5. Calculate customer RFM measures and assign quintile-based scores and rule-based segments.
6. Turn the findings into retention, market, inventory, and seasonal planning questions.

## Run the notebook

1. Download the [UCI Online Retail dataset](https://www.kaggle.com/datasets/carrie1/ecommerce-data).
2. Save the CSV as `data/ecommerce.csv` in this repository. The data file is ignored by Git because it is an external source dataset.
3. Install the notebook dependencies:

   ```bash
   python -m pip install pandas matplotlib seaborn jupyter
   ```

4. Start Jupyter from the repository root and run `ecommerce_analysis.ipynb` from top to bottom.

## Repository structure

```text
ecommerce-sales-analysis/
├── data/
│   └── ecommerce.csv          # Download separately; ignored by Git
├── ecommerce_analysis.ipynb   # Cleaning, analysis, RFM, and recommendations
└── README.md
```

## Tools demonstrated

Python · Pandas · Matplotlib · Seaborn · Jupyter Notebook · RFM customer analysis

## Author

**Salahuddin K M** · [Portfolio](https://erskm.github.io) · [GitHub](https://github.com/ErSKM)
