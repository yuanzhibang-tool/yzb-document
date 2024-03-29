> 业务相关接口

---

### `business.isChinaIp`

!>本接口自容器`1.3.2`版本之后提供

**主要描述**

| 主键          | 值                       |
| ------------- | ------------------------ |
| **接口描述:** | 判断是否是国内`ip`的接口 |
| **备注**      | 无                       |

**参数验证说明**

| 参数 | 说明 | 默认值 | 验证规则 |
| ---- | ---- | ------ | -------- |
| `无` | 无   | 无     | 无       |

**方法参数示例**

```json
{}
```

**方法回调`next`参数示例**

!>无论返回多个还是一个,都会按照该格式返回,没有则没有该值

```json
{
  "is_china_ip": true|false
}
```

---

### `business.isMobileBound`

!>本接口自容器`1.3.2`版本之后提供

**主要描述**

| 主键          | 值                           |
| ------------- | ---------------------------- |
| **接口描述:** | 判断用户是否绑定手机号的接口 |
| **备注**      | 用以进行中国境内实名验证     |

**参数验证说明**

| 参数 | 说明 | 默认值 | 验证规则 |
| ---- | ---- | ------ | -------- |
| `无` | 无   | 无     | 无       |

**方法参数示例**

```json
{}
```

**方法回调`next`参数示例**

!>无论返回多个还是一个,都会按照该格式返回,没有则没有该值

```json
{
  "is_mobile_bound": true|false
}
```

---

### `business.showAccountSetting`

!>本接口自容器`1.3.2`版本之后提供

**主要描述**

| 主键          | 值                                          |
| ------------- | ------------------------------------------- |
| **接口描述:** | 判断用户未绑定手机号,进入绑定手机号设置页面 |
| **备注**      | 用以进行中国境内实名验证                    |

**参数验证说明**

| 参数         | 说明                                  | 默认值 | 验证规则 |
| ------------ | ------------------------------------- | ------ | -------- |
| `app_action` | 无,打开手机绑定时为`show_mobile_bind` | 无     | 无       |

**方法参数示例**

```json
{
  "app_action": "show_mobile_bind"
}
```

**方法回调`next`参数示例**

!>无论返回多个还是一个,都会按照该格式返回,没有则没有该值

```json
{}
```

---

### `business.showAppUpdator`

!>本接口自容器`1.3.2`版本之后提供

**主要描述**

| 主键          | 值                                                     |
| ------------- | ------------------------------------------------------ |
| **接口描述:** | 如果`js`该版本接口不支持,提示用户升级,弹出应用升级页面 |
| **备注**      | 用以进行应用升级                                       |

**参数验证说明**

| 参数 | 说明 | 默认值 | 验证规则 |
| ---- | ---- | ------ | -------- |
| `无` | 无   | 无     | 无       |

**方法参数示例**

```json
{}
```

**方法回调`next`参数示例**

!>无论返回多个还是一个,都会按照该格式返回,没有则没有该值

```json
{
  "is_mobile_bound": true|false
}
```
