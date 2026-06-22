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
The queries used to extract and aggregate the BigQuery dataset can be found below:

WITH Chicago_Delays AS (
  select
    airline,
    departure_airport,
    departure_delay,
  from `bigquery-samples.airline_ontime_data.flights`
  where departure_airport = 'ORD' 
    and departure_delay > 0
    and date >= '2008-01-01'
)

select
  airline, 
  count(departure_delay) as total_delayed_flights,
  round(avg(departure_delay), 2) AS avg_delay_mintues
from Chicago_Delays
group by airline
order by total_delayed_flights desc;


select
  airline,
  count(date) AS total_flights,
  sum(case when departure_delay > 15 then 1 else 0 end) as late_flights,
  round(
    (sum(case when departure_delay > 15 then 1 else 0 end) / count(date)) * 100, 2
  ) AS percent_late
from `bigquery-samples.airline_ontime_data.flights`
where departure_airport = 'ORD'
  and date >= '2008-01-01'
group by airline
having total_flights > 100
order by percent_late DESC;


select
  arrival_airport AS destination,
  count(date) AS total_flights,
  round(avg(arrival_delay), 2) AS avg_arrival_delay_minutes,
  max(arrival_delay) AS worst_arrival_delay
from `bigquery-samples.airline_ontime_data.flights`
where departure_airport = 'ORD'
  and date >= '2008-01-01' 
  and arrival_delay IS NOT NULL
group by arrival_airport
having total_flights > 100
order by avg_arrival_delay_minutes desc
limit 15;
