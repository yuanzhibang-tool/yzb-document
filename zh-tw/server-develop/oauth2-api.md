### 使用免登陸 code 獲取用戶 open_id 的接口

!>注意:此處獲取的`access_token`在概念上和服務開發中獲取的`access_token`不屬於同一類`access_token`這裡需要注意.服務器`access_token`主要是用來獲取和操作應用相關的資源.而用戶的`access_token`是用來操作用戶相關資源的憑證.

**接口地址**

`POST /OAuth2/token`

**參數說明**

| 參數         | 是否必須 | 說明                                                               |
| ------------ | -------- | ------------------------------------------------------------------ |
| `app_id`     | 是       | 開放平台提供更多應用 id                                            |
| ` secret`    | 是       | 開放平台提供的密鑰                                                 |
| `grant_type` | 是       | 此處恆為`authorization_code`                                       |
| `code`       | 是       | 此處為`網頁開發中的JS`使用`yzb.core.requestAuthCode`獲取臨時授權碼 |

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

!>注意:此處的`access_token`和`refresh_token`暫時無用,無法用用於更新用戶信息,獲取用戶信息請參照:用戶資源接口 API/獲取用戶信息.

錯誤的返回值

```json
{
  "status": "4102",
  "message": "authorization_code is invalid",
  "data": []
}
```

### 獲取 js_ticket 的接口

> `js_ticket`用於對網頁開發中在`core.config`方法中對當前頁面調用的`JS`方法進行簽名的值,相當於密鑰

**接口地址**

`POST /OAuth2/ticket`

**參數說明**

| 參數            | 是否必須 | 說明                                                |
| --------------- | -------- | --------------------------------------------------- |
| `app_id`        | 是       | 開放平台提供更多應用 id                             |
| ` access_token` | 是       | `獲取服務器access_token接口`中獲取到的 access_token |
| `type`          | 是       | 此處恆為`js_ticket`                                 |

**返回值**

成功的返回值

```json
{
  "status": "2000",
  "message": "ok",
  "data": {
    "ticket": "36bd5645fbadaf5e3ef4a889f0ac26ee14fa7ab0578e8e0108519a4706f2ab4c",
    "expires_in": 7200 //有效期為7200秒
  }
}
```

!>注意:`ticket`請預留 128 位長度的存儲空間.避免長度越界而產生錯誤

> 注意:獲取的`js_ticket`失效前,重新獲取後,之前的`js_ticket`將會將有效時間設置為`10分鐘`,過期自動失效.避免`js_ticket`的更替產生調用錯誤.

錯誤的返回值

```json
{
  "status": "4102",
  "message": "server_access_token is invalid",
  "data": []
}
```

---

### 檢測獲取的 access_token 或者 js_ticket 是否有效的接口

!>使用最佳實踐中使用阿里雲函數計算或者 docker 集中獲取更新`code`的無需調用該接口檢驗.

> `access_token`或者`js_ticket`都屬於`code`類型的值,所以接口以`checkCode`命名

**接口地址**

`POST /OAuth2/checkCode`

**參數說明**

| 參數      | 是否必須 | 說明                                                                                     |
| --------- | -------- | ---------------------------------------------------------------------------------------- |
| `app_id`  | 是       | 開放平台提供更多應用 id                                                                  |
| ` type`   | 是       | 當檢測`code`類型為`access_token`則為`access_token`,如果類型為`js_ticket`,則為`js_ticket` |
| `code`    | 是       | 要檢測的`code`值                                                                         |
| `open_id` | 否       | 此處當檢測的是用戶的授權`access_token`時,才是必傳的值                                    |

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

錯誤的返回值

```json
{
  "status": "4102",
  "message": "server_access_token is invalid",
  "data": []
}
```

!>無效返回的則是`status`為`4102`,其他非`2000`則為錯誤

---
