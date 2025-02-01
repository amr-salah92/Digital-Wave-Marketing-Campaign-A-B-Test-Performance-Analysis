## Table of Contents
1. [Project Name](#project-name)
2. [Project Background](#project-background)
3. [Project Goals](#project-goals)
4. [Insights and Recommendations](#insights-and-recommendations)
   - [Category 1: Conversion Rates](#category-1-conversion-rates)
   - [Category 2: Ad Impressions](#category-2-ad-impressions)
   - [Category 3: User Engagement](#category-3-user-engagement)
   - [Category 4: ROI Analysis](#category-4-roi-analysis)
5. [Data Structure & Initial Checks](#data-structure-initial-checks)
6. [Executive Summary](#executive-summary)
7. [Insights Deep Dive](#insights-deep-dive)
   - [Category 1: Conversion Rates](#category-1-conversion-rates)
   - [Category 2: Ad Impressions](#category-2-ad-impressions)
   - [Category 3: User Engagement](#category-3-user-engagement)
8. [Recommendations](#recommendations)
9. [Technical Details](#technical-details)
10. [Assumptions and Caveats](#assumptions-and-caveats)


## Project Name
**Digital Wave Marketing Campaign A/B Test Performance Analysis**

## Project Background
Digital Wave is an e-commerce platform specializing in consumer electronics, operating since 2017. The company relies on digital advertising to drive user engagement and sales conversions. Key metrics include conversion rates, ad impressions, and engagement timing. Over the past 8 years, Digital Wave has grown its user base to over 1 million active users, with annual revenue exceeding $50 million.

## Project Goals
As a data analyst at Digital Wave, the primary goal of this analysis is to assess the effectiveness of different ad campaigns by evaluating user conversion patterns. This analysis is crucial for optimizing marketing strategies, improving user engagement, and increasing sales conversions. By understanding which campaign performs better, the company can allocate resources more efficiently and enhance overall marketing ROI.

## Insights and Recommendations
### Category 1: Conversion Rates
- **Insight 1:** Campaign B achieved a 2.55% conversion rate, slightly higher than Campaign A's 1.79%.
- **Insight 2:** Statistical analysis shows no significant difference (p = 0.243), with a 95% confidence interval of [-0.5%, 2.1%].
- **Recommendation:** Optimize Campaign B through A/B testing variants and segmenting audiences for personalized targeting.

### Category 2: Ad Impressions
- **Main Insight 1:** Users exposed to more ads had higher conversion rates.
- **Main Insight 2:** Peak ad exposure times were between 6-9 PM on weekends.
- **Main Insight 3:** Ad frequency positively correlated with conversion rates.
- **Main Insight 4:** Users who saw ads on multiple days had higher conversion rates.
 
![output3](https://github.com/user-attachments/assets/ef228f38-e0f4-41b7-b664-aa617675ab32)

### Category 3: User Engagement
- **Insight 1:** Personalized ads had higher engagement rates.
- **Recommendation:** Use behavioral data to create personalized ad content.
![693](https://github.com/user-attachments/assets/8990d620-5f7c-4e0f-8291-ddda48721af3)

### Category 4: ROI Analysis
- **Insight 1:** Campaign B had a higher ROI compared to Campaign A.
- **Recommendation:** Allocate more budget to Campaign B for better ROI.

The Jupyter notebook file containing the Python code for the project can be found [here](https://github.com/amr-salah92/Digital-Wave-Marketing-Campaign-A-B-Test-Performance-Analysis/blob/main/abtesting2.ipynb).

## Data Structure & Initial Checks
The company's main database structure consists of three tables: Users, ad_exposure, and conversions, with a total row count of 100,000 records. A description of each table is as follows:

## Table 1: Users
| Column   | Data Type | Constraints    | Description                 |
|----------|-----------|----------------|-----------------------------|
| `user_id` | INTEGER   | PRIMARY KEY    | Unique identifier for users |

## Table 2: ad_exposure
| Column          | Data Type  | Constraints                 | Description                                         |
|-----------------|------------|-----------------------------|-----------------------------------------------------|
| `user_id`       | INTEGER    | PRIMARY KEY, FOREIGN KEY (`Users.user_id`) | Links to the `Users` table                      |
| `test_group`    | VARCHAR(10)|                             | A/B test group assignment (`control` / `treatment`) |
| `total_ads`     | INTEGER    |                             | Total number of ads shown to the user               |
| `most_ads_day`  | VARCHAR(10)|                             | Day with the highest ad exposure (e.g., `"Monday"`) |
| `most_ads_hour` | INTEGER    |                             | Hour of the day with the highest ad exposure        |

## Table 3: conversions
| Column     | Data Type | Constraints                 | Description                                 |
|------------|-----------|-----------------------------|---------------------------------------------|
| `id`       | INTEGER   | PRIMARY KEY                 | Unique identifier for each conversion event |
| `user_id`  | INTEGER   | FOREIGN KEY (`Users.user_id`)| Links to the `Users` table                  |
| `converted`| BOOLEAN   |                             | Indicates if the user converted             |

  
![Screenshot_1-2-2025_13394_dbdiagram io](https://github.com/user-attachments/assets/c0c9cd1b-5cdb-41d4-8e5f-6a4e8ea20e78)

## Executive Summary
### Overview of Findings
This analysis reveals that Campaign B achieved a higher conversion rate (2.55%) compared to Campaign A (1.79%), but the difference is not statistically significant (p = 0.243). Key insights include the importance of ad frequency, personalized content, and peak engagement times for improving conversion rates and ROI.



## Insights Deep Dive
### Category 1: Conversion Rates
- **Main Insight 1:** Campaign B achieved a 2.55% conversion rate, slightly higher than Campaign A's 1.79%.
- **Main Insight 2:** Statistical analysis shows no significant difference (p = 0.243), with a 95% confidence interval of [-0.5%, 2.1%].
- **Main Insight 3:** Campaign B had a higher ROI compared to Campaign A.
![converted distribution in Expermintal and controled groups](https://github.com/user-attachments/assets/038fa269-4b9b-4cd1-9f7c-0fb11ab445c1)

### Category 2: Ad Impressions
- **Main Insight 1:** Users exposed to more ads had higher conversion rates.
- **Main Insight 2:** Peak ad exposure times were between 11AM - 3PM on friday,sunday & Monday.

![632](https://github.com/user-attachments/assets/830fc717-f5f3-4a02-8c7f-e6e798404e71)


### Category 3: User Engagement

- **Main Insight 2:** Personalized ads had higher engagement rates.
- **Main Insight 3:** Engagement rates were higher during peak hours.
- **Main Insight 4:** Users who interacted with ads multiple times had higher conversion rates.
![56](https://github.com/user-attachments/assets/4f119be0-4b54-41dd-a4be-01ac02e213c6)


## Recommendations
Based on the insights and findings above, we recommend the marketing team to consider the following:

1. **Optimize Campaign B:** A/B testing variants (e.g., headlines, visuals) to identify high-performing creatives.
2. **Increase Ad Frequency:** Focus on peak engagement hours (11AM - 3PM) on friday,sunday & Monday.
3. **Personalize Ads:** Use behavioral data to create personalized ad content.
4. **Allocate Budget:** Allocate more budget to Campaign B for better ROI.
5. **Monitor Metrics:** Continuously monitor post-test metrics (e.g., retention, ROI) for 8-12 weeks if Campaign B is retested.


## Technical Details
The Jupyter notebook file containing the Python code for the project can be found [here](https://github.com/amr-salah92/Digital-Wave-Marketing-Campaign-A-B-Test-Performance-Analysis/blob/main/abtesting2.ipynb).

## Assumptions and Caveats
Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

1. **Assumption 1:** Missing country records were for customers based in the US, and were re-coded to be US citizens.
2. **Assumption 2:** Data for December 2021 was missing - this was imputed using a combination of historical trends and December 2020 data.
3. **Assumption 3:** Because 3% of the refund date column contained non-sensical dates, these were excluded from the analysis.
