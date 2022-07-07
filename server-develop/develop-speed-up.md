> 快速实现对应业务

### 实现授权`token`的获取和自动更新

1.使用`docker-compose`部署,该方式可以自动实现数据缓存到 redis,自动启动代理服务器等功能.
**具体`compose`方式部署,请参照:**
https://github.com/yuanzhibang-tool/docker/tree/main/oapp-code-docker-compose

> 该`compose`实现了代理,redis 存储以及定时更新`token`和`ticket`的工作,并会定时清理日志,保持日志不会占用过多空间

_注意:请配置好您这边需要的开放平台应用信息以及在开放平台该应用下添加 ip 白名单,否则会返回错误,已挂载日志到`logs`目录下,如有问题请查看目录,开发者如果需要自己组合业务请参考该`compose`文件自己调整._

---

### 支持的 docker 镜像,请参照

https://hub.docker.com/u/yuanzhibang

---

Docker 镜像构建以及 token 更新任务为开源项目,请参照:
https://github.com/yuanzhibang-tool/docker.git
https://github.com/yuanzhibang-tool/oapp-token-cron-task.git

!>请注意阅读项目以及目录下的 README.md 以更快实现功能开发

---

### 业务接口的快速开发

**node 接口开发**
我们对接口的调用进行了封装,`node`开发我们封装了`node`的`npm`库
https://www.npmjs.com/package/@yuanzhibang/oauth-server
具体使用说明,请参照开源项目,和代码备注.
https://github.com/yuanzhibang-tool/oauth-server.git

---

**java,php,python 接口开发**
我们提供了 demo,对接口进行了一定的封装,请参考使用.
https://github.com/yuanzhibang-tool/demo

---

**_demo 或者 npm 包已完成的工作:_**

1.js 签名生成

2.所有接口的封装调用

3.接口调用支持设置代理,具体使用请参照 单元测试代码

4.支持从 redis 获取取`server_access_token`或者`js_ticket`

!>欢迎猿猿们提供其他语言的 demo 代码,请按照其他语言的封装进行封装,并提供单元测试.提供的代码将遵循 MIT 协议.
