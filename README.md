# Decodelabs-Internship E-Commerce Sales Analysis (Excel)

An Excel workbook analysing 1,200 e-commerce orders (Jan 2023 - Jun 2025) to show which products and referral sources drive revenue, and how much revenue is lost to cancellations and returns.

## Key findings
- 61% of order value never becomes revenue (Cancelled, Returned, Pending).
- Printer and Laptop lead net revenue; Desk is lowest.
- Instagram has the lowest cancel rate (15.8%); Google the highest (24.1%).
- Average monthly net revenue fell from ~$18.0K (2023) to ~$12.3K (H1 2025).

## Workbook structure
- README: business question and assumptions
- Dashboard: KPI cards, 4 charts, key findings
- Analysis: formula-driven summary tables (SUMIFS, COUNTIFS, SUMPRODUCT)
- Pivot: net revenue by month with Year and Product slicers
- Data: cleaned dataset as an Excel Table with helper columns
  (Year, Month, NetRevenue)

## Method
Net revenue counts only Shipped and Delivered orders. Coupon discounts are not applied in the source data.

## Data
Practice e-commerce dataset, cleaned by me. Findings are illustrative, not real business results.

## Tools
Excel: Tables, formulas, charts, pivot tables, slicers
