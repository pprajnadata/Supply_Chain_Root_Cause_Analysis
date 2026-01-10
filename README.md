# Logistics Delivery Bottleneck Analysis (Root Cause Analysis)
#Finding Bottlenecks at Supply chain
🚛 We have all been there: frustrated, checking a delivery app, and imagining our package stuck in a massive traffic jam. But is the "traffic jam" actually the problem? 

This project performs a **Root Cause Analysis (RCA)** on 10,000+ logistics orders to determine if late deliveries are caused by **Transit Failures** or **Merchant Processing Bottlenecks**.

---

## 🧠 The Project Overview
The "Delayed Delivery" tag is a heavy one that usually hurts a logistics team's reputation. To keep the analysis fair and isolate the variables, I used Python to focus on **"local" orders** (distance < 50km). If a short-distance trip takes days, the highway isn't the problem.
![Raw Data Overview](Assets/Rawdata.png)

### The Methodology: "Splitting the Clock"
I used SQL to divide the delivery timeline into two distinct phases:
1. **The Warehouse Phase:** Time from order approval to hand-off to the carrier.
2. **The Road Phase:** Time from the carrier picking up the package to the customer's doorstep.
![SQL Logic Snippet](Assets/Dayslogic.png)


---

## ⚙️ Analytical Logic (SQL)
Using **SQLite**, I implemented a `CASE` statement to compare the two phases. If the Warehouse Phase outweighed the Road Phase, the order was flagged as a **'Merchant Bottleneck'**.


![SQL merchant delay logic used](Assets/Transit_delay.png)
---

## 📊 Key Findings: The "Aha!" Moment

After analyzing 194 short-distance failures, the data revealed a startling reality:
* **Average Warehouse Phase:** ~2.37 Days
* **Average Road Phase:** ~1.05 Days

** Observation:** Even for local trips, warehouse processing time is, on average, **more than double** the actual delivery time.



### Deep Dive: Top Late Orders
When we look at the specific distribution of days spent for the most delayed local orders, the **Merchant/Warehouse time (Blue)** consistently dwarfs the **Driver/Road time (Orange)**.

![Late Order Distribution](Assets/Days_spent_distribution_top5_orders.png)

---

## 🛠️ Processed Data Output
The final transformed dataset identifies the root cause for every late delivery, allowing the business to stop blaming drivers and start addressing the actual source of the delay.

![Final Analysis Table](Assets/Final_analysis.png)

---

## 🚀 Strategic Recommendations
The high-value fix isn't "buying faster trucks"—that’s expensive and ignores the root cause. My data-driven recommendations are:

1. **Merchant Incentives:** Reward sellers who dispatch packages within 24 hours.
2. **Process Optimization:** Streamline warehouse hand-off protocols to reduce the 2.37-day average hold time to may be 2days max.
3. **Targeted Support:** Provide better logistics tools for "Merchant Bottleneck" outliers to solve the delay before the driver even arrives.

---

## 🧰 Tech Stack
* **Language:** Python (Pandas, Matplotlib)
* **Database:** SQL (SQLite3)
* **Environment:** Colab Notebook
