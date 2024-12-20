# Danny's Diner SQL Case Study

Welcome to the **Danny's Diner SQL Case Study Solved by PRAVALLIKA MADDI** repository! This project was created to showcase SQL queries and provide insights into a fictional restaurant's operations. The goal is to demonstrate how to leverage SQL to analyze customer behavior, spending patterns, and menu popularity in the context of Danny’s Diner.

## Introduction

Danny seriously loves Japanese food so in the beginning of 2021, he decides to embark upon a risky venture and opens up a cute little restaurant that sells his 3 favourite foods: sushi, curry and ramen.

Danny’s Diner is in need of your assistance to help the restaurant stay afloat - the restaurant has captured some very basic data from their few months of operation but have no idea how to use their data to help them run the business.

## Problem Statement
Danny wants to use the data to answer a few simple questions about his customers, especially about their visiting patterns, how much money they’ve spent and also which menu items are their favourite. Having this deeper connection with his customers will help him deliver a better and more personalised experience for his loyal customers.

He plans on using these insights to help him decide whether he should expand the existing customer loyalty program - additionally he needs help to generate some basic datasets so his team can easily inspect the data without needing to use SQL.

Danny has provided you with a sample of his overall customer data due to privacy issues - but he hopes that these examples are enough for you to write fully functioning SQL queries to help him answer his questions!

Danny has shared with you 3 key datasets for this case study:

->sales
->menu
->members

### Key Datasets

Danny has shared three key datasets for this case study:

- **sales**: Contains records of customer purchases, including product IDs, order dates, and customer IDs.
- **menu**: Details about the menu items, including product IDs, names, and prices.
- **members**: Contains records of customers who have joined the loyalty program, including their customer IDs and join dates.

The goal is to write fully functioning SQL queries based on these datasets to help Danny analyze and solve the key business questions he has.


### Example Datasets

#### 1. **sales** Table

The **sales** table captures customer-level purchases, the corresponding `order_date`, and the `product_id` that maps to items on the menu.

| customer_id | order_date | product_id |
|-------------|------------|------------|
| A           | 2021-01-01 | 1          |
| A           | 2021-01-01 | 2          |
| A           | 2021-01-07 | 2          |
| A           | 2021-01-10 | 3          |
| A           | 2021-01-11 | 3          |
| A           | 2021-01-11 | 3          |
| B           | 2021-01-01 | 2          |
| B           | 2021-01-02 | 2          |
| B           | 2021-01-04 | 1          |
| B           | 2021-01-11 | 1          |
| B           | 2021-01-16 | 3          |
| B           | 2021-02-01 | 3          |
| C           | 2021-01-01 | 3          |
| C           | 2021-01-01 | 3          |
| C           | 2021-01-07 | 3          |

#### 2. **menu** Table

The **menu** table associates `product_id` with product names and their prices. This data is used to relate purchases in the **sales** table to the items ordered and their costs.

| product_id | product_name | price |
|------------|--------------|-------|
| 1          | sushi        | 10    |
| 2          | curry        | 15    |
| 3          | ramen        | 12    |

#### 3. **members** Table

The **members** table tracks when each customer joined the loyalty program.

| customer_id | join_date  |
|-------------|------------|
| A           | 2021-01-07 |
| B           | 2021-01-09 |

## Project Overview

In the first few months, Danny has been collecting data through a loyalty program that captures customer behavior and sales trends. The project involves analyzing this data to:
1. Calculate total spending by customers.
2. Evaluate customer visit frequency.
3. Identify the most popular items on the menu.
4. Analyze the impact of the loyalty program on customers.

By using SQL queries to analyze this data, you’ll be able to provide Danny with the insights he needs to better understand his customers and make informed business decisions.

## Repository Structure

This repository contains the following key files:

1. **SQL Queries**: 
   - Queries to answer specific business questions such as total spending, popular items, and customer visit frequency.
   - SQL scripts (found in the `queries.sql` file) for running these queries in a database.
   
2. **HTML/CSS Showcase**: 
   - A simple HTML page demonstrating the SQL results visually.
   - A CSS file that styles the showcase to make it visually appealing.
   - **index.html**: Displays the results of the SQL queries in a clean layout.

3. **README.md**: This file, providing an overview of the repository and instructions.

## Instructions

1. **Setting Up the Database**:
   - Clone this repository to your local machine.
   - Set up the database by running the following SQL commands in your database management system (such as PostgreSQL, MySQL, etc.).
   - You can download the SQL files (e.g., `dannys_diner_schema.sql`) and run them to create the required tables (`sales`, `menu`, `members`).

2. **Running Queries**:
   - Use the `queries.sql` file to run the SQL queries and generate reports.
   - Here are some of the important SQL queries included in the project:
     - **Total Spending**: Find the total amount spent by each customer.
     - **Visit Frequency**: Calculate the number of days each customer visited the restaurant.
     - **Most Popular Items**: Find the most frequently ordered items.
     - **Loyalty Program Analysis**: Analyze customers’ behavior before and after joining the loyalty program.

