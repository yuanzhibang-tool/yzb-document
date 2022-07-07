# @yuanzhibang/extension-debugger

用来进行猿之棒开放平台拓展的调试工具,模拟 renderer 进程和 node 进行进行通信以及回调
**仓库地址:**
https://github.com/yuanzhibang-tool/yzb-extension-debugger.git
**issue**
https://github.com/yuanzhibang-tool/yzb-extension-debugger/issues
**npm**
https://www.npmjs.com/package/@yuanzhibang/extension-debugger

## 安装

`npm i @yuanzhibang/extension-debugger --save-dev`
或者
`yarn add @yuanzhibang/extension-debugger --dev`

---

## 使用

!>下方提供的两个演示已经配置好调试配置,`jest`单元测试,如果有问题可以在交流群,或者`issue`中提问

`typescript`使用演示 https://github.com/yuanzhibang-tool/yzb-extension-demo-ts/blob/main/debug/debug.ts
`javascript`使用演示 https://github.com/yuanzhibang-tool/yzb-extension-demo-js/blob/main/debug/debug.js

```typescript
// 引入依赖
import {
  extensionDebugger,
  DebuggerLogger,
} from '@yuanzhibang/extension-debugger';

// 开启日志，设置false为关闭,默认为true

DebuggerLogger.withLog = true;

// 启动调试网络服务，端口号为8080

extensionDebugger.startServer(8080);

// !启动开发的拓展,调试状态下支持ts,js文件

extensionDebugger.runExtension('./src/index.ts');

// 手动模拟向拓展进程发送topic消息

extensionDebugger
  .sendPromise('test-node-process-messsage-topic', { k1: 'v1' })
  .then((result) => {
    // 拓展进程发来的结果回调
    console.log(result);
  })
  .catch((error) => {
    // 拓展进程发来的错误回调
    console.log(error);
  })
  .finally(() => {
    console.log('finally');
  });

// 设置渲染端的topic消息回调

extensionDebugger.setRendererTopicMessageCallback((topic, message) => {
  console.log(topic);
  console.log(message);
});

// 设置渲染段非topic消息回调

extensionDebugger.setRendererOtherMessageCallback((message) => {
  console.log(message);
});
```

## 查看调试消息输出

> 调试信息以及发送的消息信息可以在调试控制台查看

![](images/2E4AE63D-5B39-4ccc-839A-3B32100FA966.png)

## 快速模拟渲染进程发送 topic 消息

点击输出日志中的`simple_debug_tool_url`或者点击 vscode 的提示,来打开快速调试工具
![](images/449D0F12-B963-4b2b-A602-5F8D56A57861.png)
![](images/2E4AE63D-5B39-4ccc-839A-3B32100FA966.png)

## 快速调试工具

> 回调内容可以在调试控制台查看

![](images/F479A123-DAF3-48e0-8A23-D1A5ECB26D3F.png)
