# Promotional Cost Efficiency Analysis

## Objective
To measure the efficiency of promotional spending and analyze the relationship between promotional costs and sales outcomes. The goal is to assess the extent to which promotional expenditures yield a return commensurate with the results achieved.

## Based on the objectives provided, the marketing team has requested an analysis and insights on:
### Effectiveness and Efficiency of Promotions Conducted During 2023, by Calculating the Monthly Overall Promotional Burn Rate.

```sql
SELECT EXTRACT(MONTH FROM order_date) order_month,
	   SUM(purchase_amount_usd) sales,
	   ROUND(SUM(discount/100*purchase_amount_usd),2) promotion_value,
	   ROUND(SUM(discount/100*purchase_amount_usd) / SUM(purchase_amount_usd)*100,2) burn_rate_percentage
FROM customer_transaction
WHERE EXTRACT(YEAR FROM order_date) = 2023
GROUP BY order_month
ORDER BY order_month ASC;
```



#### Insight
From the perspective of sales, there was no growth at all. But the burn rate was relatively increasing in Q1 and Q2. Indicating that the company was inefficiently spending money during these quarters without successfully increasing sales. However, in Q3 and Q4, the company managed to stabilize the burn rate percentage.



