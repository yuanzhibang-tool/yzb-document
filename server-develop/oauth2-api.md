## **OAuth2 接口说明**

### **使用免登陆 code 获取用户 open_id 的接口**

> [danger]注意:此处获取的`access_token`在概念上和服务开发中获取的`access_token`不属于同一类`access_token`这里需要注意.服务器`access_token`主要是用来获取和操作应用相关的资源.而用户的`access_token`是用来操作用户相关资源的凭证.

**接口地址**

`POST /OAuth2/token`
**参数说明**
| 参数 | 是否必须 | 说明|
| --- | --- |---|
| `app_id` | 是 |开放平台提供更多应用 id|
|` secret` | 是 |开放平台提供的密钥|
| `grant_type` | 是 |此处恒为`authorization_code`|
|`code`|是|此处为`网页开发中的JS`获取临时授权码的值|
**返回值**
成功的返回值

```json
{
  "status": 2000,
  "message": "ok",
  "data": {
    "open_id": "bkNhRE1LN2FGb3pnWEJKS2l0MzZ0OCt3cVMwRkE0SXJTaDd6T2FNSWp0UjhhMUt1N29Db3ltcEZabXFMaGp0d0c1WDU3czk5QVkwbmlTSHVoblZ0elZoMWhXT2tFYW1FSElzaFZuU3VRSWhzM1VKd3RxL3ozSU1rUWMwaUt2TGk4OHA5c21lS3pRTmV1YTRRTEJ6L0c1N3pyU3NVYlUwM01qd203WTRVUDZBPQ",
    "access_token": "5cc928f1eadd0a25bf18e08269c2309741e94b0b51585d987d24488331ca50de",
    "expires_in": 7200,
    "refresh_token": "1503c423d5303ccab35cb26792f403fcae48eec2bedca99b2e9259683f2a31ac",
    "scope": "sns_base"
  }
}
```

> [danger]注意:此处的`access_token`和`refresh_token`暂时无用,无法用用于更新用户信息,获取用户信息请参照:用户资源接口 API/获取用户信息.

错误的返回值

```json
{
  "status": "4102",
  "message": "authorization_code is invalid",
  "data": []
}
```

### **获取`js_ticket`的接口**

> `js_ticket`用于对网页开发中在`core.config`方法中对当前页面调用的`JS`方法进行签名的值,相当于密钥

**接口地址**

`POST /OAuth2/ticket`

**参数说明**
| 参数 | 是否必须 | 说明|
| --- | --- |---|
| `app_id` | 是 |开放平台提供更多应用 id|
|` access_token` | 是 |`获取服务器access_token接口`中获取到的 access_token|
| `type` | 是 |此处恒为`js_ticket`|

**返回值**
成功的返回值

```json
{
  "status": "2000",
  "message": "ok",
  "data": {
    "ticket": "36bd5645fbadaf5e3ef4a889f0ac26ee14fa7ab0578e8e0108519a4706f2ab4c",
    "expires_in": 7200 //有效期为7200秒
  }
}
```

> [danger]注意:`ticket`请预留 128 位长度的存储空间.避免长度越界而产生错误

> 注意:获取的`js_ticket`失效前,重新获取后,之前的`js_ticket`将会将有效时间设置为`10分钟`,过期自动失效.避免`js_ticket`的更替产生调用错误.

错误的返回值

```json
{
  "status": "4102",
  "message": "server_access_token is invalid",
  "data": []
}
```

---

### **检测获取的`access_token`或者`js_ticket`是否有效的接口**

> [danger]使用最佳实践中使用阿里云函数计算或者 docker 集中获取更新`code`的无需调用该接口检验.

> `access_token`或者`js_ticket`都属于`code`类型的值,所以接口以`checkCode`命名

**接口地址**

`POST /OAuth2/checkCode`

**参数说明**
| 参数 | 是否必须 | 说明|
| --- | --- |---|
| `app_id` | 是 |开放平台提供更多应用 id|
|` type` | 是 |当检测`code`类型为`access_token`则为`access_token`,如果类型为`js_ticket`,则为`js_ticket`|
| `code` | 是 |要检测的`code`值|
| `open_id` | 否 |此处当检测的是用户的授权`access_token`时,才是必传的值|

**返回值**
成功的返回值

```json
{
  "status": "2000",
  "message": "ok",
  "data": {
    "expires_in": 1654576906
  }
}
```

错误的返回值

```json
{
  "status": "4102",
  "message": "server_access_token is invalid",
  "data": []
}
```

> [danger]无效返回的则是`status`为`4102`,其他非`2000`则为错误

---
