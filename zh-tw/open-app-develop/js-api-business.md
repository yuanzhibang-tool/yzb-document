> 業務相關接口

---

### `business.isChinaIp`

!>本接口自容器`1.3.2`版本之後提供

**主要描述**

| 主鍵          | 值                       |
| ------------- | ------------------------ |
| **接口描述:** | 判斷是否是國內`ip`的接口 |
| **備註**      | 無                       |

**參數驗證說明**

| 參數 | 說明 | 默認值 | 驗證規則 |
| ---- | ---- | ------ | -------- |
| `無` | 無   | 無     | 無       |

**方法參數示例**

```json
{}
```

**方法回調`next`參數示例**

!>無論返回多個還是一個,都會按照該格式返回,沒有則沒有該值

```json
{
  "is_china_ip": true|false
}
```

---

### `business.isMobileBound`

!>本接口自容器`1.3.2`版本之後提供

**主要描述**

| 主鍵          | 值                           |
| ------------- | ---------------------------- |
| **接口描述:** | 判斷用戶是否綁定手機號的接口 |
| **備註**      | 用以進行中國境內實名驗證     |

**參數驗證說明**

| 參數 | 說明 | 默認值 | 驗證規則 |
| ---- | ---- | ------ | -------- |
| `無` | 無   | 無     | 無       |

**方法參數示例**

```json
{}
```

**方法回調`next`參數示例**

!>無論返回多個還是一個,都會按照該格式返回,沒有則沒有該值

```json
{
  "is_mobile_bound": true|false
}
```

---

### `business.showAccountSetting`

!>本接口自容器`1.3.2`版本之後提供

**主要描述**

| 主鍵          | 值                                          |
| ------------- | ------------------------------------------- |
| **接口描述:** | 判斷用戶未綁定手機號,進入綁定手機號設置頁面 |
| **備註**      | 用以進行中國境內實名驗證                    |

**參數驗證說明**

| 參數         | 說明                                  | 默認值 | 驗證規則 |
| ------------ | ------------------------------------- | ------ | -------- |
| `app_action` | 無,打開手機綁定時為`show_mobile_bind` | 無     | 無       |

**方法參數示例**

```json
{
  "app_action": "show_mobile_bind"
}
```

**方法回調`next`參數示例**

!>無論返回多個還是一個,都會按照該格式返回,沒有則沒有該值

```json
{}
```

---

### `business.showAppUpdator`

!>本接口自容器`1.3.2`版本之後提供

**主要描述**

| 主鍵          | 值                                                     |
| ------------- | ------------------------------------------------------ |
| **接口描述:** | 如果`js`該版本接口不支持,提示用戶升級,彈出應用升級頁面 |
| **備註**      | 用以進行應用升級                                       |

**參數驗證說明**

| 參數 | 說明 | 默認值 | 驗證規則 |
| ---- | ---- | ------ | -------- |
| `無` | 無   | 無     | 無       |

**方法參數示例**

```json
{}
```

**方法回調`next`參數示例**

!>無論返回多個還是一個,都會按照該格式返回,沒有則沒有該值

```json
{
  "is_mobile_bound": true|false
}
```
