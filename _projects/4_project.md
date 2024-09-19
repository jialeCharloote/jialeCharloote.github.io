---
layout: page
title: EDGAR 
description: Analysis of EDGAR log data from 2020 to 2024
img: assets/img/edgar.webp
importance: 4
category: work
---

## What is EDGAR Log Data?

**SEC.gov | EDGAR Log File Data Sets**  
Loughran and McDonald - EDGAR Server Log // Miscellaneous Data // Software Repository for Accounting and Finance // University of Notre Dame  
James Ryans - [Request Access to EDGAR Log File Data (google.com)](https://google.com)

## Prior Literature

- **Gone after 2017**: The older dataset was discontinued after 2017.
- **New data from 2020**: Data became available again starting from 2020, but nobody has processed it yet.
- **Data differences**: The current dataset no longer provides IP addresses, which were available in previous versions.

## Data Processing

We downloaded and processed the EDGAR log data to obtain:
- **Download dates** 
- **Accession IDs**

We counted the number of downloads per day, per accession ID, and per CIK. Using the SEC’s index, we retrieved additional information such as form type, filing date, company name, etc.

## Key Findings

- **Dramatic increase in search volume** from 2021 to 2022.
- As expected, **search volumes decrease on weekends**.
