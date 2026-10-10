# E-Commerce Orders: Data Cleaning and Exploratory Data Analysis

**DecodeLabs Data Analytics Internship, Projects 1 and 2 (Batch 2026)**
Tool: Microsoft Excel | By [Your name] | [LinkedIn](https://linkedin.com/in/pamilerinilesanmi) | [GitHub](https://github.com/pamskid)

> This is a practice dataset from the internship. The numbers describe this dataset, not a real business.

---

## The short version

**61% of order value never becomes revenue.** Out of $1.26M in orders, only $489K was shipped or delivered. The rest was pending, cancelled or returned.

**Monthly revenue jumps around a lot.** January to June 2025 averaged about 26% less per month than the same months in 2024. But the months vary so much that I can't call it a steady decline.

---

## 1. What I wanted to find out

Project 1 was about whether I could trust the data. Project 2 was about what the data says.

I looked at what a typical order looks like, whether any orders are unusual, how revenue changes over time, and where order value gets lost.

## 2. The data

- 1,200 orders from January 2023 to June 2025
- 14 original columns (order, customer, product, quantity, price, status, coupon, referral source and so on)
- 3 columns I added: Year, Month and NetRevenue (NetRevenue only counts Shipped and Delivered orders)

## 3. What I did

### Project 1: cleaning (details in `Data_Cleaning_Change_Log.pdf`)

| What I checked | What I found | What I did |
|---|---|---|
| Duplicate orders | 0 duplicate rows and 0 duplicate Order IDs | Nothing needed |
| Missing values | 309 blank coupon codes | Labeled them "NoCoupon" instead of deleting the rows |
| Number precision | 29 prices with tiny rounding errors | Rounded them to 2 decimals |
| Dates | All 1,200 were already real dates | Formatted them as yyyy-mm-dd |
| Text | No extra spaces or spelling variations | Nothing needed |

I didn't delete any rows. There were 1,200 before and after.

### Project 2: exploring the data (the `EDA` tab)

1. **Basic statistics:** count, mean, median, standard deviation, quartiles, min, max and skewness for Quantity, UnitPrice, ItemsInCart and TotalPrice.
2. **Outliers:** I used two methods. The IQR method flags values far outside the middle 50% of the data. The Z-score flags values more than 3 standard deviations from the mean. I mainly used IQR because order values are skewed.
3. **Correlation:** how strongly the numeric columns move together.
4. **Histogram:** order values in $500 bins.
5. **Trend:** monthly net revenue, a comparison of January to June in each year, and a straight-line trend with a p-value.

All the numbers on the EDA tab come from Excel formulas that read the `Data` tab, so I can trace each one back.

## 4. What I found

**1. The typical order is $824, not $1,054.** The median order is $824 and the mean is $1,054. Order values are skewed to the right (skewness 0.89), so a few big orders pull the average up. 57% of orders are under $1,000.

**2. No bad numbers, but 8 big orders stand out.** Quantity, UnitPrice and ItemsInCart have no outliers. Eight orders are above $3,330, which is the IQR limit. All eight are 5-unit orders, so they look like genuine big orders and I kept them.

**3. October 2023 was the strongest month.** It made $36.9K, above the IQR limit of about $30.3K. It pushes up the 2023 average, so 2023 isn't a fair baseline.

**4. Monthly revenue jumps around a lot.**

| Period | Average per month |
|---|---|
| Jan to Jun 2023 | $16.9K |
| Jan to Jun 2024 | $16.5K |
| Jan to Jun 2025 | $12.3K |

The first half of 2025 is about 26% below the first half of 2024 and 27% below 2023. Across all 30 months the line slopes down by about $137 a month, but the p-value is 0.35, so that could easily be chance.

**5. Where the 2025 drop comes from.** Orders placed only fell about 3% (237 to 231). But fulfilled orders went from 100 to 85, and the average fulfilled order went from $991 to $867.

**6. Most correlations are expected.** TotalPrice moves with UnitPrice (0.72) and Quantity (0.62), but that's because TotalPrice is Quantity times UnitPrice. UnitPrice is barely related to anything else (0.01 with Quantity).

## 5. What I'd suggest

1. Show the median next to the mean for order value, and use the IQR method for outliers on skewed columns like TotalPrice.
2. Find out why 61% of order value never turns into revenue. Pending, returned and cancelled orders are each about 20% of orders, which matters more than the small gaps between products and channels.
3. Find out what happened in October 2023 before using 2023 as a baseline, and compare matching periods (like January to June with January to June) in future reports.

## 6. Limits

- This is practice data, and the gaps between products and referral sources are small, so I wouldn't read too much into them.
- There's no cost data, so I can't work out profit.
- Coupon discounts aren't included in TotalPrice, so the coupon analysis only compares order size.
- 487 cancelled or pending orders have a tracking number. That came from the source data and I left it alone.
- 10 orders have a unit price under $20. They look believable, so I left them in.

## 7. What's in this repository

| File | What it is |
|---|---|
| `E-Commerce_Sales_Analysis_internship.xlsx` | The workbook, with tabs for README, Dashboard, Analysis, EDA, Pivot and Data |
| `Data_Cleaning_Change_Log.pdf` | The Project 1 change log: what I changed, why, and what it affected |
| `images/` | Screenshots of the Dashboard and the EDA tab |

## 8. How to use the workbook

1. Start with the `README` tab, which explains each tab.
2. The `Dashboard` has the main numbers and charts.
3. The `EDA` tab has my Project 2 work: statistics, outliers, correlation, histogram and observations.
4. `Data` is the cleaned table. The other tabs read from it, so changing a value there updates everything.
5. On the `Pivot` tab, use the Year and Product slicers to filter. Clear them to see all months.
