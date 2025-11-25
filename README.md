# A/B Test Case Study – Task 1

## Purpose
This project analyzes two variants (A and B) in a difficulty flow A/B test. Each variant receives 20,000 daily installs and is evaluated based on retention, DAU, IAP revenue, ad revenue, and total revenue.

## 🛠 Methodology


--------------------------
*   **Language:** Python 3.x
*   **Libraries:** `pandas`, `numpy`, `scipy` (interpolation), `matplotlib` (visualization), `statsmodels` (hypothesis testing).
*   **Retention Modeling:**
    *   Since only specific data points (D1, D3, D7, D14) were provided, **Linear Interpolation (`interp1d`)** was used to estimate retention rates for every specific day (Day 0 to Day 30).
    *   For the "New User Source" scenario, an exponential decay model ($Retention = a \cdot e^{b(x-1)}$) was implemented.
*   **Revenue Calculation:**
    *   **IAP Revenue:** Revenue = Users * Purchase Rate * ARPU
    *   **Ad Revenue:** Revenue = (Users * Ad Impressions / 1000) * eCPM
*   **Statistical Significance:** Two-proportions Z-tests were conducted (95% Confidence Interval) to ensure differences in Purchase Ratios and Retention rates were not due to chance.
--------------------------

## 🔍 Task 1: Key Findings

### a)  Daily Active Users (DAU) after 15 Days

**Question:** Which variant retains more users?


Total Variant A: 76486 users
Total Variant B: 79014 users
Winner: Variant B by 2529 users

## 👉 Winner (DAU after 15 days): Variant B 

<img width="1190" height="590" alt="download" src="https://github.com/user-attachments/assets/43234343-6603-41a9-86ee-13c1344f0d49" />



## STATISTICAL SIGNIFICANCE TEST (Z-Test)

| Metric           | Variant A | Variant B | P-Value | Result        |
| ---------------- | --------- | --------- | ------- | ------------- |
| Day 1 Retention  | 53.0%     | 48.0%     | 0.0000  | SIGNIFICANT ✅ |
| Day 3 Retention  | 27.0%     | 25.0%     | 0.0000  | SIGNIFICANT ✅ |
| Day 7 Retention  | 17.0%     | 19.0%     | 0.0000  | SIGNIFICANT ✅ |
| Day 14 Retention | 6.0%      | 9.0%      | 0.0000  | SIGNIFICANT ✅ |

STATISTICAL CONCLUSION:
The improvement in mid-to-long term retention (D7, D14) is statistically significant.

---

### b) Total Revenue by Day 15
**Question:** Which variant earns the most total money by Day 15?

*   **Winner:** **Variant A**

Total Revenue Variant A: $148,118.85
Total Revenue Variant B: $145,888.87
DIFFERENCE: $2,229.98 (Variant A is more profitable)

## 👉 Winner Variant A

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/64e6ea38-35a2-46fc-b487-695e5581c290" />


## HYPOTHESIS TEST ANALYSIS (Z-TEST)

| Metric           | Variant A | Variant B | P-Value | Result        |
| ---------------- | --------- | --------- | ------- | ------------- |
| Purchase Ratio   | 3.05%     | 3.15%     | 0.0254  | SIGNIFICANT ✅ |
| Day 1 Retention  | 53.0%     | 48.0%     | 0.0000  | SIGNIFICANT ✅ |
| Day 7 Retention  | 17.0%     | 19.0%     | 0.0000  | SIGNIFICANT ✅ |
| Day 14 Retention | 6.0%      | 9.0%      | 0.0000  | SIGNIFICANT ✅ |


* Variant B has STATISTICALLY SIGNIFICANT better long-term retention (D7/D14).
---

### c) Total Revenue by Day 30
**Question:**  If we look at the total money earned by Day 30 instead, does our choice change?

*   **Winner:** **Variant B**

Total Revenue Variant A (Day 30): $334,411.42
Total Revenue Variant B (Day 30): $352,865.84
DIFFERENCE: $18,454.42 (Variant B is more profitable)

Yes — the winner changes.

## 👉 Winner Variant B

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/186f2b81-c4b3-46ea-8bbc-b7d3bf94f51d" />


## HYPOTHESIS TEST ANALYSIS (Z-TEST)

| Metric           | Variant A | Variant B | P-Value | Result        |
| ---------------- | --------- | --------- | ------- | ------------- |
| Purchase Ratio   | 3.05%     | 3.15%     | 0.0016  | SIGNIFICANT ✅ |
| Day 1 Retention  | 53.0%     | 48.0%     | 0.0000  | SIGNIFICANT ✅ |
| Day 7 Retention  | 17.0%     | 19.0%     | 0.0000  | SIGNIFICANT ✅ |
| Day 14 Retention | 6.0%      | 9.0%      | 0.0000  | SIGNIFICANT ✅ |

## It generates more revenue AND has statistically significant better long-term retention.
---

### d) Scenario: 10-Day Sale (Day 15-24)
**Question:** What if we run a 10-day sale starting on Day 15 (boosting everyone's purchase rate by
1%)? Does this change which variant earns more total money by Day 30?

