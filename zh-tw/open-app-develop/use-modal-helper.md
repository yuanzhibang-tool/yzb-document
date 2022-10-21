> 用戶通過 app.openModal 打開新的 modal 窗口,該窗口從中無法使用`bridge yzb`注入的對象,但是注入了一個名為`modalHelper`的全局對象.

---

**該對像有如下幾個方法:**

### `modalHelper.getInitData`

**主要描述**

| 主鍵          | 值                                          |
| ------------- | ------------------------------------------- |
| **接口描述:** | 獲取通過`app.openModal`中傳入的`initData`值 |
| **備註**      | 為同步接口直接賦值即可                      |

_示例_

```javascript
var passInitData = modalHelper.getInitData();
```

---

### `modalHelper.cancel`

**主要描述**

| 主鍵          | 值                                                                               |
| ------------- | -------------------------------------------------------------------------------- |
| **接口描述:** | 關閉該 modal 窗口並返回空內容                                                    |
| **備註**      | 在`app.openModal`中傳入的`next`接收回調,如果 modal 窗口失焦後關閉也會觸發該方法. |

_示例_

```javascript
// 在應用窗口中
yzb.app.showModal({
  data: {
    url: 'https://www.baidu.com/', //modal視圖要打開的url
    width: 500, //打開窗口的寬
    height: 400, //打開窗口的高
    init_data: {
      //給modal窗口傳入的內容,具體如何使用參考
      k1: 'v1',
      k2: 'v2',
    },
  },
  next: (result) => {
    console.log(result);
    //調用modalHelper.cancel(),result為空,調用modalHelper.confirm(confirmData),result為傳入的confirmData
  },
  error: () => {},
  complete: () => {},
});

// 在modal窗口中
modalHelper.cancel();
```

---

### `modalHelper.confirm`

**主要描述**

| 主鍵          | 值                                              |
| ------------- | ----------------------------------------------- |
| **接口描述:** | 關閉該 modal 窗口並返回需要回調給調用窗口的內容 |
| **備註**      | 在`app.openModal`中傳入的`next`接收回調參數     |

_示例_

```javascript
// 在應用窗口中
yzb.app.showModal({
  data: {
    url: 'https://www.baidu.com/', //modal視圖要打開的url
    width: 500, //打開窗口的寬
    height: 400, //打開窗口的高
    init_data: {
      //給modal窗口傳入的內容,具體如何使用參考
      k1: 'v1',
      k2: 'v2',
    },
  },
  next: (result) => {
    console.log(result);
    //調用modalHelper.cancel(),result為空,調用modalHelper.confirm(confirmData),result為傳入的confirmData
  },
  error: () => {},
  complete: () => {},
});

// 在modal窗口中
var comfirmData = {
  ck1: 'cv1',
  ck2: 'cv2',
};
modalHelper.comfirm(comfirmData);
```
