📊 Power BI Shopify Sales Dashboard

🧾 Project Overview

This Power BI project presents an interactive stock market analysis dashboard built from stock-volume and date-based data.

The dashboard focuses on:

📈 Stock Close Price

📊 Trading Volume

📉 20-Day Moving Average

📉 50-Day Moving Average

💰 Latest Close Price

🔻 Lowest Price

🔺 Highest Price

📅 Interactive Date filtering

Screenshot 2026-09-25 145323
The report contains a single dashboard page with cards, charts, and a date slicer.

💰 Close Price
Measure used in: - Close Price + 20-Day Moving Average chart - Close Price + 50-Day Moving Average chart

The measure provides the stock's closing-price value for the current date/filter context.

💡 MAX() is commonly used when there is one closing-price value per stock/date context. The exact aggregation should match the structure of the source data.

📉 20-Day Moving Average
A moving average smooths daily price fluctuations by calculating the average closing price over a rolling 20-day window.

🔎 Analysis

DATESINPERIOD() creates the rolling date window.

-20 represents the 20-day lookback period.

AVERAGEX() calculates the average over that period.

[Close Price] is evaluated for each date.

The result smooths short-term price fluctuations.

📌 Purpose: Useful for observing the short-term trend rather than individual daily movements.

📉 50-Day Moving Average
Used in: Close Price + 50-Day Moving Average chart.

The 50-day moving average calculates the average closing price over a longer rolling period.

🔎 Analysis

The logic is similar to the 20-day moving average, but the window is longer.

🟢 20-day MA → shorter-term trend

🔵 50-day MA → longer-term trend

Comparing the two can help visualize changes in the direction of the price trend.

💰 Latest Close
Displays the closing price associated with the latest available date within the relevant filter context.

🔎 Analysis

LASTDATE() identifies the latest date.

CALCULATE() changes the filter context to that date.

[Close Price] then returns the closing price for that context.

🔻 Lowest Price
Displays the minimum closing price available within the current filter context.

🔎 Analysis

MINX() evaluates the closing price across the available dates and returns the smallest value.

📌 The result changes when the report is filtered by date.

🔺 Highest Price
Displays the maximum closing price available within the current filter context.

🔎 Analysis

MAXX() evaluates [Close Price] for the available dates and returns the largest value.

📌 This gives a quick view of the highest observed closing price in the selected period.

📦 Volume Calculation

The dashboard also uses the volume column from the ShopifyStock table.

The PBIX visual definition confirms that the volume chart/card uses:

SUM(ShopifyStock[volume])

🔎 Analysis

SUM() adds the trading-volume values for the current filter context.

For example:

Day 1 Volume

Day 2 Volume
Day 3 Volume
... = Total Volume
This allows the dashboard to show total/aggregated trading activity.

🔄 How the Measures Work Together

The dashboard combines the measures to provide several levels of analysis:

mermaid-diagram
🎛️ Date Filtering

The report contains a Date slicer based on:

Dim_Date[Date]

The slicer uses a Between date-selection mode.

Why it matters

Changing the selected date range can affect:

📊 Total volume

📈 Closing-price charts

📉 Moving averages

💰 Latest Close

🔻 Lowest Price

🔺 Highest Price

This makes the report interactive rather than a static chart.

📊 Data Model

The report references two important entities:

🗓️ Dim_Date

Used for:

Date axis

Date filtering

Time-based calculations

Moving-average calculations

Latest-date calculations

✨ Conclusion

This Power BI dashboard combines stock price, trading volume, time filtering, and moving-average analysis into an interactive report.

The use of 20-day and 50-day moving averages adds trend analysis, while the Latest Close, Highest Price, and Lowest Price cards provide quick KPI-style information.

The date slicer allows users to dynamically explore different time periods and observe how the calculated values change.
