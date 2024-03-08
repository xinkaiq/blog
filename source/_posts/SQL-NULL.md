---
title: SQL NULL
date: 2024-02-18 21:10:12
tags: [SQL, NULL]
---

## NULL in SQL
`NULL` in SQL refers "missing, unknown value"

## Comparison with NULL
Comparison between a normal value with a `NULL` returns `NULL`. It is neither `TRUE` nor `FALSE`.
However, only rows `WHERE TRUE` would be `SELECT`-ed. Therefore, if you got <a href="https://leetcode.com/problems/find-customer-referee/description/">this</a>:
```
Table: Customer

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.
 

Find the names of the customer that are not referred by the customer with id = 2.

Return the result table in any order.

The result format is in the following example.

 

Example 1:

Input: 
Customer table:
+----+------+------------+
| id | name | referee_id |
+----+------+------------+
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |
+----+------+------------+
Output: 
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+
```
and you write your SQL Statement like this:
```
SELECT name
FROM Customer
WHERE referee_id != 2;
```
you will only get
```
| name |
| ---- |
| Zack |
```
since only Zack's would have `WHERE TRUE`, leaving others `WHERE FALSE` or `WHERE NULL`.

The correct Statement is this:
```
SELECT name
FROM Customer
WHERE referee_id != 2 OR referee_id IS NULL;
```
