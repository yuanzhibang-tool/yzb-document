# @yuanzhibang/node <!-- {docsify-ignore} -->

用来进行猿之棒开放平台拓展的调试工具,模拟 renderer 进程和 node 进行进行通信以及回调

**仓库地址:**

https://github.com/yuanzhibang-tool/yzb-node.git

**issue**

https://github.com/yuanzhibang-tool/yzb-node/issues

**npm**

https://www.npmjs.com/package/@yuanzhibang/node

## 安装

`npm i @yuanzhibang/node --save-dev`
或者
`yarn add @yuanzhibang/node --dev`

## 使用

!>`@yuanzhibang/node`该模块仅适用在拓展进程里,该拓展在初始化后,将自动接收`process.on('message')`的消息回调,请勿在拓展进程的其他部位使用`process.on('message')`来配置消息回调,否则可能会造成模块工作异常.