3. **Viewing Results on the Web**:
   - Open the `index.html` file in your browser to see the formatted results of the SQL queries.
   - To update the content daily, simply edit the file and commit changes on GitHub.

4. **Adding Updates**:
   - You can add or modify content by editing the HTML directly in this repository. Whenever a change is needed, follow these steps:
     - Open the relevant HTML file, edit the content, and commit the changes with a detailed message.

## Questions to Answer:

1. **Total Amount Spent by Each Customer**:
   - What is the total amount each customer spent at the restaurant?

2. **Number of Days Each Customer Visited**:
   - How many days has each customer visited the restaurant?

3. **First Item Purchased by Each Customer**:
   - What was the first item from the menu purchased by each customer?

4. **Most Purchased Item on the Menu**:
   - What is the most purchased item on the menu and how many times was it purchased by all customers?

5. **Most Popular Item for Each Customer**:
   - Which item was the most popular for each customer?

6. **Item Purchased First After Customer Became a Member**:
   -Which item was purchased first by the customer after they became a member?

7. **Item Purchased Just Before Membership**:
   - Which item was purchased just before the customer became a member?

8. **Total Items and Amount Spent Before Membership**:
   - What is the total items and amount spent for each member before they became a member?

9. **Points Calculation (10 Points per $1 Spent, Sushi has 2x Multiplier)**:
   - If each $1 spent equates to 10 points and sushi has a 2x points multiplier - how many points would each customer have?

10. **Points for the First Week After Membership**:
    - In the first week after a customer joins the program (including their join date) they earn 2x points on all items, not just sushi - how many points do customer A and B have at the end of January?

## Example Queries:

### 1. Total Amount Spent by Each Customer:
```sql
SELECT s.customer_id, SUM(m.price) AS total_sales 
FROM sales s 
JOIN menu m ON s.product_id = m.product_id 
GROUP BY s.customer_id 
ORDER BY s.customer_id;
```
## Bonus Questions:

1.**Join All The Things**:
-The following questions are related creating basic data tables that Danny and his team can use to quickly derive insights without needing to join the underlying tables using SQL.

  -Recreate the following table output using the available data.

| Customer ID | Order Date   | Product Name | Price | Member |
|-------------|--------------|--------------|-------|--------|
| A           | 2021-01-01  | curry        | 15    | N      |
| A           | 2021-01-01  | sushi        | 10    | N      |
| A           | 2021-01-07  | curry        | 15    | Y      |
| A           | 2021-01-10  | ramen        | 12    | Y      |
| A           | 2021-01-11  | ramen        | 12    | Y      |
| A           | 2021-01-11  | ramen        | 12    | Y      |
| B           | 2021-01-01  | curry        | 15    | N      |
| B           | 2021-01-02  | curry        | 15    | N      |
| B           | 2021-01-04  | sushi        | 10    | N      |
| B           | 2021-01-11  | sushi        | 10    | Y      |
| B           | 2021-01-16  | ramen        | 12    | Y      |
| B           | 2021-02-01  | ramen        | 12    | Y      |
| C           | 2021-01-01  | ramen        | 12    | N      |
| C           | 2021-01-01  | ramen        | 12    | N      |
| C           | 2021-01-07  | ramen        | 12    | N      |


2.**Rank All The Things**:

-Danny also requires further information about the ranking of customer products, but he purposely does not need the ranking for non-member purchases so he expects null ranking values for the records when customers are not yet part of the loyalty program.

| Customer ID | Order Date   | Product Name | Price | Member | Ranking |
|-------------|--------------|--------------|-------|--------|---------|
| A           | 2021-01-01  | curry        | 15    | N      | null    |
| A           | 2021-01-01  | sushi        | 10    | N      | null    |
| A           | 2021-01-07  | curry        | 15    | Y      | 1       |
| A           | 2021-01-10  | ramen        | 12    | Y      | 2       |
| A           | 2021-01-11  | ramen        | 12    | Y      | 3       |
| A           | 2021-01-11  | ramen        | 12    | Y      | 3       |
| B           | 2021-01-01  | curry        | 15    | N      | null    |
| B           | 2021-01-02  | curry        | 15    | N      | null    |
| B           | 2021-01-04  | sushi        | 10    | N      | null    |
| B           | 2021-01-11  | sushi        | 10    | Y      | 1       |
| B           | 2021-01-16  | ramen        | 12    | Y      | 2       |
| B           | 2021-02-01  | ramen        | 12    | Y      | 3       |
| C           | 2021-01-01  | ramen        | 12    | N      | null    |
| C           | 2021-01-01  | ramen        | 12    | N      | null    |
| C           | 2021-01-07  | ramen        | 12    | N      | null    |


## For Bonus Queries Solutions:

[Click Here](https://pravallikamaddi.github.io/Danny-Diner-SQL-Case-Study/Bonus.html)

## Conclusion:
**!really hope you enjoyed this fun little case study - it definitely was fun for me to create!**

## FOR ALL QUERIES (Solutions):

[Click Here](https://pravallikamaddi.github.io/Danny-Diner-SQL-Case-Study/)






