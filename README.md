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


## Variant B has STATISTICALLY SIGNIFICANT better long-term retention (D7/D14).
---

### c) Total Revenue by Day 30
**Question:**  Does the winner change if we extend the window to Day 30?

*   **Winner:** **Variant B**

Total Revenue Variant A (Day 30): $334,411.42
Total Revenue Variant B (Day 30): $352,865.84
DIFFERENCE: $18,454.42 (Variant B is more profitable)

Yes — the winner changes when the window is extended.

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
**Question:** What if we run a 10-day sale from Day 15 (+1% absolute purchase rate)?

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


Variant B shows stronger long-term retention (D7, D14), while A only leads in D1. Purchase differences are mostly insignificant.
---

### e) Scenario: New User Source (Day 20)
**Question:** Introducing a new user source (8k/day) with exponential retention curves.

*   **Winner:** **Variant B**

Total Revenue Variant A (Day 30 with New Source): $323,998.06
Total Revenue Variant B (Day 30 with New Source): $331,928.01
DIFFERENCE: $7,929.95 (Variant B is more profitable)

## Variant B maintains a stronger tail and captures more monetization from both old + new user streams.
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
**Question: Which one should you prioritize, and why? If you could only make one of these
improvements:
1. Run the temporary 10-day sale (from d)
2. Add the new, permanent user source (from e/f)**

   
**Decision:**I think priority should be the second option, because the 10-day sale only provides a short-term boost, whereas the new user source increases long-term revenue. **

## 👉 Add the new, permanent user source

| Option                        | Effect                               | Duration            | Winner                |
| ----------------------------- | ------------------------------------ | ------------------- | --------------------- |
| **10-day sale**               | Short-term IAP boost                 | Temporary (10 days) | Helps B slightly      |
| **New permanent user source** | Sustained retention + revenue growth | Long-term           | Large advantage for B |









