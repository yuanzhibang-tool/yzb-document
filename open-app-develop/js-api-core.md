## core 命名空间方法调用文档 <!-- {docsify-ignore} -->

> core 命名空间方法调用相关文档

### `core.requestAuthCode`

**主要描述**

| 主键          | 值                                                |
| ------------- | ------------------------------------------------- |
| **接口描述:** | 获取免登陆`code`的 js 方法                        |
| **备注**      | 通过调用开放平台的`/OAuth2/requestJsAuthCode`方法 |

**参数验证说明**

| 参数     | 说明     | 默认值 | 验证规则                  |
| -------- | -------- | ------ | ------------------------- |
| `app_id` | 应用`id` | 无     | 参考参数验证说明`require` |
| `tid`    | 团队`id` | 无     | 参考参数验证说明`require` |

**方法参数示例**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "data": {
       "app_id":"100011", //开放平台的app_id
       "tid":"100027" //如果为团队应用,需要传递该参数,该参数如果是由app进入,会在参数中附加上团队
     }
}

```

**方法回调`next`参数示例**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "result": {
        "code":"34TGERVG45GSDFBGERTYE45YGDFBFS"
    }
}

```

!>**注意:**

> 该方法只有`next`回调,没错误回调

---

### `core.requestAccess`

**主要描述**

| 主键          | 值                         |
| ------------- | -------------------------- |
| **接口描述:** | 请求用户授予应用权限的接口 |
| **备注**      | 打开设置应用权限页面的接口 |

**参数验证说明**

| 参数     | 说明     | 默认值     | 验证规则                                                    |
| -------- | -------- | ---------- | ----------------------------------------------------------- |
| `app_id` | 应用`id` | 无         | 参考参数验证说明`require`                                   |
| `access` | 权限列表 | `[]`空数组 | `array`,添加每条权限的验证正则`^[1-9a-zA-Z_-[*]\/]{1,128}$` |

**方法参数示例**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "data": {
       "app_id":"100011" //开放平台的app_id,
       "tid": "100043", //如果是team app必须传递此参数
       "access": ["team/send_team_message", "team/send_app_message", "team/get_team_member_base_info"]
     }
}

```

**方法回调`next`参数示例**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "result": {}
}

```

!>**注意:**

> 该方法只有`next`回调,没错误回调

---

### `core.config`

!>该接口需要的参数,请务必使用服务器端生成,不要在网页端生成.具体生成规则参照

**主要描述**

| 主键          | 值                                          |
| ------------- | ------------------------------------------- |
| **接口描述:** | 注入页面配置信息,开启`debug`以及验证`jsApi` |
| **备注**      | 无                                          |

**参数验证说明**

| 参数          | 说明                                                                                 | 默认值  | 验证规则                                                               |
| ------------- | ------------------------------------------------------------------------------------ | ------- | ---------------------------------------------------------------------- |
| `app_id`      | 应用`id`                                                                             | 无      | 参考参数验证说明`require`                                              |
| `timestamp`   | 时间戳                                                                               | 无      | `require;int;length:10,11`                                             |
| `nonce_str`   | 随机字符串                                                                           | 无      | `require;length:4,128`                                                 |
| `signature`   | 签名值                                                                               | 无      | `require;length:4,128`,正则`^[a-zA-Z0-9_-]{4,128}$`                    |
| `debug`       | 本参数,当前无需处理,不必获取,是否开启`debug`模式,开启后返回结果和错误将会弹出`alert` | `false` | `bool`                                                                 |
| `js_api_list` | 需要验证的`js_api_list`                                                              | 无      | `require;array;array*min_length:1`,正则`^[1-9a-zA-Z*-[\*][.]]{1,128}$` |
| `is_spa`      | `是否是单页面应用`                                                                   | `false` | `bool`                                                                 |

**方法参数示例**

```
{
	"data": {
		"app_id": "101000", //开放平台的`app_id`,
                "tid": "100027", //团队的`tid`
		"timestamp": 1544579311, //注意为数字类型,生成签名的时间戳,为`unix timestamp`,只精确到秒
		"nonce_str": "fasdfwHlhHLJ", //随机字符串
		"signature": "ba0dc6903b0f5ce48a1519604256aec7306ffb5a", //签名值
		"debug": true, //本参数,当前无需处理,不必获取,是否开启`debug`模式,开启后返回结果和错误将会弹出`alert`,默认是`false`
		"js_api_list": ["tool.cache.set", "tool.cache.get"] //需要验证的js_api_list
	},
	"identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c"
}

```

**返回值示例**

_成功后回调的`next`_

```
{
    "identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//注意此处无任何参数
    }
}

```

_以及错误回调_

`网络错误回调`(当原生调用出现接口网络错误时,非`200`错误,是网络级别的错误)

```

{
    "identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//注意此处无任何参数
        "code": "100002",
		"description": "网络错误",
        "suggestion": "请检查网络状态"
    }
}


```

`网络调用出错回调`(当原生调用出现接口出现返回接口数据错误时,`status`非`2000`错误,是返回结果错误层级)

```

{
    "identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//注意此处无任何参数
        "code": "100003",
		"description": "core.config参数验证失败",
        "suggestion": "请检查core.config参数"
    }
}


```

`当调用需要验证的,但是没有经过验证的方法的时候`调用的错误,是在调用该验证的方法的时候使用的,**不是在该方法中使用的**

```
{
    "identity": "cache_set_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//注意此处无任何参数
        "code": "100004",
		"description": "该javascrip函数未使用core.config配置",
        "suggestion": "请使用该core.config函数进行配置"
    }
}
```
