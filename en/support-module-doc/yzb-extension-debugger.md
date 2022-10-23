# @yuanzhibang/extension-debugger <!-- {docsify-ignore} -->

A debugging tool used to expand the Ape Stick open platform, simulate the renderer process and node to communicate and call back
**Warehouse Address:**
https://github.com/yuanzhibang-tool/yzb-extension-debugger.git
**issue**
https://github.com/yuanzhibang-tool/yzb-extension-debugger/issues
**npm**
https://www.npmjs.com/package/@yuanzhibang/extension-debugger

## Install

`npm i @yuanzhibang/extension-debugger --save-dev`
or
`yarn add @yuanzhibang/extension-debugger --dev`

---

## use

!> The two demos provided below have been configured with debug configuration, `jest` unit test, if you have any questions, you can ask questions in the exchange group or `issue`

`typescript` usage demo https://github.com/yuanzhibang-tool/yzb-extension-demo-ts/blob/main/debug/debug.ts
`javascript` usage demo https://github.com/yuanzhibang-tool/yzb-extension-demo-js/blob/main/debug/debug.js

```javascript
// import dependencies
import {
  extensionDebugger,
  DebuggerLogger,
} from '@yuanzhibang/extension-debugger';

// Turn on the log, set false to off, the default is true

DebuggerLogger.withLog = true;

// Start the debugging network service, the port number is 8080

extensionDebugger.startServer(8080);

// ! Start the development expansion, support ts, js files in the debugging state

extensionDebugger.runExtension('./src/index.ts');

// Manually simulate sending topic messages to the extension process

extensionDebugger
  .sendPromise('test-node-process-messsage-topic', { k1: 'v1' })
  .then((result) => {
    // The result callback sent by the expansion process
    console.log(result);
  })
  .catch((error) => {
    // Error callback sent by extension process
    console.log(error);
  })
  .finally(() => {
    console.log('finally');
  });

// Set the topic message callback of the renderer

extensionDebugger.setRendererTopicMessageCallback((topic, message) => {
  console.log(topic);
  console.log(message);
});

// Set render segment non-topic message callback

extensionDebugger.setRendererOtherMessageCallback((message) => {
  console.log(message);
});
```

## View debug message output

> Debug information and sent message information can be viewed in the debug console

![](images/2E4AE63D-5B39-4ccc-839A-3B32100FA966.png)

## Quickly simulate the rendering process to send topic messages

Click `simple_debug_tool_url` in the output log or click on the vscode prompt to open the quick debug tool
![](images/449D0F12-B963-4b2b-A602-5F8D56A57861.png)
![](images/2E4AE63D-5B39-4ccc-839A-3B32100FA966.png)

## Quick debugging tool

> Callback content can be viewed in the debug console

![](images/F479A123-DAF3-48e0-8A23-D1A5ECB26D3F.png)
