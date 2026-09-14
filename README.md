
# Supply Chain & Logistics Performance Dashboard | Power BI
<img width="1409" height="792" alt="image" src="https://github.com/user-attachments/assets/a16a71e8-756a-4802-a6b6-809f02a92b92" />


## 📌 Project Overview
An end-to-end Power BI business intelligence solution built on the **DataCo Smart Supply Chain** dataset. This dashboard provides supply chain managers and operations leads with complete visibility into logistics bottlenecks, revenue streams, order fulfillment cycles, and high-risk delivery channels.

---

## 📊 Key Operational Insights & Metrics
* **Financial Scale:** Generated **$36.78M** in total revenue with **$3.97M** in operating profit across **66,000 distinct orders**.
* **Delivery Bottleneck:** The overall **Late Delivery Rate stands at 54.83%**, representing a significant service-level risk that impacts customer retention.
* **The Expedited Shipping Paradox:** 
  * **First Class** shipping experienced an alarming **95.32%** delay rate.
  * **Second Class** recorded a **76.63%** delay rate.
  * **Standard Class** proved to be the most reliable tier with only **38.07%** late deliveries.
* **Geographic Revenue Concentration:** **Western Europe ($5.9M)** and **Central America ($5.7M)** represent over 31% of total global sales.
* **Top Product Categories:** **Fishing ($6.93M)**, **Cleats ($4.43M)**, and **Camping & Hiking ($4.12M)** drive top-line revenue.

---

## 🛠️ Data Architecture & Modeling
* **Data Cleansing (Power Query):**
  * Filtered an initial 50+ column schema down to 13 high-impact operational fields.
  * Converted scheduling and transit timestamps into standardized date hierarchies.
  * Audited numerical types across profit calculations and transit days.
* **Core DAX Measures:**
  * **Late Delivery Rate:**
    ```dax
    Late Delivery Rate = 
    DIVIDE(
        CALCULATE(COUNTROWS('DataCoSupplyChainDataset'), 'DataCoSupplyChainDataset'[Late_delivery_risk] = 1),
        COUNTROWS('DataCoSupplyChainDataset'),
        0
    )
    ```
  * **Total Sales:**
    ```dax
    Total Sales = SUM('DataCoSupplyChainDataset'[Sales])
    ```
  * **Total Profit:**
    ```dax
    Total Profit = SUM('DataCoSupplyChainDataset'[Order Profit Per Order])
    ```
  * **Distinct Orders:**
    ```dax
    Total Orders = DISTINCTCOUNT('DataCoSupplyChainDataset'[Order Id])
    ```

---

## 📈 Dashboard Layout & Visual Structure
1. **Executive KPI Cards:** Immediate status check on Total Sales, Total Profit, Order Volume, and Delivery Failure Rate.
2. **Orders by Delivery Status (Donut Chart):** Visual segmentation of order outcomes (Late Delivery, Advance Shipping, On Time, Canceled).
3. **Late Delivery Rate by Shipping Mode (Bar Chart):** Critical analysis identifying systemic delays across express transit tiers.
4. **Geographic Revenue Distribution (Horizontal Bar):** Ranking order regions by sales contribution.
5. **Product Category Breakdown (Matrix):** Tabular revenue summary across merchandising departments.
6. **Dynamic Slicers:** Instant drill-down by `Year` and `Department Name`.

---

