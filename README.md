# E-Commerce Sales and Customer Analysis — Python

## Executive Summary

This project analyzes the UCI Online Retail transaction dataset with Python and Pandas. It covers December 2010 through December 2011 and studies sales patterns, products, countries, customer concentration, and rule-based RFM segments.

| Snapshot measure | Result |
|---|---:|
| Source rows | 541,909 |
| Rows retained after cleaning | 397,884 |
| Customers with a CustomerID | 4,338 |
| Unique invoices | 18,532 |
| Revenue on retained positive-sales rows | £8,911,407.90 |
| Average revenue per invoice | £480.87 |

The revenue figure is not net of returns: negative-quantity rows are excluded rather than subtracted.

## Business Problem

An e-commerce team needs to understand where recorded sales are concentrated and which customers may merit further retention analysis. The project helps frame decisions about market concentration, seasonal planning, and customer outreach; it does not measure the effect of a campaign or prove future churn.

Questions addressed:

- How does recorded sales value vary by month?
- Which countries and products contribute most to the included sales?
- How concentrated is sales value across customers?
- How can RFM metrics group customers for further investigation?

## Methodology

1. Load the external transaction CSV into Pandas.
2. Exclude rows without a CustomerID and remove rows with non-positive quantity or unit price.
3. Parse invoice dates and calculate row-level sales value.
4. Aggregate sales by month, country, product, invoice, and customer.
5. Calculate customer RFM measures and assign quintile-based scores with rule-based segment labels.

| Metric | Definition used |
|---|---|
| Revenue | `Quantity × UnitPrice` for retained positive-quantity, positive-price rows |
| Average revenue per invoice | Retained-row revenue divided by distinct InvoiceNo count |
| Recency | Days since a customer's latest included invoice at the notebook's reference date |
| Frequency | Distinct invoice count per customer |
| Monetary | Sum of retained-row revenue per customer |

The dataset's negative quantities include returns, but this project excludes them. It also excludes rows without CustomerID, so these results describe the retained, customer-identifiable positive-sales records.

## Skills

- **Python:** Pandas, NumPy, Jupyter
- **Visualization:** Matplotlib and Seaborn
- **Customer analysis:** RFM feature design, quintile scoring, rule-based segments
- **Analytics:** transaction cleaning, sales aggregation, customer and market comparisons

## Results & Business Recommendation

| Evidence in the analysis | Practical follow-up |
|---|---|
| The United Kingdom contributes about £7.31M of the £8.91M retained-row revenue. | Review market concentration and compare customer behavior across other countries before planning expansion. |
| November 2011 is the highest-revenue month at about £1.16M. | Use it as a planning signal; one year of data cannot establish a recurring seasonal pattern. |
| Product rankings differ when comparing units sold and sales value. | Review both measures instead of using sales value alone to make assortment decisions. |
| The RFM rules label 1,673 customers “At Risk.” | Treat this as a segment for investigation, not a validated churn prediction; test any retention action before scaling it. |

The RFM labels are rule-based. The analysis does not establish that a customer will churn, that any market is under-served, or that a proposed campaign will increase revenue.

### Visual

![Monthly revenue trend](https://erskm.github.io/assets/projects/ecommerce-monthly-revenue.png)

## Next Steps

1. Include negative-quantity rows in a separate returns analysis and calculate net sales with an explicit return definition.
2. Compare more than one year before making seasonal claims.
3. Validate RFM thresholds against later customer activity.
4. Measure retention campaigns with a defined control or comparison group.
5. Add margin or product cost data before making profitability recommendations.

### Run the notebook

1. Download the [Online Retail dataset](https://www.kaggle.com/datasets/carrie1/ecommerce-data).
2. Save the CSV as `data/ecommerce.csv` in this repository.
3. Install dependencies: `python -m pip install pandas matplotlib seaborn jupyter`.
4. Start Jupyter from the repository root and run `ecommerce_analysis.ipynb` from top to bottom.

The data file is ignored by Git because it is an external source dataset.

**Author:** Salahuddin K M · [Portfolio](https://erskm.github.io) · [GitHub](https://github.com/ErSKM)