*   **Winner:** **Variant B**

Total Revenue Variant A (Day 30 with Sale): $372,318.56
Total Revenue Variant B (Day 30 with Sale): $393,308.70
DIFFERENCE: $20,990.13 (Variant B is more profitable)

## 👉 Winner Variant B

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/4dbbd579-3a7c-425c-8b06-b7570f6068b4" />

## HYPOTHESIS TEST ANALYSIS (Z-TEST)

| Metric               | Variant A | Variant B | P-Value | Result            |
| -------------------- | --------- | --------- | ------- | ----------------- |
| Base Purchase Ratio  | 3.05%     | 3.15%     | 0.0016  | SIGNIFICANT ✅     |
| Sale Period Purchase | 4.05%     | 4.15%     | 0.1108  | Not Significant ❌ |
| Day 1 Retention      | 53.0%     | 48.0%     | 0.0000  | SIGNIFICANT ✅     |
| Day 7 Retention      | 17.0%     | 19.0%     | 0.0000  | SIGNIFICANT ✅     |
| Day 14 Retention     | 6.0%      | 9.0%      | 0.0000  | SIGNIFICANT ✅     |


* Variant B shows stronger long-term retention (D7, D14), while A only leads in D1. Purchase differences are mostly insignificant.
---

### e) Scenario: New User Source (Day 20)
**Question:** On Day 20 we add a new user source. From then on, we get 12,000 users from the original
source and 8,000 from this new one. The new users' retention is described by these formulas.
With this mix of old and new users, which variant makes more total money by Day 30?

*   **Winner:** **Variant B**

Total Revenue Variant A (Day 30 with New Source): $323,998.06
Total Revenue Variant B (Day 30 with New Source): $331,928.01
DIFFERENCE: $7,929.95 (Variant B is more profitable)

## 👉 Winner Variant B

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/11a8b469-6d9d-43d0-84a2-48ef45b10fc2" />


## HYPOTHESIS TEST RESULTS

| Metric          | Variant A | Variant B | P-Value | Result             |
| --------------- | --------- | --------- | ------- | ------------------ |
| Purchase Ratio  | 3.05%     | 3.15%     | 0.0016  | SIGNIFICANT DIFF ✅ |
| Day 1 Retention | 53.0%     | 48.0%     | 0.0000  | SIGNIFICANT DIFF ✅ |
| Day 7 Retention | 17.0%     | 19.0%     | 0.0000  | SIGNIFICANT DIFF ✅ |


STATISTICAL VERDICT: The difference is statistically significant based on user behavior. The results are reliable.

---

### f) Strategic Recommendation
**Question**: Which one should you prioritize, and why? If you could only make one of these
improvements:
1. Run the temporary 10-day sale (from d)
2. Add the new, permanent user source (from e/f)**

   
**Decision:**I think priority should be the second option, because the 10-day sale only provides a short-term boost, whereas the new user source increases long-term revenue. **

## 👉 Add the new, permanent user source

| Option                        | Effect                               | Duration            | Winner                |
| ----------------------------- | ------------------------------------ | ------------------- | --------------------- |
| **10-day sale**               | Short-term IAP boost                 | Temporary (10 days) | Helps B slightly      |
| **New permanent user source** | Sustained retention + revenue growth | Long-term           | Large advantage for B |

# Task 2: User Behavior & Game Economy Analysis

## Overview
This module focuses on **Exploratory Data Analysis (EDA)** and **User Segmentation** to uncover hidden trends in player behavior, session patterns, and monetization dynamics. By analyzing millions of event rows, this study identifies key drivers of retention and revenue, providing actionable recommendations for product and marketing teams.

## 📂 Data Processing Pipeline

The analysis pipeline processes raw daily activity logs through the following stages:

1.  **Data Ingestion & Merging:**
    *   Merged 17 separate CSV files (`000...00` to `000...16`) into a single master DataFrame containing **7.2M+ rows**.
    *   Verified data integrity by checking head/tail consistency to ensure no row shifts occurred during merging.
2.  **Cleaning & Preprocessing:**
    *   **Missing Values:** Handled missing `country` data (MCAR) by dropping rows (<0.2% data loss).
    *   **Type Conversion:** Converted `event_date` and `install_date` to datetime objects.

## 🔍 Distribution Overview

### 1. Total Sessions by Platform

<img width="997" height="468" alt="download" src="https://github.com/user-attachments/assets/1894fd76-c3b7-4356-90cf-55863b7dc77e" />

* The Median Behavior of iOS and Android users is surprisingly similar. In other words, an average iPhone user and a Samsung user engage with the game at roughly the same frequency.

### 2. Total Sessions by Platform

<img width="997" height="468" alt="download" src="https://github.com/user-attachments/assets/88a9bf2f-abb7-4b9d-983a-2f9cc835f377" />

* There is a significant outlier in the Ukraine data. While the maximum session counts in other countries remain around 15–18, some users in Ukraine reach 35+ sessions.

### 3. Daily Active Users Lifecycle Distribution

<img width="1410" height="671" alt="download" src="https://github.com/user-attachments/assets/c359a9cc-66c0-487d-8646-c2363924afd4" />

