# UK Internet Retail Sales – Explaining and Predicting Online Sales Over Time 📈

## 🧠 Project overview

This project looks at UK internet retail sales over time and tries to answer a simple question:

**What drives online retail sales, and how did Covid change people's shopping behaviour?**

Using time series data on monthly UK internet sales, I build a simple, explainable model that links
current online sales to past sales, Covid, and store types (for example, food vs clothing stores).

---

## 📦 Data

- **Source:** [Office for National Statistics (ONS) – UK internet sales data](https://www.ons.gov.uk/businessindustryandtrade/retailindustry/datasets/retailsalesindexinternetsales)  
- **Frequency:** Monthly  
- **Location:** United Kingdom  
- **Target:** Internet retail sales in £  

Each row represents **one month**, with columns such as:

- Internet sales value  
- Store type (e.g. food, textile/clothing/footwear, etc.)  
- Time-related features (month, year)  
- Covid period indicator (0 = non-Covid month, 1 = Covid month)  
- Lagged values of internet sales (last month, last year)

---

## 🎯 Modelling goal

The aim of the model is to **explain and predict UK internet retail sales over time**.  
In particular, I want to:

- See how much **current online sales depend on past sales**  
  (short-term momentum and seasonal patterns).
- **Measure the impact of Covid** on internet shopping in a quantitative way.  
- **Compare different types of shops** (e.g. food vs clothing/footwear) in terms of their online sales performance.

---

## 🔧 Methods

I use **multiple linear regression (OLS)** as a simple, transparent model:

- It’s **easy to explain** – it tells us how much we expect sales to change when one factor moves,
  assuming everything else is held constant.
- It shows **which factors really matter**, and which have little effect.  
- It’s a solid **baseline**: if this model already explains most of the variation, we don’t need
  more complex “black box” methods to understand the main story.

Key features in the model:

- **Lagged sales:**
  - `last_month_value` – sales in the previous month  
  - `last_year_value` – sales in the same month one year ago  
- **Covid dummy:** indicator for months during the Covid period  
- **Store type dummies:** to compare different shop categories

---

## 🔍 Main findings

In this section I translate the model output into plain English:

- **Past sales are the strongest drivers.**  
  Sales this month are very similar to last month’s. The coefficient for `last_month_value` is
  about **0.96**, meaning that if last month’s sales go up by 1 unit, this month’s sales go up by
  roughly **0.96 units**, all else equal. There is also a smaller, but still meaningful effect from
  sales in the **same month last year** (coefficient ≈ **0.036**), which captures seasonal patterns.

- **Covid gave a clear boost to online sales.**  
  The Covid indicator has a coefficient of about **+43.3**. After we control for time and past sales,
  months during the Covid period still have internet sales that are on average about **43 units higher**
  than comparable non-Covid months. This quantifies the uplift in online retail during the pandemic.

- **Store types behave differently.**  
  By including store type dummies, the model can compare categories like **food** vs
  **textile/clothing/footwear** in terms of their online performance.  
  *(Here you can add 1–2 bullets about which store types performed better or worse, based on your results.)*

---


