# Sales & Profit Performance Dashboard

My first Power BI project, built using Microsoft’s Financial Sample dataset. I used it to explore a straightforward question: ** are the products and markets generating the most sales also the most profitable?**

![Sales and Profit Performance Dashboard](dashboard.png)

[View dashboard PDF](Sales_Profit_Dashboard.pdf) · [Download Power BI report](Sales_Profit_Dashboard.pbix)

## Project overview

The report brings together sales, profit, and profit margin in one page. It includes:

- KPI cards for total sales, total profit, and profit margin.
- Monthly sales trends.
- Sales comparisons across countries.
- Profit and sales share by customer segment.
- A product table comparing sales, profit, and margins.
- A Country slicer for exploring individual markets.

## Main findings

### 1. Higher sales do not always mean a higher margin

Paseo generated the most product sales at **$33.01 million**, approximately **27.8% of total sales**. It also contributed the highest product profit at **$4.80 million**.

Amarilla, however, had the highest profit margin at **15.86%**, compared with Paseo’s **14.53%**.

This gives two different perspectives on performance. Paseo contributes more total profit, while Amarilla earns more profit per dollar of sales. I would consider both measures before recommending which product to prioritize.

### 2. France earned more profit than Canada despite lower sales

| Metric | Canada | France |
|---|---:|---:|
| Sales | $24.89M | $24.35M |
| Profit | $3.53M | $3.78M |
| Profit margin | 14.18% | 15.53% |

Canada generated slightly more revenue, but France converted a larger share of its sales into profit.

This comparison shows why I included profit margin alongside sales. Ranking countries by revenue alone would miss that difference.

### 3. Enterprise needs further investigation

Government contributed the most segment profit, followed by Small Business. Enterprise recorded a loss despite generating sales.

I would investigate Enterprise first by comparing discounts, costs, and product performance within the segment. The report shows where the loss occurs, but it does not explain its cause.

### 4. Monthly sales were uneven

The trend shows several peaks and declines rather than consistent growth. A useful follow-up would be to break those months down by product and segment to understand what changed.

I would need a longer period of data before describing these movements as seasonality.

## Overall results

| Metric | Result |
|---|---:|
| Total sales | $118,726,350.26 |
| Total profit | $16,893,702.26 |
| Profit margin | 14.23% |

## Data preparation

I imported the Excel workbook and used Power Query to inspect column quality, trim text fields, and review data types.

I retained decimal values in Units Sold and negative profit values rather than changing them to make the data look cleaner. I also created a Month Start column to group records by month while keeping different years separate.

## Calculations

The report uses these DAX measures:

```dax
Total Sales =
SUM('financials'[Sales])

Total Profit =
SUM('financials'[Profit])

Profit Margin % =
DIVIDE([Total Profit], [Total Sales], 0)
```

Profit margin is calculated from total profit and total sales, rather than by averaging individual row margins.

For the monthly trend, I created this calculated column:

```dax
Month Start =
DATE(
    YEAR('financials'[Date]),
    MONTH('financials'[Date]),
    1
)
```

## What I would investigate next

- Which products and discount bands contribute most to Enterprise losses?
- Does Amarilla’s higher margin hold across individual countries?
- Which products or segments explain the largest monthly sales changes?

These questions would help turn the initial findings into more specific recommendations.

## Files and viewing instructions

- **dashboard.png:** Unfiltered overview of the report.
- **Sales_Profit_Dashboard.pdf:** Additional dashboard views showing selected countries and segments.
- **Sales_Profit_Dashboard.pbix:** Interactive report for Power BI Desktop.

The image and PDF are static. Open the PBIX in Power BI Desktop to use the slicer and chart selections.

Some PDF views include segment selections. Faded bars show the wider comparison, while highlighted portions indicate the selected segment.

To refresh the report on another computer, download the source workbook and update its location through **Transform data → Data source settings → Change Source**.

## Tools and source

**Tools:** Power BI Desktop, Power Query, DAX, Microsoft Excel.

**Source:** [Microsoft Financial Sample workbook](https://learn.microsoft.com/en-us/power-bi/create-reports/sample-financial-download).

This project uses sample data for learning and portfolio demonstration. The findings describe the sample and are not conclusions about a real business.
