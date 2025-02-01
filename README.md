# Marketing A/B Testing Report

## Table of Contents
1. [Title Page](#title-page)
2. [Executive Summary](#executive-summary)
3. [Data Structure and Overview](#data-structure-and-overview)
4. [Introduction](#introduction)
5. [Methodology](#methodology)
6. [Findings](#findings)
7. [Conclusion](#conclusion)
8. [Recommendations](#recommendations)

### Title Page
**Title:** Marketing A/B Testing Analysis Report: Campaign A (PSA) vs. Campaign B (Ad)  
**Author:** Amr Salah Abd Elghany

### Executive Summary
This report analyzes the performance of two marketing campaigns (A: Public Service Announcement "PSA" and B: Ad Campaign) to determine which strategy drives higher user conversion rates. Key findings:
- Campaign B (Ad) achieved a 2.55% conversion rate, slightly higher than Campaign A (1.79%).
- Statistical analysis shows no significant difference (p = 0.243), with a 95% confidence interval of [0.5%, 2.1%] (crossing 0).

## Data Structure and Overview

**Database Schema & Initial Checks**  

This repository documents the database schema and initial validation checks for analyzing user ad exposure and conversion events.  

**Database Structure**  

The database consists of three primary tables: `Users`, `ad_exposure`, and `conversions`. Below is a breakdown of each table, including its schema and purpose.  

**1. Users**  
Stores unique user information.  

| Column   | Data Type | Constraints    | Description                 |  
|----------|----------|---------------|-----------------------------|  
| `user_id` | INTEGER  | PRIMARY KEY    | Unique identifier for users |  

**2. ad_exposure**  
Tracks user interaction with advertisements.  

| Column          | Data Type  | Constraints                 | Description                                         |  
|---------------|----------|---------------------------|---------------------------------------------------|  
| `user_id`      | INTEGER  | PRIMARY KEY, FOREIGN KEY (`Users.user_id`) | Links to the `Users` table                      |  
| `test_group`   | VARCHAR(10) |  | A/B test group assignment (`control` / `treatment`) |  
| `total_ads`    | INTEGER  |  | Total number of ads shown to the user            |  
| `most_ads_day` | VARCHAR(10) |  | Day with the highest ad exposure (e.g., `"Monday"`) |  
| `most_ads_hour` | INTEGER  |  | Hour of the day with the highest ad exposure     |  

**3. conversions**  
Stores user conversion events.  

| Column     | Data Type | Constraints                 | Description                                 |  
|-----------|----------|---------------------------|---------------------------------------------|  
| `id`       | INTEGER  | PRIMARY KEY               | Unique identifier for each conversion event |  
| `user_id`  | INTEGER  | FOREIGN KEY (`Users.user_id`) | Links to the `Users` table                |  
| `converted` | BOOLEAN  |  | Indicates if the user converted            |  

**Referential Integrity**  

- `ad_exposure.user_id` → `Users.user_id`: Ensures that ad exposure data only exists for valid users.  
- `conversions.user_id` → `Users.user_id`: Ensures that conversion records are linked to registered users.  

**Initial Data Validation Checks**  

Before running analyses, perform the following validation steps:  

1. **Check for Missing Values**: Ensure all required fields are populated.  
2. **Detect Duplicates**: Confirm that `user_id` in `Users` and `ad_exposure` is unique.  
3. **Verify Data Consistency**:  
   - Ensure `test_group` only contains valid values (`control`, `treatment`).  
   - Confirm `converted` values are either `TRUE` or `FALSE`.  
   - Validate `most_ads_day` contains valid day names (`Monday–Sunday`).  
   - Ensure `most_ads_hour` is within the range `0–23`.  

![Screenshot_1-2-2025_13394_dbdiagram io](https://github.com/user-attachments/assets/0d1b40dc-cb3c-4791-8f07-65af4fd9a5c0)


### Introduction
**Purpose:**
- Compare conversion rates between Campaign A (control) and Campaign B (experimental).
- Provide data-driven recommendations for campaign optimization.

**Background:**
The A/B test ran for four weeks, with users randomly assigned to either Campaign A (PSA) or Campaign B (Ad). Conversion data and ad exposure metrics were collected to evaluate effectiveness.

### Methodology
**Data Sources:**
- **Dataset:** Marketing A/B Testing (Kaggle)
- **Description:** Contains user IDs, campaign assignment, conversion status (True/False), and ad exposure metrics.
- **Source:** Randomized controlled trial data from company records.
- **Validity:** Cleaned (duplicates removed, missing values addressed).

**Analysis Methods:**
- **Statistical Tests:** Two proportion z-test for conversion rate comparison.
- **Tools:** Python (Pandas, SciPy, Matplotlib, Seaborn).

**Limitations:**
- Small observed effect size.
- Short test duration (4 weeks).

### Findings
**Conversion Rates:**
| Campaign | Conversion Rate |
|----------|-----------------|
| A (PSA)  | 1.79%           |
| B (Ad)   | 2.55%           |
| Pooled Rate | 39.62%       |

![converted distribution in Expermintal and controled groups](https://github.com/user-attachments/assets/25f7eaba-c34d-47dc-a299-56e45261e0a9)

**Statistical Significance:**
- **Test Statistic (Z-score):** -1.17
- **Critical Z-value:** ±1.96
- **p-value:** 0.243
- **Interpretation:** No significant difference (p > 0.05).

**Confidence Interval:**
- **Confidence Interval:** [-0.5%, 2.1%]
- **Interpretation:** The true difference could range from a 0.5% decrease to a 2.1% increase in conversions for Campaign B.

![gaussian distribution with rejection region](https://github.com/user-attachments/assets/315011e4-7401-4061-858d-ad31f5e41191)

**Key Performance Indicators (KPIs):**
- **Conversion Rate Uplift:** B vs. A: +0.76% (not statistically significant).
- **Statistical Error:** 0.66% (margin of error).

### Conclusion
Campaign B (Ad) shows a 0.76% higher conversion rate than Campaign A (PSA), but the difference is not statistically significant. The confidence interval crossing 0 indicates uncertainty about Campaign B’s true impact.

### Recommendations
1. Reject Campaign B as the primary strategy due to statistically unreliable results (p = 0.243). Maintaining Campaign A avoids unnecessary costs from unproven changes.
2. Retest with a larger sample (minimum 10,000 users/group) to reduce statistical error (current: ±0.66%) and narrow the confidence interval. Use power analysis to determine ideal sample size for detecting ≥1% effect.
3. Optimize Campaign B by:
   - A/B testing variants (e.g., headlines, visuals) to identify high-performing creatives.
   - Segmenting audiences using behavioral data (e.g., ad engagement time) for personalized targeting.
   - Testing time-sensitive offers during peak engagement hours (12-2 
PM/Friday and Sunday).
4. Monitor post-test metrics (e.g., retention, ROI) for 8–12 weeks if Campaign B is retested.

