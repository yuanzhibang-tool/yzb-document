### 如何生成`core.config`中需要的签名信息
>[danger]由于这里需要使用到`js_ticket`,属于安全信息,请务必在服务器端计算通过接口返回给页面
欢迎提供其他平台计算`sign`的计算代码
---
**php代码示例**
```php
//! 使用此规则生成core.config中需要的信息
$jsTicket = "a4dcdk";  //此值从redis中获取定时获取的应用对应的js_ticket;
$noncestr = "1234";  //此为随机生成的字符串,最长为128个字符串;
$timestamp = time(); //1654850924,此为当前的时间unix戳,仅到秒为10位正整数.
$url = "https://yuanzhibang.com/a/b"; //此为当前页面的url,为去除掉锚点和参数的部分,如果最后为/结尾则去掉
$signString = "js_ticket=" . $jsTicket . "&nonce_str=" . $noncestr  . "&timestamp=" . $timestamp . "&url=" . $url;
// 按照以上的值,生成的$signString="js_ticket=a4dcdk&nonce_str=1234&timestamp=1654850924&url=https://yuanzhibang.com/a/b";
// 计算sha1,此时计算sha1的值为a8cb02e00c2759372954bf5516d110066b911aa4
$sign = sha1($signString );
// $sign务必为全部小写
```
*****
**node代码示例**
```javascript

```
****
**java代码示例**
```java

```
****
**python代码示例**
```python

```
****
**php代码示例**
```php

```
****



