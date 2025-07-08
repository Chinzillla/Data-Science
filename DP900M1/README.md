## Part 1 – Quick Checks (True/False)

1. \_\_\_  CSV and Parquet are both considered *structured* formats.
2. \_\_\_  In a text file, the row terminator always appears **after** the delimiter on each line.
3. \_\_\_  A denormalized table usually uses **more** storage than the fully-normalized equivalent.
4. \_\_\_  JSON and Avro are examples of *unstructured* data formats.
5. \_\_\_  In OLTP systems the ACID “Durability” guarantee means a committed transaction can still roll back if the server crashes immediately afterwards.

---

## Part 2 – Multiple Choice

6. Which of these BEST qualifies as *semi-structured* data?
   a) Raw MPEG-4 video file
   b) Fixed-width COBOL copybook file
   c) DynamoDB item stored as JSON
   d) A gzip-compressed tar archive

7. What is the default row terminator on most Unix-like operating systems?
   a) `\r`
   b) `\n`
   c) `\r\n`
   d) `\t`

8. Which OLAP feature primarily speeds up “drill-down” queries?
   a) Write-ahead logging
   b) Pre-aggregated cubes
   c) Two-phase commits
   d) Vector-based storage

9. You’re exporting a table whose string columns may contain commas **and** line breaks. Which pair of settings will avoid column shifts and merged rows?
   a) Delimiter = `,` Row terminator = `\n`
   b) Delimiter = `|` Row terminator = `\n`
   c) Delimiter = ASCII 31 (unit separator) Row terminator = ASCII 30 (record separator)
   d) Delimiter = `\n` Row terminator = `,`

10. When denormalizing an ecommerce schema to speed up order look-ups, which *new* column would be the MOST sensible to copy onto the **orders** table?
    a) Product inventory count
    b) Customer email address
    c) Supplier bank routing number
    d) Data-warehouse surrogate key

---

## Part 3 – Fill in the Blank

11. The database property that prevents concurrent transactions from interfering with each other is called **\_\_\_\_\_**.
12. A **\_\_\_\_\_** view (or table) stores the pre-computed result of a query to avoid recomputation on every read.
13. In Parquet, data for each column is stored together inside a structure known as a **\_\_\_\_\_** group.
14. A data-lakehouse combines the **flexible storage** of a data ­lake with the **\_\_\_\_\_ semantics** of a data ­warehouse.
15. In a key-value store, the “value” can be any blob, but the **\_\_\_\_\_** must be unique within the table or partition.

---

## Part 4 – Short Answer

16. Describe one **advantage** and one **disadvantage** of schema-on-read engines (e.g., Spark or Athena) when working with semi-structured data.
17. Give two concrete reasons why denormalization can reduce query latency in a read-heavy workload.
18. Explain why storing log files in JSON Lines (`.jsonl`) format rather than plain CSV can simplify downstream analytics.
19. Consider a CSV exported from Windows that suddenly appears as one long line when opened on Linux. What most likely went wrong with the row terminator, and how would you fix it?
20. Outline the ETL (or ELT) flow that moves OLTP data into a data-warehouse cube, naming at least three intermediate steps or layers.

---

## Part 5 – Scenario-Based

### 21. Inventory Dashboard

A start-up keeps daily inventory counts in a normalized relational database:

* `products(product_id PK, name, category)`
* `warehouses(warehouse_id PK, region)`
* `inventory(product_id FK, warehouse_id FK, inventory_date, qty)`

Analysts complain that their Power BI dashboard, which shows **total quantity per product per region for the last 90 days**, takes minutes to refresh.

**Task:** Propose a denormalization or pre-aggregation strategy (schema change, materialized view, or new table) that could cut the query time by 90%. Justify your approach in two or three bullet points.

---

### 22. Log Ingestion Pipeline

You receive 2 TB/day of web-server logs in mixed formats—some JSON Lines, some space-delimited text.
Management wants *near-real-time* error-rate metrics and *monthly* deep-dive analysis of user behavior.

**Task:** Design a storage layout (file format choices, folder partitioning, or database selection) and processing layers that satisfy both latency profiles. Explain how delimiters/row-terminators or record framing influence your design.
