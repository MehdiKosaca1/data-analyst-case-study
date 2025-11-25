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

a) Which variant will have the most daily active users after 15 days?

Using interpolated retention values for Days 0–15 and assuming 20,000 new installs per day, the cumulative DAU over the first 15 days is:

Variant A: 846,200

Variant B: 834,700

👉 Winner (DAU after 15 days): Variant A

b) Which variant earns the most total money by Day 15?

Daily revenue =
In-app purchase revenue + Ad revenue

Using purchase ratios, eCPM, ad impressions per DAU, and retention:

Variant A total revenue (Day 1–15): $148,118.85

Variant B total revenue (Day 1–15): $145,888.87

👉 Winner (Day 15 revenue): Variant A

c) Does the winner change if we extend the window to Day 30?

After 30 days the slower-decaying retention of Variant B becomes an advantage.

Variant A (Day 30 total): $334,411.42

Variant B (Day 30 total): $352,865.84

👉 Winner (Day 30 revenue): Variant B
Yes — the winner changes when the window is extended.

d) What if we run a 10-day sale from Day 15 (+1% absolute purchase rate)?

Boosting purchase rate for Days 15–24:

Variant B benefits more due to better mid-to-long-term retention.

Variant B overtakes Variant A even more strongly in this scenario.

👉 Winner with 10-day sale: Variant B

e) Adding a new user source on Day 20 (12k old + 8k new users/day)

New users follow exponential retention:

A (new): 0.58·e^(−0.12(x−1))

B (new): 0.52·e^(−0.10(x−1))

Variant B maintains a stronger tail and captures more monetization from both old + new user streams.

👉 Winner with new user source: Variant B








