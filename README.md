Explanation Video:https://drive.google.com/file/d/1Q1zXNSkJwMSIPodsCQdITUsrQ218Abfp/view?usp=drive_link


EDVIRON – Revenue, Commission & Settlement Analytics

Power BI Assignment – Explanation Note

1. Project Objective

The objective of this project is to analyze transactional payment data processed through the Edviron platform and build an interactive analytics dashboard.
The solution performs data cleaning, pricing normalization, revenue computation, settlement tracking, and exposure monitoring using Power BI.

The dashboard enables business stakeholders to understand:

Platform revenue generation

ERP partner performance

Payment gateway behavior

Settlement risks and pending exposure

2. Data Preparation & Cleaning

The raw dataset contained multiple ERP partner sheets. The following steps were performed:

Data Consolidation

Combined all ERP sheets (AKIRA, CampusPro, Edchemy, Sigma) into a single dataset using Power Query.

Added a new column “Partner” to identify the source ERP of each transaction.

Data Cleaning

Removed empty rows and irrelevant columns.

Standardized text fields (trimmed spaces, cleaned characters).

Standardized Status values into:

SUCCESS

FAILED

PENDING

Replaced missing categorical values with labeled placeholders:

Unknown Payment Mode

Unknown Institute (where necessary)

Corrected data types:

Transaction Amount → Decimal

Pricing columns → Text (for % detection)

Pricing Normalization

The dataset contained pricing in two formats:

Flat value (₹5)

Percentage (2%)

All pricing values were converted into absolute INR values per transaction.

3. Revenue Calculation Logic

The following pricing layers exist:

Merchant Pricing – Amount ERP charges school

Partner Pricing – Amount Edviron charges ERP

Edviron Buying – Edviron’s cost to payment gateway

After conversion to INR:

ERP Revenue

ERP Revenue = Merchant Pricing − Partner Pricing

This represents the ERP partner’s earning.

Edviron Net Revenue

Edviron Net Revenue = Partner Pricing − Edviron Buying

This represents Edviron’s actual profit after paying gateway costs.

Edviron Gross Revenue

Edviron Gross Revenue = ERP Revenue + Edviron Net Revenue

This represents total commission collected on the platform.

4. Settlement & Exposure Logic
School Settlement Amount

Amount transferred to school after platform commissions:

School Settlement = Transaction Amount − Edviron Gross Revenue

ERP Payable

Amount that Edviron must settle to the ERP partner:

ERP Payable = ERP Revenue

Edviron Retained

Company’s retained earnings:

Edviron Retained = Edviron Net Revenue

Pending Exposure

Financial risk occurs when payment is not captured.

Pending Exposure = Transaction Amount
(when Capture Status = PENDING)

This helps identify unsettled transactions and receivable risk.

5. Dashboard Design & Reports

Four analytical report pages and one executive dashboard were created.

1. Time Summary

Daily/Monthly GMV trend

Revenue distribution over time

2. Partner Performance

Transaction count by ERP partner

Revenue contribution by partner

Success rate comparison

3. Gateway & Payment Method Analysis

Gateway-wise transaction volume

Payment method usage (UPI/Card/Netbanking)

Success vs Failure rates

4. Exposure Report

Pending exposure by partner

Gateway settlement risk

Outstanding settlement amounts

5. Executive Dashboard

Includes key KPIs:

Total Transactions

GMV

ERP Revenue

Edviron Net Revenue

Edviron Gross Revenue

Pending Exposure

Unique Users

Interactive slicers:

Date Range

Gateway

Payment Method

6. Assumptions

Percentage pricing is applied on Transaction Amount.

Pending exposure is calculated when Capture Status is PENDING.

Missing categorical values were labeled rather than removed to preserve transaction counts.

Revenue calculations are performed per transaction and then aggregated.

7. Business Insights Enabled

This dashboard allows Edviron to:

Identify high-performing ERP partners

Monitor payment gateway reliability

Detect payment failure patterns

Track settlement delays and financial risk

Understand user payment preferences

Conclusion

The project successfully transformed raw transactional data into a structured financial analytics system.
The solution enables business stakeholders to monitor revenue, operational performance, and settlement exposure through an interactive Power BI dashboard.
