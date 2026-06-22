# ✈️ Chicago O'Hare (ORD) Flight Delay & Operations Analysis

## 🎯 Project Objective
Operational efficiency is the lifeblood of the aviation industry. Every minute a plane sits on the tarmac or delays at the gate, it disrupts cascading flight schedules and increases costs. This project analyzes over 1.5 million flight records departing from Chicago O'Hare (ORD) to identify key operational bottlenecks, evaluate carrier on-time performance (OTP), and pinpoint problem routes.

## 🛠️ Tools & Technologies
* **Google BigQuery:** Queried and aggregated massive datasets using cloud data warehousing.
* **Looker Studio:** Designed an executive-facing interactive dashboard for stakeholder reporting.
* **SQL Dialect:** Standard SQL 
* **Key SQL Skills:** Conditional Aggregations (`CASE WHEN`), Data Type Formatting, Post-Aggregation Filtering (`HAVING`), Mathematical Aggregations (`AVG`, `SUM`, `COUNT`).

## 📊 Executive Dashboard

![Executive Dashboard]
<img width="1687" height="1257" alt="Screenshot 2026-06-22 11 31 27 AM" src="https://github.com/user-attachments/assets/41cc0aa3-4383-4828-bbf4-308177a169a5" />

## 💡 Business Questions Answered
1. **Carrier Performance:** Which airlines have the highest departure delay rates (>15 minutes) leaving Chicago, indicating potential ground crew or turnaround inefficiencies?
2. **Geographic Bottlenecks:** Which of the top 15 destinations are causing the most severe arrival delays, highlighting broader airspace or routing bottlenecks?
3. **Volume vs. Reliability:** How do the delay rates of high-frequency carriers compare to smaller regional airlines?

## 💻 The SQL Code
The queries used to extract and aggregate the BigQuery dataset can be found here:
* [View the BigQuery SQL Analysis Scripts](chicago_otp_queries.sql)
