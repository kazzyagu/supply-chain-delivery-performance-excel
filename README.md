# supply-chain-delivery-performance-excel
Excel analysis of late deliveries in the DataCo supply chain dataset: pivot tables, a dashboard and three recommendations.


# Supply Chain Delivery Performance Analysis (Excel)

An end-to-end Excel analysis of delivery performance using the DataCo Smart Supply Chain dataset. The project cleans the raw data, answers business questions with pivot tables, presents the findings on an interactive dashboard, and ends with three recommendations for management.

## Business questions

1. How many orders are delivered late?
2. What percentage of orders are late?
3. Which shipping methods, markets and product categories have the most late deliveries?
4. What should management do to improve supply chain performance?

## Dataset

- **Source:** DataCo Smart Supply Chain dataset ([add the link to where you downloaded it])
- **Size:** about 180,000 order-item rows, about 65,700 unique orders
- **Note:** the raw file is not included in this repository. Download it from the source above.

## Tools and skills used

- Excel: PivotTables, Data Model (Distinct Count), slicers, PivotCharts
- Formulas: COUNTIF, SUM, SUMPRODUCT, GETPIVOTDATA, IF
- Data cleaning: duplicate checks, standardising text values, helper columns
- Dashboard design: KPI cards, linked charts, interactive filters

## Method

1. **Cleaned the data.** Checked for blanks and duplicates, translated Spanish country names into English with a lookup table, and reviewed columns that carried no information.
2. **Defined the metrics.** Counted unique orders (Distinct Count of Order Id) instead of rows, because one order can contain several products.
3. **Defined "delivered".** Used Order Status = COMPLETE + CLOSED and excluded canceled orders. Results for COMPLETE only are also shown in the analysis for comparison.
4. **Created a Delay Days column** (real shipping days minus scheduled shipping days) to measure how late orders were.
5. **Built pivot tables** for late orders and late rates by shipping method, market, region, product category and time.
6. **Built the dashboard** and wrote the recommendations.

## Key findings

Basis: Order Status = COMPLETE + CLOSED, excluding canceled orders.

| Measure | Result |
|---|---|
| Orders | 28,965 |
| Late orders | 16,633 |
| Late rate | 57.4% |
| Average delay of late orders | 1.6 days |

**Late rate by shipping modes**

| Shipping method | Scheduled days | Real days (avg) | Late rate |
|---|---|---|---|
| First Class | 1 | 2.0 | 100% |
| Second Class | 2 | 4.0 | 80.1% |
| Same Day | 0 | 0.5 | 48.5% |
| Standard Class | 4 | 4.0 | 39.8% |

- Premium shipping methods are promised faster than they are delivered, so they are late by design.
- The late rate stays between about 56% and 59% across markets, months, weekdays and quarters, so the issue is company-wide rather than regional or seasonal.
- Most late orders miss their scheduled date by only 1 to 2 days.
- Cleats, Men's Footwear and Women's Apparel have the most late orders. These are counts, so they partly reflect order volume.

## Recommendations

1. **Reset the promised delivery times for First Class and Second Class** so they match real performance, or improve fulfillment until the promise is met.
2. **Treat lateness as a company-wide process issue.** Review dispatch and carrier handoff steps and set a target late rate.
3. **Fix how delivery status is recorded and track it monthly.** Late delivery is recorded on orders that are still pending payment or processing, which makes the status unreliable.

## Dashboard

![Dashboard]()

## Repository contents

- `Supply_Chain_Analysis.xlsm` - workbook with the Clean_Data, Analysis, Dashboard and Recommendations sheets
- `images/` - screenshots of the dashboard and key pivot tables

## Limitations

- "Delivered" is not defined in the dataset, so I used COMPLETE + CLOSED. This is an assumption. The late rate is similar under either definition (about 58% vs 57%).
- Product category counts overlap, because an order with items in several categories appears under each one.
- The delivery status appears on orders that cannot have shipped yet, so the data may be synthetic. Treat the results as a demonstration of method rather than conclusions about a real company.

## Author

Kingsley Agu - [https://www.linkedin.com/in/coachkcagu/?isSelfProfile=true] - kazzyagu at gmail com
