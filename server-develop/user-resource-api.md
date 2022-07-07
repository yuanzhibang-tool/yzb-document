## **用户资源相关接口说明**

### **获取应用所拥有权限信息的接口**

> 具体权限信息,请参考权限介绍页面

**接口地址**

`POST /UserResource/getAppAccess`
**参数说明**
| 参数 | 是否必须 | 说明|
| --- | --- |---|
| `open_id` | 是 |用户的`open_id`|
| `app_id` | 是 |开放平台应用的`id`|

**返回值**
成功的返回值

```json
{
  "status": 2000,
  "message": "ok",
  "data": ["user/send_app_message"]
}
```

错误的返回值,参见错误信息介绍

```json
{
  "status": 4102,
  "message": "authorization_code is invalid",
  "data": []
}
```

---

### **获取用户基础信息的接口**

**接口地址**

`POST /UserResource/getUserBaseInfo`
**参数说明**
| 参数 | 是否必须 | 说明|
| --- | --- |---|
| `open_id` | 是 |用户的`open_id`|
| `app_id` | 是 |开放平台应用的`id`|

**返回值**
成功的返回值

```json
{
  "status": 2000,
  "message": "ok",
  "data": {
    "nick": "天使",
    "avatar": "https://avatar.dd.david-health.cn/file/2019-07-21/0B4C96B3-DD62-47F9-B9BF-080CAF090DBA.jpeg",
    "sex": "1"
  }
}
```

错误的返回值,参见错误信息介绍

```json
{
  "status": 4102,
  "message": "authorization_code is invalid",
  "data": []
}
```
