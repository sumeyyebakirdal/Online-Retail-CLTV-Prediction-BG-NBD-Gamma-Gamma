# Online Retail CLTV Prediction with BG-NBD & Gamma-Gamma

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![Lifetimes](https://img.shields.io/badge/lifetimes-v0.11.3-orange)
![Business](https://img.shields.io/badge/Focus-CRM_Analytics-red)

## 📌 Business Problem
A UK-based retail company wants to determine a roadmap for its sales and marketing activities. To make medium-to-long-term plans, the company needs to predict the potential value that existing customers will provide in the future.

This project focuses on predicting the **Customer Lifetime Value (CLTV)** for UK customers using probabilistic models, helping the company identify high-potential customers and optimize marketing spend.

---

## 📂 Dataset Story
The dataset **"Online Retail II"** contains online sales transactions of a UK-based retail company between 01/12/2009 and 09/12/2011. The company specializes in unique all-occasion gift items.

* **Dataset Source:** [Kaggle - Online Retail II Dataset](https://www.kaggle.com/datasets/lakshmi25npathi/online-retail-dataset)
* **Target Audience:** Wholesale and individual customers.
* **Key Features:** Invoice, StockCode, Quantity, InvoiceDate, Price, Customer ID, Country.

---

## 🛠️ Project Roadmap & Tasks

### 1. Data Preparation
* Cleaned missing values and removed cancelled transactions (Invoices starting with 'C').
* Filtered the data for **United Kingdom** customers only.
* Handled outliers using the **Interquartile Range (IQR)** method to ensure model stability.

### 2. Creating CLTV Structure
Calculated RFM metrics in a weekly format:
* **Recency:** Time since the first and last purchase.
* **T (Tenure):** Age of the customer since the first purchase.
* **Frequency:** Total number of repeat purchases (Frequency > 1).
* **Monetary:** Average revenue per transaction.

### 3. BG-NBD & Gamma-Gamma Modeling
* **BG-NBD:** Predicted the "Expected Number of Transactions" for customers.
* **Gamma-Gamma:** Predicted the "Expected Average Profit" per customer.

### 4. CLTV Forecasting (Time Periods)
Generated predictions for different time horizons as requested in the project requirements:
* 1-Month CLTV Prediction
* 6-Month CLTV Prediction (Primary target)
* 12-Month CLTV Prediction



### 5. Segmentation
Divided customers into 4 segments (A, B, C, D) based on 6-month CLTV values.
* **Segment A:** High-value "Champions" requiring VIP services.
* **Segment D:** Low-value or at-risk customers requiring reactivation.

---

## 🚀 Key Insights
* Analyzing the difference between 1-month and 12-month CLTV allows us to see which customers are likely to stay loyal in the long run versus those who provide quick short-term gains.
* The model helps in shifting the focus from "Total Revenue" to "Predicted Future Profitability."

---
