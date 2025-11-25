# A/B Test Case Study – Task 1

## Purpose
This project analyzes two variants (A and B) in a difficulty flow A/B test. Each variant receives 20,000 daily installs and is evaluated based on retention, DAU, IAP revenue, ad revenue, and total revenue.

## Methodology

1. Retention Modeling:

Given retention points: D1, D3, D7, D14

Linear interpolation used to estimate day-by-day retention curve

DAU calculated as: DAU(day) = 20,000 * (Retention(day) / 100)

2. Revenue Modeling:

IAP Revenue
Revenue = Users * Purchase Rate * ARPU

Ad Revenue
Revenue = (Users * Ad Impressions / 1000) * eCPM

--------------------------
*   **Language:** Python 3.x
*   **Libraries:** `pandas`, `numpy`, `scipy` (interpolation), `matplotlib` (visualization), `statsmodels` (hypothesis testing).
*   **Retention Modeling:**
    *   Since only specific data points (D1, D3, D7, D14) were provided, **Linear Interpolation (`interp1d`)** was used to estimate retention rates for every specific day (Day 0 to Day 30).
    *   For the "New User Source" scenario, an exponential decay model ($Retention = a \cdot e^{b(x-1)}$) was implemented.
*   **Revenue Calculation:**
    *   **IAP Revenue:** $DAU \times Purchase Ratio \times Avg Purchase Price$
    *   **Ad Revenue:** $DAU \times Ad Impressions/DAU \times (eCPM / 1000)$
*   **Statistical Significance:** Two-proportions Z-tests were conducted (95% Confidence Interval) to ensure differences in Purchase Ratios and Retention rates were not due to chance.


## 🔍 Task 1: Key Findings

### a)  Daily Active Users (DAU) after 15 Days

**Question:** Which variant retains more users?

*   **Winner:** **Variant B**

Using interpolated retention values for Days 0–15 and assuming 20,000 new installs per day, the cumulative DAU over the first 15 days is:

Variant A: 846,200

Variant B: 834,700

## 👉 Winner (DAU after 15 days): Variant A 

<img width="1190" height="590" alt="download" src="https://github.com/user-attachments/assets/43234343-6603-41a9-86ee-13c1344f0d49" />



---

### b) Total Revenue by Day 15
**Question:** Which variant earns the most total money by Day 15?

*   **Winner:** **Variant A**

Using purchase ratios, eCPM, ad impressions per DAU, and retention:

Variant A total revenue (Day 1–15): $148,118.85

Variant B total revenue (Day 1–15): $145,888.87

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/64e6ea38-35a2-46fc-b487-695e5581c290" />

---

### c) Total Revenue by Day 30
**Question:**  Does the winner change if we extend the window to Day 30?

*   **Winner:** **Variant B**
After 30 days the slower-decaying retention of Variant B becomes an advantage.

Variant A (Day 30 total): $334,411.42

Variant B (Day 30 total): $352,865.84

Yes — the winner changes when the window is extended.

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/186f2b81-c4b3-46ea-8bbc-b7d3bf94f51d" />

---

### d) Scenario: 10-Day Sale (Day 15-24)
**Question:** What if we run a 10-day sale from Day 15 (+1% absolute purchase rate)?

*   **Winner:** **Variant B**
*  Boosting purchase rate for Days 15–24:

Variant B benefits more due to better mid-to-long-term retention.

Variant B overtakes Variant A even more strongly in this scenario.

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/4dbbd579-3a7c-425c-8b06-b7570f6068b4" />


---

### e) Scenario: New User Source (Day 20)
**Question:** Introducing a new user source (8k/day) with exponential retention curves.

*   **Winner:** **Variant B**

New users follow exponential retention:

A (new): 0.58·e^(−0.12(x−1))

B (new): 0.52·e^(−0.10(x−1))

Variant B maintains a stronger tail and captures more monetization from both old + new user streams.

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/11a8b469-6d9d-43d0-84a2-48ef45b10fc2" />

---

### f) Strategic Recommendation
**Decision:** If we can only make one improvement, we should prioritize **Option 2: Add the new, permanent user source.**
| Option                        | Effect                               | Duration            | Winner                |
| ----------------------------- | ------------------------------------ | ------------------- | --------------------- |
| **10-day sale**               | Short-term IAP boost                 | Temporary (10 days) | Helps B slightly      |
| **New permanent user source** | Sustained retention + revenue growth | Long-term           | Large advantage for B |









