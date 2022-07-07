**参数说明**

| 状态码   | 英文描述                              | 英文建议                                    | 中文描述                                   | 中文建议                            |
| -------- | ------------------------------------- | ------------------------------------------- | ------------------------------------------ | ----------------------------------- |
| `100000` | unknown error                         | please read document                        | 出现未知错误                               | 请阅读文档                          |
| `100001` | illegal parameters                    | please check the paramaters                 | 参数非法                                   | 具体会返回参数错误的描述,请注意查看 |
| `100002` | core.config paramaters check fail     | please check core.config paramaters         | `core.config`参数验证失败                  | 请检查 core.config 参数             |
| `100003` | the js api must config by core.config | please use core.config to config the js api | 调用的方法需要`core.config`验证,但是未验证 | 请使用 core.config 验证该函数       |
| `100004` | user did not give access              | please retry to request the access          | 用户未授权                                 | 提示用户进行授权                    |
| `200000` | network error                         | please check the network                    | 网络错误                                   | 请检查网络状态                      |
| `200010` | user not use wifi                     | please tell user to connect wifi            | 未连接到`wifi`                             | 提醒用户连接`wifi`                  |
| `200011` | the api response status not 200       | please check the api                        | 接口返回状态码错误非`200`                  | 提醒开发者检查接口                  |
| `200012` | the api not return json format data   | please check the api response data          | 返回数据非`json`格式                       | 提醒开发者检查接口                  |
| `200013` | request timeout                       | please check the api and network            | 接口访问超时                               | 提醒开发者检查接口和我网络          |
| `300011` | the cache value must less than 1M     | please reduce the value                     | 单次存储的缓存大于`1M`                     | 请减少单次缓存存储大小              |
| `300012` | total cache must less than 50M        | plase remove or empty the cache             | 总存储的缓存大于`50M`                      | 请清空缓存或者清除其他缓存          |

---

**状态码出现情况规整**

| 状态码   | 出现的情况                                                                                              |
| -------- | ------------------------------------------------------------------------------------------------------- |
| `100000` | 调用`bridge`总入口出现 `crash`                                                                          |
| `100000` | 用户定位出现无法确定的问题时出现!                                                                       |
| `100001` | 参数验证器格式验证失败弹出!                                                                             |
| `100001` | 调用方法过程中 `tid` 对比失败时候会弹出!                                                                |
| `100001` | 调用方法过程中 `app_id` 对比失败时候会弹出!                                                             |
| `100002` | 调用 `core.config` 参数原生网络请求,接口返回非 2000,但是接口成功时!                                     |
| `100003` | 调用的方法需要 `core.config` 验证,但是未验证!                                                           |
| `100004` | 用户未授权,获取`地理位置`,获取 `wifi` 信息,用户拒绝或者没有权限授权的时候会出现!                        |
| `200000` | `core.config` 调用接口出现任何网络错误,超时和连接不上服务器(飞行模式,非 `200` 错误)                     |
| `200000` | `core.requestAuthCode` 调用接口出现网络错,超时和连接不上服务器(飞行模式,非 `200` 错误)                  |
| `200000` | `network.request get` 服务器无法连接,或者飞行模式,没有任何输出的 response! 注意此处不带非 `200` 错误    |
| `200000` | `network.request post` 服务器无法连接,或者飞行模式,没有任何输出的 `response`! 注意此处不带非 `200` 错误 |
| `200010` | 当获取 `wifi` 信息,用户没有连接 `wifi` 的时候会调用此错误!                                              |
| `200011` | 使用 `network.request get` 当接口返回状态码错误非 `200`,则回调该错误!                                   |
| `200011` | 使用 `network.request post` 当接口返回状态码错误非 `200`,则回调该错误!                                  |
| `200012` | 使用 `network.request get` 当获取的结果非 `json` 的时候回调用该错误,注意先判断 `200011` 错误!           |
| `200012` | 使用 `network.request post` 当获取的结果非 `json` 的时候回调用该错误,注意先判断 200011 错误!            |
| `200013` | 使用 `network.request get`,当接口访问超过给定的时间的时候返回该错误代码                                 |
| `200013` | 使用 `network.request post`,当接口访问超过给定的时间的时候返回该错误代码                                |
| `300011` | 缓存,单次存储大于 `1m`                                                                                  |
| `300012` | 缓存,单个应用单个团队存储大于 `50m`                                                                     |
