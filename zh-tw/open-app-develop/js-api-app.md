---

### `app.close`

**主要描述**

| 主鍵 | 值 |
| ------------- | ------------------- |
| **接口描述:** | 關閉當前應用的`js`方法 |  
| **備註** | 無 |

**參數驗證說明**

| 參數 | 說明| 默認值 | 驗證規則 |
| --- | --- | --- | --- |
| `無` | 無 | 無 |無 |

**方法參數示例**

```json
{}
```

**方法回調`next`參數示例**

```json
{}
```

---

### `app.showModal`

**主要描述**

| 主鍵          | 值                                   |
| ------------- | ------------------------------------ |
| **接口描述:** | 使用 modal 顯示新 url 內容的`js`方法 |
| **備註**      | 無                                   |

**參數驗證說明**

| 參數        | 說明                                     | 默認值 | 驗證規則             |
| ----------- | ---------------------------------------- | ------ | -------------------- |
| `url`       | modal 視圖要打開的 url                   | 無     | 無                   |
| `width`     | 打開窗口的寬,過小過大均會被自動調整      | 無     | 無                   |
| `height`    | 打開窗口的高,過小過大均會被自動調整      | 無     | 無                   |
| `init_data` | 給 modal 窗口傳入的內容,具體如何使用參考 | 空     | 請使用對象來傳遞內容 |

**方法參數示例**

```json
{
  "url": "https://www.baidu.com/", //modal視圖要打開的url
  "width": 500, //打開窗口的寬
  "height": 400, //打開窗口的高
  "init_data": {
    //給modal窗口傳入的內容,具體如何使用參考
    "k1": "v1",
    "k2": "v2"
  }
}
```

**方法回調`next`參數示例**

```json
{}
```

---

### `app.setUrlOpenAction`

**主要描述**

| 主鍵          | 值                                                                     |
| ------------- | ---------------------------------------------------------------------- |
| **接口描述:** | 設置通過 url 打開應用的回調接口，該接口將完整的 url 回調給設置的該函數 |
| **備註**      | 無                                                                     |

**參數說明**

傳入一個參數為 url 的函數

```javascript
// url 示例: yzb://yuanzhibang.com?action=open_app&app_action=app_detail&app_id=101170
yzb.app.setUrlOpenAction((url) => {
  console.log(`open app by url: ${url}`);
});
```

---

### `app.setVersion`

**主要描述**

| 主鍵          | 值                                          |
| ------------- | ------------------------------------------- |
| **接口描述:** | 設置當前的應用版本號,在應用反饋會帶上該信息 |
| **備註**      | 無                                          |

**參數說明**

傳入一個版本號參數,建議為`1.0.1`格式的

```javascript
yzb.app.setVersion('1.0.1');
```