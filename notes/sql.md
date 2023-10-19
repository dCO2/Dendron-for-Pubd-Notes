---
id: d049v5agaal82wytcmoz2de
title: sql
desc: ''
updated: 1697717653667
created: 1697018682151
---

- ![[what i expect from exposés on technologies#^anchor-tech-get-started]]
  - CREATE TABLE, ALTER TABLE, SELECT, FROM, WHERE, DISTINCT, LIMIT, GROUP BY, JOIN, UNION, INSERT INTO, SET, UPDATE, DELETE, DROP, COUNT, SUM, AVG,...
- ![[what i expect from exposés on technologies#^anchor-tech-internals]]
  - [SQL queries don't start with SELECT](https://news.ycombinator.com/item?id=21150606)
  - [Best practices for writing SQL queries](https://news.ycombinator.com/item?id=26762206)
  - [Speeding up SQL queries by orders of magnitude using UNION](https://news.ycombinator.com/item?id=26524776)
  - innoDB pages (https://stackoverflow.com/questions/4401910/mysql-what-is-a-page)
- ![[what i expect from exposés on technologies#^anchor-production-problems]]
  - **general**
    - If you have a relational database sharded across multiple servers, how do you generate the uniqueid column, if the id automatically increments, in such a way that there are no id collisions?
    - SQL tuning (tighten up the schema): Use CHAR instead of VARCHAR for fixed-length fields?
    - `NOT NULL` improves search performance?
    - pass
  - **sql queries**
    - (window functions) "determine cumulative sales for each month for a business"? `SELECT month, sales, SUM(sales) OVER (ORDER BY month) AS cumulative_sales FROM sales_data;`
    - (common table expressions) "determine the average age of customers who have bought a particular product" `WITH product_customers AS (SELECT name, age FROM customer_data WHERE product = 'widget') SELECT AVG(age) AS avg_age FROM product_customers;`
    - (recursive queries) "calculate the total cost of a series of interconnected transactions"
      - "identify the shortest path between two nodes in a network":
      ```sql
          WITH RECURSIVE job_categories AS (
            SELECT job_title, COUNT(*) AS employee_count
            FROM employee_data
            GROUP BY job_title
            UNION ALL
            SELECT e.job_title, COUNT(*) AS employee_count
            FROM employee_data e
            JOIN job_categories jc ON e.supervisor = jc.job_title
            GROUP BY e.job_title
          )
          SELECT job_title, SUM(employee_count) AS total_employees
          FROM job_categories
          GROUP BY job_title;
      ```
      - `WITH RECURSIVE job_categories AS (SELECT job_title, COUNT(*) AS employee_count FROM employee_data GROUP BY job_title UNION ALL SELECT e.job_title, COUNT(*) AS employee_count FROM employee_data e JOIN job_categories jc ON e.supervisor = jc.job_title GROUP BY e.job_title ) SELECT job_title, SUM(employee_count) AS total_employees FROM job_categories GROUP BY job_title;`
    <!-- - <details>
        <summary>"tricky queries" (GPT generated):</summary>
        - **Inventory Valuation with FIFO Method:**
          ```sql
          SELECT product_id, product_name,
            SUM(quantity * cost) as total_inventory_value
          FROM (
            SELECT *,
              ROW_NUMBER() OVER (PARTITION BY product_id ORDER BY purchase_date) as rn
            FROM inventory_purchases
          ) ranked_purchases
          JOIN products ON ranked_purchases.product_id = products.product_id
          WHERE rn = 1
          GROUP BY product_id, product_name;
          ```
        - **Employee Shift Scheduling:**
          ```sql
          WITH Shifts AS (
            SELECT employee_id, shift_date, shift_type,
              LAG(shift_type) OVER (PARTITION BY employee_id ORDER BY shift_date) as previous_shift
            FROM employee_schedule
          )
          SELECT employee_id, shift_date, shift_type
          FROM Shifts
          WHERE shift_type = 'Night' AND previous_shift = 'Day';
          ```
        - **Customer Cohort Analysis:**
          ```sql
          WITH Cohort AS (
            SELECT
              DATE_DIFF(order_date, registration_date, DAY) as days_since_registration,
              COUNT(DISTINCT customer_id) as cohort_size
            FROM orders
            GROUP BY days_since_registration
          )
          SELECT days_since_registration, cohort_size
          FROM Cohort
          ORDER BY days_since_registration;
          ```
        - **Time Series Forecasting:**
          ```sql
          WITH MonthlySales AS (
            SELECT DATE_TRUNC('month', order_date) AS month,
              SUM(sales_amount) as total_sales
            FROM sales
            GROUP BY month
          )
          SELECT month, total_sales,
            AVG(total_sales) OVER (ORDER BY month ROWS BETWEEN 2 PRECEDING AND 2 FOLLOWING) as moving_average
          FROM MonthlySales;
          ```
        - **Dynamic Pricing Strategy:**
          ```sql
          SELECT product_id, product_name,
            price * (CASE WHEN stock_quantity > 100 THEN 0.9 ELSE 1.2 END) as dynamic_price
          FROM products;
          ```
        - **Nested Categories:**
          ```sql
          WITH RecursiveCategories AS (
            SELECT category_id, category_name, parent_category_id
            FROM categories
            WHERE parent_category_id IS NULL
            UNION ALL
            SELECT c.category_id, c.category_name, c.parent_category_id
            FROM RecursiveCategories rc
            JOIN categories c ON rc.category_id = c.parent_category_id
          )
          SELECT category_id, category_name, parent_category_id
          FROM RecursiveCategories;
          ```
        - **User Engagement Analysis:**
          ```sql
          WITH UserEngagement AS (
            SELECT user_id, event_date,
              ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY event_date) as event_sequence
            FROM user_events
          )
          SELECT user_id, event_date,
            event_sequence - LAG(event_sequence) OVER (PARTITION BY user_id ORDER BY event_date) as time_between_events
          FROM UserEngagement;
          ```
        - **Retail Store Analytics:**
          ```sql
          WITH SalesSummary AS (
            SELECT store_id, DATE_TRUNC('week', sale_date) AS week,
              SUM(sales_amount) as weekly_sales
            FROM store_sales
            GROUP BY store_id, week
          )
          SELECT store_id, week, weekly_sales,
            LAG(weekly_sales) OVER (PARTITION BY store_id ORDER BY week) as previous_week_sales
          FROM SalesSummary;
          ```
        - **Network Security Analysis:**
          ```sql
          WITH SuspiciousActivity AS (
            SELECT source_ip, COUNT(*) as activity_count
            FROM network_logs
            GROUP BY source_ip
            HAVING activity_count > 1000
          )
          SELECT source_ip, activity_count
          FROM SuspiciousActivity;
          ```
        - **Customer Segmentation:**
          ```sql
          SELECT customer_id, customer_name, total_orders, total_spent,
            NTILE(4) OVER (ORDER BY total_spent) as spending_quartile
          FROM (
            SELECT c.customer_id, c.customer_name,
              COUNT(o.order_id) as total_orders, SUM(o.total_amount) as total_spent
            FROM customers c
            JOIN orders o ON c.customer_id = o.customer_id
            GROUP BY c.customer_id, c.customer_name
          ) CustomerSummary;
          ```
      </details> -->
    - "tricky queries" (GPT generated): 
    - **Inventory Valuation with FIFO Method:**
      ```sql
      SELECT product_id, product_name,
        SUM(quantity * cost) as total_inventory_value
      FROM (
        SELECT *,
          ROW_NUMBER() OVER (PARTITION BY product_id ORDER BY purchase_date) as rn
        FROM inventory_purchases
      ) ranked_purchases
      JOIN products ON ranked_purchases.product_id = products.product_id
      WHERE rn = 1
      GROUP BY product_id, product_name;
      ```
    - **Employee Shift Scheduling:**
      ```sql
      WITH Shifts AS (
        SELECT employee_id, shift_date, shift_type,
          LAG(shift_type) OVER (PARTITION BY employee_id ORDER BY shift_date) as previous_shift
        FROM employee_schedule
      )
      SELECT employee_id, shift_date, shift_type
      FROM Shifts
      WHERE shift_type = 'Night' AND previous_shift = 'Day';
      ```
    - **Customer Cohort Analysis:**
      ```sql
      WITH Cohort AS (
        SELECT
          DATE_DIFF(order_date, registration_date, DAY) as days_since_registration,
          COUNT(DISTINCT customer_id) as cohort_size
        FROM orders
        GROUP BY days_since_registration
      )
      SELECT days_since_registration, cohort_size
      FROM Cohort
      ORDER BY days_since_registration;
      ```
    - **Time Series Forecasting:**
      ```sql
      WITH MonthlySales AS (
        SELECT DATE_TRUNC('month', order_date) AS month,
          SUM(sales_amount) as total_sales
        FROM sales
        GROUP BY month
      )
      SELECT month, total_sales,
        AVG(total_sales) OVER (ORDER BY month ROWS BETWEEN 2 PRECEDING AND 2 FOLLOWING) as moving_average
      FROM MonthlySales;
      ```
    - **Dynamic Pricing Strategy:**
      ```sql
      SELECT product_id, product_name,
        price * (CASE WHEN stock_quantity > 100 THEN 0.9 ELSE 1.2 END) as dynamic_price
      FROM products;
      ```
    - **Nested Categories:**
      ```sql
      WITH RecursiveCategories AS (
        SELECT category_id, category_name, parent_category_id
        FROM categories
        WHERE parent_category_id IS NULL
        UNION ALL
        SELECT c.category_id, c.category_name, c.parent_category_id
        FROM RecursiveCategories rc
        JOIN categories c ON rc.category_id = c.parent_category_id
      )
      SELECT category_id, category_name, parent_category_id
      FROM RecursiveCategories;
      ```
    - **User Engagement Analysis:**
      ```sql
      WITH UserEngagement AS (
        SELECT user_id, event_date,
          ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY event_date) as event_sequence
        FROM user_events
      )
      SELECT user_id, event_date,
        event_sequence - LAG(event_sequence) OVER (PARTITION BY user_id ORDER BY event_date) as time_between_events
      FROM UserEngagement;
      ```
    - **Retail Store Analytics:**
      ```sql
      WITH SalesSummary AS (
        SELECT store_id, DATE_TRUNC('week', sale_date) AS week,
          SUM(sales_amount) as weekly_sales
        FROM store_sales
        GROUP BY store_id, week
      )
      SELECT store_id, week, weekly_sales,
        LAG(weekly_sales) OVER (PARTITION BY store_id ORDER BY week) as previous_week_sales
      FROM SalesSummary;
      ```
    - **Network Security Analysis:**
      ```sql
      WITH SuspiciousActivity AS (
        SELECT source_ip, COUNT(*) as activity_count
        FROM network_logs
        GROUP BY source_ip
        HAVING activity_count > 1000
      )
      SELECT source_ip, activity_count
      FROM SuspiciousActivity;
      ```
    - **Customer Segmentation:**
      ```sql
      SELECT customer_id, customer_name, total_orders, total_spent,
        NTILE(4) OVER (ORDER BY total_spent) as spending_quartile
      FROM (
        SELECT c.customer_id, c.customer_name,
          COUNT(o.order_id) as total_orders, SUM(o.total_amount) as total_spent
        FROM customers c
        JOIN orders o ON c.customer_id = o.customer_id
        GROUP BY c.customer_id, c.customer_name
      ) CustomerSummary;
      ```
    - Ranking Rows Based on a Specific Ordering Criteria
    - List The First 5 Rows of a Result Set
    - List the Last 5 Rows of a Result Set
    - List The Second Highest Row of a Result Set
    - List the Second Highest Salary By Department
    - List the First 50% Rows in a Result Set
    - List the Last 25% Rows in a Result Set
    - Number the Rows in a Result Set
    - List All Combinations of Rows from Two Tables
    - Join a Table to Itself
    - Join a Table to Itself
    - Employees with Salaries Higher Than Their Departmental Average
    - Obtain All Rows Where a Value Is in a Subquery Result
    - Find Duplicate Rows
    - Count Duplicate Rows
    - Find Common Records Between Tables
    - Grouping Data with ROLLUP
    - Conditional Summation
    - Group Rows by a Range
    - Compute a Running Total
    - Compute a Moving Average
    - Compute a Difference (Delta) Between Two Columns on Different Rows [source](https://learnsql.com/blog/25-advanced-sql-query-examples/)
    - how to select distinct values in a field, alongside other fields
- inverted index (https://sirupsen.com/napkin/problem-10-mysql-transactions-per-second/)
- define a composite primary key in SQL (https://sirupsen.com/napkin/problem-6)
  - `PRIMARY KEY (FieldID1, FieldID2)`
  - https://stackoverflow.com/questions/1110349/how-can-i-define-a-composite-primary-key-in-sql
- netpin's migration.sql
  - why should you not conceive it as a user having a list of notes & a note having a single user, but instead, a note having a relation to a user? ([[documenting netpin]]) 
  - `CONSTRAINT "User_pkey" PRIMARY KEY ("uid")`
  - `ALTER TABLE`
  - `CREATE UNIQUE INDEX "User_name_key" ON "User"("name");`
  - ```sql
    -- CreateTable
    CREATE TABLE "User" (
        "uid" INT4 NOT NULL DEFAULT unique_rowid(),
        "name" STRING NOT NULL,
        "createdAt" TIMESTAMP(3) NOT NULL DEFAULT CURRENT_TIMESTAMP,
        "expiresAt" TIMESTAMP(3),

        CONSTRAINT "User_pkey" PRIMARY KEY ("uid")
    );

    -- CreateTable
    CREATE TABLE "Note" (
        "nid" INT4 NOT NULL DEFAULT unique_rowid(),
        "rid" INT4 NOT NULL,
        "link" STRING NOT NULL,
        "createdAt" TIMESTAMP(3) NOT NULL DEFAULT CURRENT_TIMESTAMP,
        "expiresAt" TIMESTAMP(3),
        "title" STRING NOT NULL,
        "content" STRING NOT NULL,

        CONSTRAINT "Note_pkey" PRIMARY KEY ("nid")
    );

    -- CreateIndex
    CREATE UNIQUE INDEX "User_name_key" ON "User"("name");

    -- CreateIndex
    CREATE UNIQUE INDEX "Note_link_key" ON "Note"("link");

    -- CreateIndex
    CREATE UNIQUE INDEX "Note_title_key" ON "Note"("title");

    -- CreateIndex
    CREATE UNIQUE INDEX "Note_content_key" ON "Note"("content");

    -- AddForeignKey
    ALTER TABLE "Note" ADD CONSTRAINT "Note_rid_fkey" FOREIGN KEY ("rid") REFERENCES "User"("uid") ON DELETE RESTRICT ON UPDATE CASCADE;
  
  ```
- pass