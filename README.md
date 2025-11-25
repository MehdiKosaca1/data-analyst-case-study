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

## Key Findings (Task 1-A):
| Variant | Total DAU |
| ------- | --------- |
| **A**   | 76,486    |
| **B**   | 79,014    |

## Winner: Variant B









