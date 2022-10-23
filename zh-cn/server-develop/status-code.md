#### 返回状态码说明

> 由于状态码的重要作用是指引程序自动进行分析处理,是进行重试还是停止重试,所以我们将错误分为两类错误,一类是即使重试也会出现同样错误的状态码,一类是需要进行特殊处理

| 错误码 | 说明                |
| ------ | ------------------- |
| `2000` | 成功                |
| `2011` | 成功,但是没有数据   |
| `4000` | 通用错误            |
| `4102` | 传入的`code`无效    |
| `4103` | 没有权限            |
| `4104` | 用户没有添加该`app` |