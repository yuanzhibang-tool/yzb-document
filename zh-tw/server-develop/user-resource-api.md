### 獲取應用所擁有權限信息的接口

> 具體權限信息,請參考權限介紹頁面

**接口地址**

`POST /UserResource/getAppAccess`

**參數說明**

| 參數      | 是否必須 | 說明               |
| --------- | -------- | ------------------ |
| `open_id` | 是       | 用戶的`open_id`    |
| `app_id`  | 是       | 開放平台應用的`id` |

**返回值**

成功的返回值

```json
{
  "status": "2000",
  "message": "ok",
  "data": ["user/send_app_message"]
}
```

錯誤的返回值,參見錯誤信息介紹

```json
{
  "status": "4102",
  "message": "authorization_code is invalid",
  "data": []
}
```

---

### 獲取用戶基礎信息的接口

**接口地址**

`POST /UserResource/getUserBaseInfo`

**參數說明**

| 參數      | 是否必須 | 說明               |
| --------- | -------- | ------------------ |
| `open_id` | 是       | 用戶的`open_id`    |
| `app_id`  | 是       | 開放平台應用的`id` |

**返回值**

成功的返回值

```json
{
  "status": "2000",
  "message": "ok",
  "data": {
    "nick": "天使",
    "avatar": "https://upload.yuanzhibang.com/file/2019-07-21/0B4C96B3-DD62-47F9-B9BF-080CAF090DBA.jpeg",
    "sex": "1" //1男,2女,3未知
  }
}
```

錯誤的返回值,參見錯誤信息介紹

```json
{
  "status": "4102",
  "message": "authorization_code is invalid",
  "data": []
}
```
