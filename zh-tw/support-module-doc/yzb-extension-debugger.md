# @yuanzhibang/extension-debugger <!-- {docsify-ignore} -->

用來進行猿之棒開放平台拓展的調試工具,模擬 renderer 進程和 node 進行進行通信以及回調
**倉庫地址:**
https://github.com/yuanzhibang-tool/yzb-extension-debugger.git
**issue**
https://github.com/yuanzhibang-tool/yzb-extension-debugger/issues
**npm**
https://www.npmjs.com/package/@yuanzhibang/extension-debugger

## 安裝

`npm i @yuanzhibang/extension-debugger --save-dev`
或者
`yarn add @yuanzhibang/extension-debugger --dev`

---

## 使用

!>下方提供的兩個演示已經配置好調試配置,`jest`單元測試,如果有問題可以在交流群,或者`issue`中提問

`typescript`使用演示 https://github.com/yuanzhibang-tool/yzb-extension-demo-ts/blob/main/debug/debug.ts
`javascript`使用演示 https://github.com/yuanzhibang-tool/yzb-extension-demo-js/blob/main/debug/debug.js

```javascript
// 引入依賴
import {
  extensionDebugger,
  DebuggerLogger,
} from '@yuanzhibang/extension-debugger';

// 開啟日誌，設置false為關閉,默認為true

DebuggerLogger.withLog = true;

// 啟動調試網絡服務，端口號為8080

extensionDebugger.startServer(8080);

// !啟動開發的拓展,調試狀態下支持ts,js文件

extensionDebugger.runExtension('./src/index.ts');

// 手動模擬向拓展進程發送topic消息

extensionDebugger
  .sendPromise('test-node-process-messsage-topic', { k1: 'v1' })
  .then((result) => {
    // 拓展進程發來的結果回調
    console.log(result);
  })
  .catch((error) => {
    // 拓展進程發來的錯誤回調
    console.log(error);
  })
  .finally(() => {
    console.log('finally');
  });

// 設置渲染端的topic消息回調

extensionDebugger.setRendererTopicMessageCallback((topic, message) => {
  console.log(topic);
  console.log(message);
});

// 設置渲染段非topic消息回調

extensionDebugger.setRendererOtherMessageCallback((message) => {
  console.log(message);
});
```

## 查看調試消息輸出

> 調試信息以及發送的消息信息可以在調試控制台查看

![](images/2E4AE63D-5B39-4ccc-839A-3B32100FA966.png)

## 快速模擬渲染進程發送 topic 消息

點擊輸出日誌中的`simple_debug_tool_url`或者點擊 vscode 的提示,來打開快速調試工具
![](images/449D0F12-B963-4b2b-A602-5F8D56A57861.png)
![](images/2E4AE63D-5B39-4ccc-839A-3B32100FA966.png)

## 快速調試工具

> 回調內容可以在調試控制台查看

![](images/F479A123-DAF3-48e0-8A23-D1A5ECB26D3F.png)
