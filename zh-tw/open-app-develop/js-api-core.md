## core 命名空間方法調用文檔 <!-- {docsify-ignore} -->

> core 命名空間方法調用相關文檔

### `core.requestAuthCode`

**主要描述**

| 主鍵          | 值                                                |
| ------------- | ------------------------------------------------- |
| **接口描述:** | 獲取免登陸`code`的 js 方法                        |
| **備註**      | 通過調用開放平台的`/OAuth2/requestJsAuthCode`方法 |

**參數驗證說明**

| 參數     | 說明     | 默認值 | 驗證規則                  |
| -------- | -------- | ------ | ------------------------- |
| `app_id` | 應用`id` | 無     | 參考參數驗證說明`require` |
| `tid`    | 團隊`id` | 無     | 參考參數驗證說明`require` |

**方法參數示例**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "data": {
       "app_id":"100011", //開放平台的app_id
       "tid":"100027" //如果為團隊應用,需要傳遞該參數,該參數如果是由app進入,會在參數中附加上團隊
     }
}

```

**方法回調`next`參數示例**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "result": {
        "code":"34TGERVG45GSDFBGERTYE45YGDFBFS"
    }
}

```

!>**注意:**

> 該方法只有`next`回調,沒錯誤回調

---

### `core.requestAccess`

**主要描述**

| 主鍵          | 值                         |
| ------------- | -------------------------- |
| **接口描述:** | 請求用戶授予應用權限的接口 |
| **備註**      | 打開設置應用權限頁面的接口 |

**參數驗證說明**

| 參數     | 說明     | 默認值     | 驗證規則                                                    |
| -------- | -------- | ---------- | ----------------------------------------------------------- |
| `app_id` | 應用`id` | 無         | 參考參數驗證說明`require`                                   |
| `access` | 權限列表 | `[]`空數組 | `array`,添加每條權限的驗證正則`^[1-9a-zA-Z_-[*]\/]{1,128}$` |

**方法參數示例**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "data": {
       "app_id":"100011" //開放平台的app_id,
       "tid": "100043", //如果是team app必須傳遞此參數
       "access": ["team/send_team_message", "team/send_app_message", "team/get_team_member_base_info"]
     }
}

```

**方法回調`next`參數示例**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "result": {}
}

```

!>**注意:**

> 該方法只有`next`回調,沒錯誤回調

---

### `core.config`

!>該接口需要的參數,請務必使用服務器端生成,不要在網頁端生成.具體生成規則參照

**主要描述**

| 主鍵          | 值                                          |
| ------------- | ------------------------------------------- |
| **接口描述:** | 注入頁面配置信息,開啟`debug`以及驗證`jsApi` |
| **備註**      | 無                                          |

**參數驗證說明**
| 參數 | 說明 | 默認值 | 驗證規則 |
| ------------- | ------------------------------------------------------------------------------------ | ------- | ---------------------------------------------------------------------- |
| `app_id` | 應用`id` | 無 | 參考參數驗證說明`require` |
| `timestamp` | 時間戳 | 無 | `require;int;length:10,11` |
| `nonce_str` | 隨機字符串 | 無 | `require;length:4,128` |
| `signature` | 簽名值 | 無 | `require;length:4,128`,正則`^[a-zA-Z0-9_-]{4,128}$` |
| `debug` | 本參數,當前無需處理,不必獲取,是否開啟`debug`模式,開啟後返回結果和錯誤將會彈出`alert` | `false` | `bool` |
| `js_api_list` | 需要驗證的`js_api_list` | 無 | `require;array;array*min_length:1`,正則`^[1-9a-zA-Z*-[\*][.]]{1,128}$` |
| `is_spa` | `是否是單頁面應用` | `false` | `bool` |

**方法參數示例**

```
{
	"data": {
		"app_id": "101000", //開放平台的`app_id`,
                "tid": "100027", //團隊的`tid`
		"timestamp": 1544579311, //注意為數字類型,生成簽名的時間戳,為`unix timestamp`,只精確到秒
		"nonce_str": "fasdfwHlhHLJ", //隨機字符串
		"signature": "ba0dc6903b0f5ce48a1519604256aec7306ffb5a", //簽名值
		"debug": true, //本參數,當前無需處理,不必獲取,是否開啟`debug`模式,開啟後返回結果和錯誤將會彈出`alert`,默認是`false`
		"js_api_list": ["tool.cache.set", "tool.cache.get"] //需要驗證的js_api_list
	},
	"identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c"
}

```

**返回值示例**

_成功後回調的`next`_

```
{
    "identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//注意此處無任何參數
    }
}

```

_以及錯誤回調_

`網絡錯誤回調`(當原生調用出現接口網絡錯誤時,非`200`錯誤,是網絡級別的錯誤)

```

{
    "identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//注意此處無任何參數
        "code": "100002",
		"description": "網絡錯誤",
        "suggestion": "請檢查網絡狀態"
    }
}


```

`網絡調用出錯回調`(當原生調用出現接口出現返回接口數據錯誤時,`status`非`2000`錯誤,是返回結果錯誤層級)

```

{
    "identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//注意此處無任何參數
        "code": "100003",
		"description": "core.config參數驗證失敗",
        "suggestion": "請檢查core.config參數"
    }
}


```

`當調用需要驗證的,但是沒有經過驗證的方法的時候`調用的錯誤,是在調用該驗證的方法的時候使用的,**不是在該方法中使用的**

```
{
    "identity": "cache_set_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//注意此處無任何參數
        "code": "100004",
		"description": "該javascrip函數未使用core.config配置",
        "suggestion": "請使用該core.config函數進行配置"
    }
}
```
