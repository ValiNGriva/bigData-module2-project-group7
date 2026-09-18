# 1. Problem & Executive Summary (0:00 – 1:00)
Speaker Script:
"Welcome, everyone. Today we’ll walk through how we built a data pipeline to unlock insights from the Olist Brazilian E-Commerce dataset. Our business goal is clear: improve Delivery Performance. We want to know where and when deliveries are delayed, how that affects customer reviews, and what revenue is at risk when logistics slow down.

To answer these questions, we designed a pipeline that ensures reliable, high-quality data every step of the way."

# 2. Data Pipeline Concept & High-Level Architecture (1:00 – 2:20)
**Visual Asset: Excalidraw**

Speaker Script:
"At the start, we had two choices for loading the data:
- Option A: Use a complex framework designed for live, constantly changing data.

- Option B: Use a simpler and automated command-line tasks approach tailored for static files.

Since Olist is a fixed dataset — one large CSV file — we chose Option B. It’s leaner, faster, and avoids unnecessary complexity.

From there, our pipeline flows through three clear phases:
- Extract & Load: Bring the raw CSV into Google BigQuery.

- Transform: Organize and clean the data into a structured model that highlights delivery performance.

- Consumption: Feed those insights into an executive dashboard for decision-making.

We also built in two quality checkpoints to make sure only clean, trustworthy data moves forward. This way, executives can rely on the numbers without second-guessing."

# 3. Star Schema Modeling & dbt Implementation (2:20 – 3:30)
**Visual Asset: dbt Docs(Lineage Graph)**

Speaker Script:
"To make the data useful, we shaped it into a star schema — a simple, business-friendly model.

Here’s why that matters:

- We keep delivery delays measured at the order level, while revenue is tracked at the item level. Mixing them would distort results.

- We simplify reviews, payments, and customer details so they align neatly with orders.

- We reduce geographic detail to zip-code prefixes, making route analysis easier.

Finally, we run automated checks to confirm that totals match across layers. This ensures the insights are consistent and reliable."

**Visual Asset: Excalidraw**

"Dagster models the pipeline as asset lineage: `manifest → GX gate → BigQuery load → dbt models`"

# 4. Business Case Demo — Streamlit Dashboard (3:30 – 7:30)
Speaker Script:
"Let’s look at the dashboard:

- Where: Pinpoint routes with the most delays.

- When: Break down whether delays come from sellers or couriers.

- What it Costs: Show the revenue and review score impact of late deliveries."

# 5. Recommendations & Executive Roadmap (8:40 – 10:00)
Speaker Script:
"In summary, we turned a raw dataset into a decision engine for logistics.

Our recommendations:

- Fix Delivery Promises: Adjust estimated delivery dates to reduce artificial lateness.

- Carrier SLA Renegotiation: Focus on the top five delayed routes and renegotiate contracts.

- High-Value Customer Protection: Offer proactive vouchers to VIP customers impacted by delays.

This roadmap helps restore customer trust and protect revenue."