# Hospitality Revenue Insights Analysis

## Overview
A technical analytics project that builds a hospitality revenue intelligence pipeline using hotel bookings and room inventory data. The repository includes dimension tables, booking transaction data, aggregated hotel performance metrics, and a dashboard-ready Power BI model.

## Repository Contents
- `dim_date.csv` — date dimension with calendar attributes for May, June, and July
- `dim_hotels.csv` — hotel metadata including property ID, name, category, and city
- `dim_rooms.csv` — room type dimension with room IDs and class tiers
- `fact_aggregated_bookings.csv` — daily hotel-room aggregated booking performance and capacity metrics
- `fact_bookings.csv` — transactional booking events with booking/platform, stay status, guest count, and revenue
- `meta_data_hospitality.txt` — column definitions and data dictionary for the dataset
- `Hospitality_Revenue.pbix` — Power BI report file for revenue insights and KPI dashboards
- `Hospitality_Domain_Revenue_Dashboard.pdf` — exported dashboard documentation snapshot
- `metrics-list.xlsx` — supporting metric definitions and measurement list

## Data Model
This project uses a classic star schema for hospitality analytics:
- `dim_date` as the time dimension
- `dim_hotels` as the hotel dimension
- `dim_rooms` as the room dimension
- `fact_aggregated_bookings` for daily capacity and booking summaries
- `fact_bookings` for individual booking transactions and revenue attribution

## Key Analytical Use Cases
- Revenue realization by hotel, room class, and booking status
- Capacity management and booking fulfillment tracking
- Channel/platform performance analysis
- Stay-duration and guest-count segmentation
- Cancellations and revenue leakage modeling

## How to Use
1. Open `Hospitality_Revenue.pbix` in Power BI Desktop.
2. Load the CSV files as source tables.
3. Build relationships:
   - `dim_date.date` → `fact_aggregated_bookings.check_in_date`
   - `dim_date.date` → `fact_bookings.check_in_date`
   - `dim_hotels.property_id` → `fact_aggregated_bookings.property_id`
   - `dim_hotels.property_id` → `fact_bookings.property_id`
   - `dim_rooms.room_id` → `fact_aggregated_bookings.room_category`
   - `dim_rooms.room_id` → `fact_bookings.room_category`
4. Use the dashboard visuals to explore revenue, booking success, and capacity metrics.

## What Makes This Project Technical
- Multi-table schema combining transaction and aggregate-level data
- Revenue realization logic accounting for booking status and cancellations
- Dashboard-ready data model with hotel, room, and date dimensions
- Cross-functional analytics for finance, operations, and revenue management

## Notes
- `revenue_generated` is the gross booking revenue.
- `revenue_realized` reflects net revenue after cancellation deductions.
- `booking_status` drives realized revenue, including `Checked Out`, `No show`, and `Cancelled`.

## Recommended Next Steps
- Add DAX measures for revenue per available room (RevPAR) and average daily rate (ADR)
- Implement booking lead time and customer acquisition channel analysis
- Extend the model with seasonality and occupancy forecasting
- Add data quality validation for date ranges and room capacity consistency

