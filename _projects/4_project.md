---
layout: page
title: EDGAR 
description: Analysis of EDGAR log data from 2020 to 2024
img: assets/img/edgar.webp
importance: 4
category: work
---
# Analyzing EDGAR Log Data (2020-2024): Key Insights and Trends

## I. Introduction
EDGAR (Electronic Data Gathering, Analysis, and Retrieval) is an online database maintained by the U.S. Securities and Exchange Commission (SEC). It collects and provides public access to filings from companies required to submit documents to the SEC. These filings include financial statements, disclosures, and other regulatory reports such as Form 10-K (annual reports), Form 10-Q (quarterly reports), Form 8-K (event-driven reports), and Form 4 (insider trading reports). EDGAR plays a crucial role in enhancing transparency, offering investors, analysts, and researchers critical information to assess corporate performance and regulatory compliance.

EDGAR Log Files record internet search traffic for EDGAR filings, capturing detailed user interactions with the EDGAR system. These log files include metadata such as search activities, file access, and document downloads. They typically contain timestamps, file types accessed, and document names.

The availability of EDGAR log data was discontinued after 2017 but resumed in May 2020. From what we know, no one has processed the new dataset yet. It differs from the earlier version—most notably, it no longer provides IP addresses. More detailed information about this dataset can be found on the [SEC's official website](https://www.sec.gov).

In this blog, we aim to provide a short descriptive analysis of the new EDGAR dataset (June 1, 2020, to June 31, 2024) and discuss its potential applications in related research.

---

## II. Prior Literature
The EDGAR log dataset has been widely used to study investor attention, access patterns, and the economic consequences of information disclosure. For example, Drake et al. (2015) examined the downloading patterns of EDGAR filings and their relationship with firms' earnings announcements from 2008 to 2011.

Earlier versions of the EDGAR dataset (pre-2017) contained IP addresses, enabling researchers to distinguish between human users and automated bots, with many studies excluding bot searches (Loughran and McDonald, 2017; Ryans, 2017; Drake et al., 2015). However, Drake et al. (2020) included bots to examine institutional investor behavior, as automated data retrieval often reflects institutional activity.

The new dataset from 2020 no longer provides IP addresses. While this shift limits certain analyses, the data remains highly valuable for tracking interactions with specific filings.

---

## III. Data Processing
We downloaded and processed the EDGAR log data to obtain download dates and accession IDs. We counted the number of downloads per day per accession ID per CIK (Central Index Key). Using the SEC’s index, we supplemented this with information such as form type, filing date, and company name.

Due to the dataset’s size—each daily log file contains millions of download records—we used the **UChicago Midway3 cloud computing platform** to process the files. Our code for processing and analysis is available [here](https://github.com).

---

## IV. Key Findings

### 1. Median Requests by Weekday & Holidays
- We observed a dramatic increase in search volume from 2020 to 2024, indicating growing reliance on EDGAR filings.
- Activity drops on weekends and holidays, reflecting reduced investor engagement during non-trading days.

### 2. Total Downloads by Month (2020-2024)
- **May 2024** recorded the highest download volume, surpassing 2 billion requests.
- **Seasonality**: Downloads peak between April and June, coinciding with Q1 and Q2 reporting seasons.
- **Trend**: Download volumes have steadily increased, showing rising investor interest in financial disclosures.

### 3. Total Requests by Form Category
Following Drake et al. (2015), we grouped the forms into 9 categories: Form 10-K, Form 10-Q, Form 8-K, Form 424, Form S, Form SC, Form 4, Form DEF, and Other.  
- **Form 4 (Insider Trading Reports)**: This form consistently receives the most requests, reflecting strong interest in tracking insider trading.  
- **10-K and 10-Q**: These key financial reports show steady growth in demand.  
- **Form 8-K**: Requests spiked in 2023, suggesting heightened attention to event-driven disclosures like earnings announcements and mergers.  
- **DEF and SC Filings**: Though less common, these filings show moderate growth, indicating increased relevance for niche investor segments.

### 4. Top 10 Companies by EDGAR Downloads

| **Rank** | **2020**                | **2021**                | **2022**                | **2023**                | **2024**                |
|----------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|
| 1        | Microsoft Corporation   | Microsoft Corporation   | Microsoft Corporation   | Oracle Corporation      | Oracle Corporation      |
| 2        | Amazon.com, Inc.        | IBM                     | Oracle Corporation      | IBM                     | IBM                     |
| 3        | Apple Inc.              | Zoom Video Communications | IBM                    | Microsoft Corporation   | Microsoft Corporation   |
| 4        | Meta Platforms, Inc.    | Tesla, Inc.             | American Airlines       | Coca-Cola Company       | Tesla, Inc.             |
| 5        | Airbnb, Inc.            | NVIDIA Corporation      | Apple Inc.              | Alphabet Inc.           | Coca-Cola Company       |
| 6        | IBM                     | Procter & Gamble        | Tesla, Inc.             | Qualcomm Inc.           | Intel Corporation       |
| 7        | Intel Corporation       | Apple Inc.              | NVIDIA Corporation      | Tesla, Inc.             | PepsiCo, Inc.           |
| 8        | Netflix, Inc.           | Alphabet Inc.           | Alphabet Inc.           | Apple Inc.              | Netflix, Inc.           |
| 9        | NVIDIA Corporation      | Qualcomm Inc.           | Coca-Cola Company       | Procter & Gamble        | NVIDIA Corporation      |
| 10       | Tesla, Inc.             | CrowdStrike             | Qualcomm Inc.           | NVIDIA Corporation      | Qualcomm Inc.           |

#### Analysis
- **Tech Dominance**: Microsoft dominated from 2020 to 2022, but Oracle took the top spot in 2023 and 2024.
- **IBM’s Consistency**: IBM maintained a top-3 position across all five years, reflecting sustained interest in its filings.
- **Surging Interest**: Companies like Oracle, Coca-Cola, and Tesla saw increased engagement in 2023-2024, suggesting shifts in market focus.

---

## V. Discussion & Further Research
The analysis of EDGAR log data from 2020 to 2024 highlights evolving investor attention trends, with technology companies at the forefront. The sharp rise in requests during 2023 suggests that external factors, such as geopolitical events and market volatility, influence these trends.

Several events since 2020, including **COVID-19**, **Russia’s invasion of Ukraine**, **the Israel-Gaza conflict**, and the **rise of AI technologies** like ChatGPT, have shaped market behavior. For example, our content analysis shows that requests for filings related to Russia increased ahead of the invasion.

### Potential Research Extensions
- **Market Reactions**: Analyze how certain filings (e.g., 8-K, Form 4) affect stock prices following high download volumes.
- **Impact of Global Events**: Correlate download patterns with major events like COVID-19 or advancements in AI.
- **Sentiment Analysis**: Use NLP to assess how investor sentiment shifts with new disclosures, particularly for tech companies.
- **Historical vs. Current Filings**: Investigate why investors search for historical filings and how they use past disclosures to inform current decisions.

By continuing to analyze this dataset, researchers can gain valuable insights into how corporate disclosures influence market behavior and investor decision-making.

---

## VI. References  
- **Drake, M. S., Roulstone, D. T., & Thornock, J. R.** (2015). *The determinants and consequences of information acquisition via EDGAR.* Contemporary Accounting Research, 32(3), 1128-1161. [https://doi.org/10.1111/1911-3846.12094](https://doi.org/10.1111/1911-3846.12094)  

- **Drake, M. S., Roulstone, D. T., & Thornock, J. R.** (2020). *EDGAR search and download activity: Institutional investors' behavior and its impact on stock prices.* Journal of Financial Economics, 135(2), 537-558. [https://doi.org/10.1016/j.jfineco.2019.07.009](https://doi.org/10.1016/j.jfineco.2019.07.009)  

- **Loughran, T., & McDonald, B.** (2017). *The use of word lists in textual analysis.* Journal of Behavioral Finance, 18(3), 233-246. [https://doi.org/10.1080/15427560.2017.1340970](https://doi.org/10.1080/15427560.2017.1340970)  

- **Ryans, J. K.** (2017). *EDGAR and the effect of automated data retrieval on financial markets.* Journal of Accounting Research, 55(2), 471-502. [https://doi.org/10.1111/1475-679X.12132](https://doi.org/10.1111/1475-679X.12132)  

---

**Notes**: We do not have access to the log files for 2020-09-26 and 2024-04-24, as these files are missing from the SEC EDGAR website. However, we believe that the absence of these two files will not significantly bias our analysis


