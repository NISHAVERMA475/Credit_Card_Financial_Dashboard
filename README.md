# Credit_Card_Financial_Dashboard
Power Bi Dashboard
Credit Card Weekly Insights Dashboard
A dynamic Power BI dashboard that tracks weekly performance, revenue growth, and customer insights for credit card operations — built using Excel data and DAX for real-time decision-making.  

1. Project Objective
To build a comprehensive weekly dashboard that offers clear, data-driven insights into revenue, transactions, customer segmentation, and card performance — helping stakeholders monitor credit card KPIs effectively.

2. Tech Stack
🟡 Power BI – Visualizations, dashboard design, DAX measures

📗 Excel (CSV) – Data source

🐙 GitHub – Version control, repository hosting

3. Data Preparation
  3.1 Cleaned and structured .csv files

  3.2 Imported directly into Power BI

  3.3 Created calculated columns and measures using DAX for:

    - Revenue

    - Age groups

    - Income segments

    - Weekly comparisons

4. Key DAX Measures
Revenue
Revenue = 'public cc_detail'[annual_fees] + 
          'public cc_detail'[total_trans_amt] + 
          'public cc_detail'[interest_earned]
Age Group
  AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)
Income Group
IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)
Week-on-Week Revenue Comparison
Current_week_Reveneue = CALCULATE(
  SUM('public cc_detail'[Revenue]),
  FILTER(ALL('public cc_detail'),
  'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))
)

Previous_week_Reveneue = CALCULATE(
  SUM('public cc_detail'[Revenue]),
  FILTER(ALL('public cc_detail'),
  'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) - 1)
)
5. Project Highlights
📊 Weekly Revenue Tracking

👥 Customer Segmentation (Age & Income)

💳 Card Type Contribution Analysis

🗺️ State-Wise Revenue Trends

⚠️ Activation Rate & Delinquency Monitoring

📅 Year-to-Date (YTD) Summary

6. Key Insights (Week 53 – 31st Dec)
Revenue increased by 28.8% WoW

YTD Revenue: $57M

Total Interest: $7.98M, Transaction Amount: $46M

Male customers contributed $31M, females $26M

Blue & Silver cards account for 93% of transactions

TX, NY & CA contribute 68% of total transactions

Activation Rate: 56.76%, Delinquent Rate: 5.41%

7. Business Problem & Solution
Problem:
No centralized weekly dashboard for monitoring customer behavior, revenue trends, or regional/card-type performance.

Solution:
Developed an interactive Power BI dashboard using Excel data that enables stakeholders to view performance trends week over week, with deep customer segmentation and actionable insights.

8. Screenshots
Credit card transaction report :
![image](https://github.com/user-attachments/assets/a1cb3e85-345c-460c-98e8-37bfc837addf)
Credit card customer Report :
![image](https://github.com/user-attachments/assets/b1334382-7b10-4972-b6a5-a3b49524c2e2)