* More than 50% of the chart is dominated by the "Long-term Player (30+ Days)" segment. This indicates that the game not only attracts curious users but also successfully retains a loyal player base, demonstrating high stickiness.


## 🔍 Key Analyses & Insights

### 1. Average User Revenue by Day 1 Behavior
Segmented users based on first-day playtime:
*   **Tourist (<5 min)** Very short playtime, low engagement and revenue.
*   **Potential (5-20 min)** Moderate playtime, some engagement and revenue potential.
*   **Fanatic (>20 min)** Long playtime, highly engaged, generates the highest revenue.

<img width="855" height="545" alt="download" src="https://github.com/user-attachments/assets/8ca57eb9-4841-4e3b-92c1-4ba94e061cbf" />

* When we examine the relationship between the time spent on the first day and the revenue generated, we observe a nonlinear, exponential increase. Users who spend less than 20 minutes in the game on their first day ("Tourist" and "Potential") generate limited revenue, whereas users who spend more than 20 minutes—the "Fanatic" group—have an average revenue approximately five times higher than the next lower segment.

* The game's first-day experience (FTUE) should be redesigned to keep users engaged for at least 20 minutes. For example, providing a "timed, powerful reward" at the 15th minute could push users past this critical 20-minute threshold, potentially increasing revenue potential fivefold.

### 2. RFM Segmentation (Recency, Frequency, Monetary)

**RFM Analysis:**
* What does it measure? It evaluates a user's overall health as of today.

Used RFM analysis to categorize users based on Recency (R) and Frequency (F):
*   **Champions:** High spend, frequent play, recent activity.
*   **Loyal Users:** Frequent and recent players, slightly lower than Champions.
*   **wcomers:** Recently joined but low activity.
*   **Lost Loyals:** Previously frequent but inactive now.
*   **Sleeping (Lost):** Low activity and low recency.
*   **At Risk / Average:** Moderate engagement, potential to churn.

<img width="1097" height="545" alt="download" src="https://github.com/user-attachments/assets/b7f6f2ee-e836-4c42-9e05-e77bb772c299" />

* This table shows that the game performs well on the Acquisition side but struggles with Retention. While new users are successfully brought in, many fail to become loyal players and instead fall into the "At Risk" or "Sleeping" segments.
* **Recommended Action:**
* Instead of focusing primarily on acquiring new users, our priority should be to convert the large "At Risk" user base into loyal players.

### 3. COUNTRY-BASED REVENUE BEHAVIOR (IAP vs ADS)
*   **Finding:**
    *   **Tier 1 (US, DE):** Revenue is dominated by **IAP (In-App Purchases)**.
    *   **Tier 2/3 (RU, IN):** IAP is low, but **Ad Revenue** makes up 30-50% of the total value.

<img width="1010" height="608" alt="download" src="https://github.com/user-attachments/assets/5e94f213-51d5-4c46-ae74-276da7f45e0c" />

* The USA and Germany account for the majority of total revenue, and almost all of this revenue comes from IAP (In-App Purchases).

* Let's pay attention to Russia and India at the bottom of the list. While the yellow bar (IAP) is very low, the blue bar (Ads) accounts for a significant portion of total revenue (30%-50%). We can say that players in these countries spend less compared to players in other countries.

### 4. Weekday vs Weekend: Player Activity and Spending

<img width="1070" height="526" alt="download" src="https://github.com/user-attachments/assets/7eb42403-7dd4-4578-955d-03667a943e19" />

* Activity (gray bars) and revenue (green line) show a sharp increase starting Thursday. Players are entering weekend mode early. Both the number of players and their spending peak on Friday (≈ $0.142 revenue).
* Major sales events should definitely start on Thursday evening to capture the upward trend.
* Special Sunday-only discounts or “One-Day-Only Costume” promotions can be used to lift the green line (revenue) that drops on Sunday.

### 5. Balance Scale: Does Spending Affect Win Rate?

*   **Categorized players by spending levels:**
* Free Player (0$): No spending.
* Minnow (0-5$): Low spender.
* Dolphin (5-20$): Moderate spender.
* Whale (>20$): High spender.

<img width="846" height="545" alt="download" src="https://github.com/user-attachments/assets/d0fad7c6-e3c3-44d2-a23b-8aaa2f830ba5" />

* The most critical finding in the chart is that the average win rate of players who spend nothing (Free Players) remains around 40%, while even a minimal spender (Minnow) sees their win rate suddenly jump to about 62%.

## Recommendations
* Data on game sessions played with friends should be collected and analyzed. In particular, the frequency with which players join games with their friends and their co-play behavior can be examined.
* Develop a Rapid Intervention Strategy for the "Tourist" Segment Lost in the First Days Tourist users quit the game within <5 minutes.
* Balance Intervention Needed for Spending Players (Minnows) The sudden increase in win rates for paying players, while Free-to-Play users remain stuck at a 40% win rate, indicates a risk of early churn.
* In countries like Russia and India, where IAP is low but ad revenue is high, increasing ad impressions could boost monetization.
