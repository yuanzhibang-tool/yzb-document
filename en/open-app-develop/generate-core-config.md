### How to generate the signature information required in `core.config`

!>Because `js_ticket` needs to be used here, it belongs to security information, please be sure to return it to the page through the interface on the server side
Welcome to provide calculation code for other platforms to calculate `sign`

---

**php code example**

```php
//! Use this rule to generate the information needed in core.config
$jsTicket = "a4dcdk"; //This value obtains the js_ticket corresponding to the application obtained periodically from redis;
$noncestr = "1234"; //This is a randomly generated string, the longest is 128 strings;
$timestamp = time(); //1654850924, this is the current time unix stamp, only the second is a 10-digit positive integer.
$url = "https://yuanzhibang.com/a/b"; //This is the url of the current page, to remove the anchor and parameters, if the last is / end, remove
$signString = "js_ticket=" . $jsTicket . "&nonce_str=" . $noncestr . "&timestamp=" . $timestamp . "&url=" . $url;
// According to the above values, the generated $signString="js_ticket=a4dcdk&nonce_str=1234&timestamp=1654850924&url=https://yuanzhibang.com/a/b";
// Calculate sha1, at this time the value of sha1 is a8cb02e00c2759372954bf5516d110066b911aa4
$sign = sha1($signString );
// $sign must be all lowercase
```

---

**node code example**

```javascript

```

---

**java code example**

```java

```

---

**python code example**

```python

```

---

**php code example**

```php

```

---
