# E-commerce Customer Analytics

This repository contains code and analyses for understanding e-commerce customer behavior using event data. The goal is to identify customer segments and derive actionable insights to improve funnel conversion and marketing strategies.

## Table of Contents

* [Project Overview](#project-overview)
* [Data](#data)
* [Environment Setup](#environment-setup)
* [Usage](#usage)
* [Analysis Workflow](#analysis-workflow)

  * [1. Data Preparation](#1-data-preparation)
  * [2. Funnel Analysis](#2-funnel-analysis)
  * [3. Category & Brand Analysis](#3-category--brand-analysis)
  * [4. Time Series Analysis](#4-time-series-analysis)
  * [5. RFM Segmentation](#5-rfm-segmentation)
  * [6. K-Means Clustering](#6-k-means-clustering)
* [Results](#results)
* [Future Work](#future-work)

---

## Project Overview

The aim of this project is to leverage event log data (views, carts, purchases) from an e-commerce site to:

1. Quantify funnel performance (View ➔ Cart ➔ Purchase)
2. Identify high-performing product categories and brands
3. Analyze temporal patterns in visits and revenue
4. Segment customers into meaningful groups using RFM and k-means clustering

---

## Data

* **Dataset:** [E-commerce behavior data from a multi-category store](https://www.kaggle.com/datasets/mkechinov/ecommerce-behavior-data-from-multi-category-store)
* **Source Schema:** Synthetic event log containing `user_id`, `event_type` (view/cart/purchase), `category_code`, `brand`, `price`, `event_time`.
* **Format:** CSV or Parquet files loaded into a pandas DataFrame `df`.

---

## Environment Setup

```bash
git clone <repo_url>
cd ecommerce-customer-analytics
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

---

## Usage

1. Launch Jupyter Notebook:

   ```bash
   jupyter notebook
   ```
2. Open `Marketing Analytics- E-commerce Customers.ipynb` and run cells sequentially.

---

## Analysis Workflow

### 1. Data Preparation

* Convert `event_time` to datetime and extract `date`.
* Filter event types into separate DataFrames for views, carts, and purchases.

### 2. Funnel Analysis

* Calculate counts for each funnel stage.
* Visualize with bar charts (matplotlib/seaborn) and compute conversion rates.

### 3. Category & Brand Analysis

* Identify top categories by views and by cart/purchase.
* Drill into `electronics.smartphone` to rank top smartphone brands.
* Use colored barplots for clarity.

### 4. Time Series Analysis

* Aggregate daily visitor counts and daily purchase amounts.
* Plot time series to spot peaks (e.g., Black Friday) and trends.

### 5. RFM Segmentation

* Compute Recency (days since last purchase), Frequency (# of purchases), Monetary (total spend) per user.
* Create RFM DataFrame and examine distributions.

### 6. K-Means Clustering

* Scale Frequency and Monetary features.
* Determine optimal `k` with elbow and silhouette methods.
* Apply k-means, assign cluster labels, and visualize segments.

---

## Results

* **Funnel Conversion:** View➔Cart \~4.7%, Cart➔Purchase \~20%.
* **Top Converting Category:** `electronics.smartphone` led both cart additions and purchases.
* **Peak Period:** Black Friday drove spikes in both visits and revenue.
* **Segments Identified:**

  * **Occasionals:** Low frequency, low monetary value.
  * **Big Spenders:** Low frequency, high monetary value.
  * **Frequent Buyers:** High frequency, moderate monetary value.

---

## Future Work

* Incorporate additional features (e.g., product price tiers, acquisition channels).
* Evaluate segmentation stability over time and retrain periodically.
* Build predictive models to target likely buyers with personalized offers.

---
