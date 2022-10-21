### 如何生成`core.config`中需要的簽名信息

!>由於這裡需要使用到`js_ticket`,屬於安全信息,請務必在服務器端計算通過接口返回給頁面
歡迎提供其他平台計算`sign`的計算代碼

---

**php 代碼示例**

```php
//! 使用此規則生成core.config中需要的信息
$jsTicket = "a4dcdk";  //此值從redis中獲取定時獲取的應用對應的js_ticket;
$noncestr = "1234";  //此為隨機生成的字符串,最長為128個字符串;
$timestamp = time(); //1654850924,此為當前的時間unix戳,僅到秒為10位正整數.
$url = "https://yuanzhibang.com/a/b"; //此為當前頁面的url,為去除掉錨點和參數的部分,如果最後為/結尾則去掉
$signString = "js_ticket=" . $jsTicket . "&nonce_str=" . $noncestr  . "&timestamp=" . $timestamp . "&url=" . $url;
// 按照以上的值,生成的$signString="js_ticket=a4dcdk&nonce_str=1234&timestamp=1654850924&url=https://yuanzhibang.com/a/b";
// 計算sha1,此時計算sha1的值為a8cb02e00c2759372954bf5516d110066b911aa4
$sign = sha1($signString );
// $sign務必為全部小寫
```

---

**node 代碼示例**

```javascript

```

---

**java 代碼示例**

```java

```

---

**python 代碼示例**

```python

```

---

**php 代碼示例**

```php

```

---
