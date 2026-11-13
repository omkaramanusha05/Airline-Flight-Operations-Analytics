# Airline Flight Operations Analytics Platform

## 1. Project Overview
This project analyzes airline flight operations using the Medallion Architecture in Databricks. The objective is to clean raw flight data, create trusted analytical tables, and build an interactive dashboard.

## 2. Technologies Used
- Databricks
- Lakeflow Spark Declarative Pipelines
- Databricks SQL
- Unity Catalog
- SQL
- Databricks AI/BI Dashboards

## 3. Dataset Details
- Dataset: `airline_flights_raw.csv`
- Total raw records: 1,365
- Data domain: Synthetic domestic airline flights
- Period: 2025

## 4. Medallion Architecture

### Bronze Layer
Stores the raw flight data.
- Table: `bronze_flights`
- Total records: 1,365

### Silver Layer
Cleans and validates the flight data.
- `silver_flights`: 1,321 clean records
- `silver_flights_rejected`: 19 rejected records
- Duplicate surplus records removed: 25

### Gold Layer
Contains aggregated tables for dashboard reporting.
- `gold_monthly_flights`
- `gold_airline_summary`
- `gold_route_summary`
- `gold_delay_summary`
- `gold_data_quality`

## 5. Data Cleaning Rules
- Removed duplicate flight IDs, keeping one record per flight ID.
- Standardized text fields using trimming and capitalization.
- Calculated missing delay values using scheduled and actual departure times.
- Calculated ticket revenue using passengers multiplied by average fare.
- Rejected flights with passengers exceeding seat capacity.
- Rejected records with negative average fares.
- Classified flights into On Time, Minor Delay, and Major Delay categories.

## 6. Data Quality Reconciliation

| Category | Records |
|---|---:|
| Bronze Records | 1,365 |
| Clean Silver Records | 1,321 |
| Rejected Records | 19 |
| Duplicate Surplus | 25 |
| Total Accounted | 1,365 |

**Reconciliation:** 1,365 = 1,321 + 19 + 25

**Data Quality Status: BALANCED**

## 7. Delay Analysis

| Delay Category | Flights |
|---|---:|
| On Time | 902 |
| Minor Delay | 284 |
| Major Delay | 135 |
| Unknown | 0 |

## 8. Dashboard
Created and published one Databricks AI/BI Dashboard with three pages:

1. **Overview** – Total flights, passengers, ticket revenue, delayed flights, monthly revenue trend, and airline on-time performance.
2. **Airlines, Routes & Delays** – Airline performance, top 10 routes by revenue, delay categories, and delay reasons.
3. **Data Quality** – Bronze, clean, rejected, and duplicate counts with reconciliation status.

The dashboard uses the five Gold tables and contains 16 widgets.

## 9. Project Outcome
The pipeline successfully transforms 1,365 raw records into 1,321 clean records, identifies 19 rejected records, and accounts for 25 duplicate surplus records. The Gold tables support airline performance, route, delay, and data-quality analysis.

## 10. Conclusion
This project demonstrates an end-to-end data engineering and analytics workflow using Databricks, SQL, Lakeflow Spark Declarative Pipelines, Medallion Architecture, and AI/BI Dashboards.

## 11. Published Dashboard

[View Airline Flight Operations Dashboard](https://dbc-f9964a2c-ce6c.cloud.databricks.com/dashboardsv3/01f1df8275851f3fa0c19ab9a2dee552/published?o=7474655349553641)
