# Marketing A/B Testing Report

## Table of Contents
1. [Title Page](#title-page)
2. [Executive Summary](#executive-summary)
3. [Introduction](#introduction)
4. [Methodology](#methodology)
5. [Findings](#findings)
6. [Conclusion](#conclusion)
7. [Recommendations](#recommendations)

### Title Page
**Title:** Marketing A/B Testing Analysis Report: Campaign A (PSA) vs. Campaign B (Ad)  
**Author:** Amr Salah Abd Elghany

### Executive Summary
This report analyzes the performance of two marketing campaigns (A: Public Service Announcement "PSA" and B: Ad Campaign) to determine which strategy drives higher user conversion rates. Key findings:
- Campaign B (Ad) achieved a 2.55% conversion rate, slightly higher than Campaign A (1.79%).
- Statistical analysis shows no significant difference (p = 0.243), with a 95% confidence interval of [0.5%, 2.1%] (crossing 0).

**Recommendation:** Do not adopt Campaign B as the difference is not statistically significant. Investigate alternative strategies or refine the experimental campaign.

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

