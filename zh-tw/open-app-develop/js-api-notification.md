> 通知相關命名空間方法調用相關文檔

### `notification.vibrate`

**主要描述**

| 主鍵          | 值                        |
| ------------- | ------------------------- |
| **接口描述:** | 調用震動的方法            |
| **備註**      | 調用該接口,整個窗口會抖動 |

**參數驗證說明**

| 參數 | 說明 | 默認值 | 驗證規則 |
| ---- | ---- | ------ | -------- |
| 無   | 無   | 無     | 無       |

**方法參數示例**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "data": {}
}

```

**方法回調`next`參數示例(只有`next`回調,沒錯誤回調)**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "result": {}
}
```

!>**注意:**

> 無錯誤回調

---

### `notification.showToast`

**主要描述**

| 主鍵          | 值                      |
| ------------- | ----------------------- |
| **接口描述:** | 顯示 toast 輕提示的方法 |
| **備註**      | 會在應用端上部提示信息  |

**參數驗證說明**

| 參數 | 說明 | 默認值 | 驗證規則 |
| ---- | ---- | ------ | -------- |
| 無   | 無   | 無     | 無       |

**方法參數示例**

```
{
    type: "info", //消息類型,info|warning|success|error
    content: "這個是提示內容!"
}

```

**方法回調`next`參數示例(只有`next`回調,沒錯誤回調)**

!>注意:無錯誤回調