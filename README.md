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

## 🔍 Task 1: Key Findings

### a) Which variant will have the most daily active users after 15 days?

Using interpolated retention values for Days 0–15 and assuming 20,000 new installs per day, the cumulative DAU over the first 15 days is:

Variant A: 846,200

Variant B: 834,700

** 👉 Winner (DAU after 15 days): Variant A 
<img width="1190" height="590" alt="download" src="https://github.com/user-attachments/assets/43234343-6603-41a9-86ee-13c1344f0d49" />



---

### b) Total Revenue by Day 15
**Question:** Which variant earns the most money in the short term?

*   **Winner:** **Variant A**
*   **Insight:** In the short term (15 days), Variant A generates more revenue. This is driven by the significantly higher **Ad Impressions per DAU (2.3 vs 1.6)** and higher early retention (D1), which outweighs Variant B's superior monetization metrics (higher eCPM and Purchase Ratio).

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/64e6ea38-35a2-46fc-b487-695e5581c290" />

---

### c) Total Revenue by Day 30
**Question:** Does the choice change if we look at a longer timeframe?

*   **Winner:** **Variant B**
*   **Insight:** **The strategy flips.** By Day 30, the compounding effect of Variant B's superior late-stage retention (D14+) allows it to overtake Variant A. The higher Life-Time Value (LTV) of users in Variant B compensates for the lower ad volume.

<img width="1033" height="549" alt="download" src="https://github.com/user-attachments/assets/186f2b81-c4b3-46ea-8bbc-b7d3bf94f51d" />

---

### d) Scenario: 10-Day Sale (Day 15-24)
**Question:** If we run a sale boosting conversion by +1%, who wins?

*   **Winner:** **Variant B**
*   **Insight:** Variant B wins by a larger margin. Since Variant B retains users better in the later days (D14+), it has a larger pool of active users available to participate in the sale occurring between Day 15 and 24.

---

### e) Scenario: New User Source (Day 20)
**Question:** Introducing a new user source (8k/day) with exponential retention curves.

*   **Winner:** **Variant B**
*   **Insight:** Even with a mixed traffic source, the fundamental economics remain the same. Variant B's structural advantages in retention and purchase conversion result in higher total revenue by Day 30.

---

### f) Strategic Recommendation
**Decision:** If we can only make one improvement, we should prioritize **Option 2: Add the new, permanent user source.**








