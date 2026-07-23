# Car-Rental-Business-Intelligence-Dashboard
# Overview

This project is an interactive Power BI dashboard developed to analyze the operational and financial performance of a car rental company. Using transactional rental data, the dashboard provides insights into revenue trends, customer demographics, vehicle utilization, and geographic rental activity to support data-driven business decisions.

The project demonstrates the use of data modeling, DAX calculations, Power Query transformations, and interactive dashboard design to transform raw rental data into actionable business intelligence.

# Dashboard Preview

[Click here to view my dashboard](CarRentalDashboard.pdf)

[Click here to view my star schema](CarRentalStarSchema.png)

# Business Problem

A car rental company wants to better understand its rental operations and revenue performance. Management needs an interactive dashboard that allows them to:

- Monitor rental activity over time
- Track total rental revenue
- Compare vehicle brands by revenue generated
- Analyze customer demographics
- Identify geographic patterns in rental demand
- Support strategic business decisions using key performance metrics

# Data Model

The dashboard follows a star schema consisting of one fact table and three dimension tables.

Table	Descriptions
- tblTransactions: Rental transaction records including rental duration, charges, insurance, customer, and vehicle information
- tblCustomers: Customer demographic and location data
- tblCars: Vehicle inventory including make, model, color, and daily rental fee
- Date: Calendar table created using DAX to support time intelligence

# Data Modeling

The data model includes:

- One-to-many relationships between dimensions and the transaction table
- A dedicated Date table generated with CALENDARAUTO()
- Calendar hierarchy including:
  - Year
  - Month
  - Month Number
  - Quarter
  - Weekday

This model enables efficient filtering and time-based analysis across the report.

# DAX Measures & Calculations
## Calculated Columns

**Base Charge**

Calculates the rental cost before optional insurance.

BaseCharge =
tblTransactions[NumOfDays] *
RELATED(tblCars[DailyRentalFee])

**Total Insurance Fee**

Calculates optional insurance charges.

TotalInsuranceFee =
tblTransactions[NumOfDays] *
tblTransactions[OptionalDailyInsurance]

**Total Charge**

Calculates the total transaction value.

TotalCharge =
tblTransactions[BaseCharge] +
tblTransactions[TotalInsuranceFee]

## Measures

**Total Rentals**

Total Rentals =
COUNTROWS(tblTransactions)

**Base Revenue**

BaseRevenue =
SUM(tblTransactions[BaseCharge])

**Insurance Revenue**

InsuranceRevenue =
SUM(tblTransactions[TotalInsuranceFee])

# Dashboard Features
- Interactive slicers for customer gender and time filtering
- Monthly revenue trend analysis
- Revenue by vehicle manufacturer
- Geographic visualization of rentals by state
- KPI metrics for total rentals and revenue
- Cross-filtering across all report visuals

# Key Insights

The dashboard enables users to:

- Identify seasonal revenue trends throughout the year
- Compare the revenue contribution of different vehicle manufacturers
- Analyze rental demand by geographic region
- Understand customer demographics through gender segmentation
- Measure the impact of optional insurance on overall revenue

# Skills Demonstrated
- Power BI
- Data Modeling
- Star Schema Design
- DAX
- Power Query
- Business Intelligence
- KPI Development
- Interactive Dashboard Design
- Time Intelligence
Data Visualization
