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
FROM
	customer_transaction
WHERE
	EXTRACT(YEAR FROM order_date) = 2023
GROUP BY
	order_month
ORDER BY
	order_month ASC;
```

#### Insight
From the perspective of sales, there was no growth at all. But the burn rate was relatively increasing in Q1 and Q2. Indicating that the company was inefficiently spending money during these quarters without successfully increasing sales. However, in Q3 and Q4, the company managed to stabilize the burn rate percentage.

### Effectiveness and Efficiency of Promotions Conducted During 2023, by Calculating the Promotional Burn Rate by Product Category and Month.

```sql
SELECT EXTRACT(MONTH FROM order_date) order_month,
	   category,
	   SUM(purchase_amount_usd) sales,
	   ROUND(SUM(discount/100*purchase_amount_usd),2) promotion_value,
	   ROUND(SUM(discount/100*purchase_amount_usd) / SUM(purchase_amount_usd)*100,2) burn_rate_percentage
FROM
	customer_transaction
WHERE
	EXTRACT(YEAR FROM order_date) = 2023
GROUP BY
	order_month, category
ORDER BY
	order_month ASC, category;
```

#### Insight
There are product categories where the burn rate has exceeded the maximum expected rate of 43%, specifically in the <b>footwear</b> and <b>outerwear</b> categories. However, these categories actually have low sales figures, indicating that the company is spending a lot on promotions for products that are not growing, or these categories are consuming significant promotional budgets without yielding the expected sales results.

#### Note
This is one of projects in GenggamData SQL Bootcamp
