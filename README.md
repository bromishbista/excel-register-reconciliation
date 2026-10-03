# Project Register Reconciliation (Excel + Power Query)

## The problem
A council's PMO and Finance teams kept separate project registers that didn't agree.
There were duplicate rows, inconsistent names, missing records and conflicting budgets.

## What I did
**Part 1: Excel formulas.** Cleaned the data (TRIM, PROPER), matched the registers with lookups,
flagged risks (COUNTIFS, nested IF), built pivots and wrote an issue log of 12 findings.

**Part 2: Power Query.** Rebuilt the same reconciliation as a refreshable pipeline:
- Cleaned a messy finance export (junk rows, "$" stored as text, TEST and TOTAL rows, inconsistent IDs)
- Appended 3 monthly spend files and summarised them with Group By
- Merged the registers on Project ID (Left Outer for the crosswalk, Left and Right Anti for missing records)
- Unpivoted quarterly forecasts from wide to long format
- Calculated budget burn (Q1 spend divided by approved budget)
- When new data arrives, one Refresh All updates every table and the dashboard

## Key findings
- 20 of 24 projects match. 2 budget conflicts of $30,000 each remain.
- 4 projects have no finance record, and 2 of them are already marked Complete.
- 2 finance projects ($155,000) have no PMO oversight.
- One project has used 26% of its budget in a single quarter.

## Dashboard
![Dashboard](Dashboard.png)

## Power Query steps
![Power Query steps](Power-query.png)

## Tools
Excel (XLOOKUP, COUNTIFS, SUMIFS, pivot tables, charts), Power Query, data validation, conditional formatting
