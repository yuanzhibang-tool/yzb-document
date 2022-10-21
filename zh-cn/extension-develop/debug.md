!> 为了统一方便调试,请使用 `vscode` 进行开发调试,本章节的所有调试功能,均基于`vscode`说明,基于 <a href="https://github.com/yuanzhibang-tool/yzb-extension-quickstart-ts.git" target="_blank">yzb-extension-quickstart-ts</a>.如有问题请加群讨论.

_注意:请确保您的系统已安装好 node 环境,请使用 16 版本以上的 node,可以参考[如何安装指定版本的 node?](/#/question/how-to-install-node-version-specified ':ignore')_

---

### 1.克隆项目到本地,切换到`main`分支,安装依赖

```shell
git clone https://github.com/yuanzhibang-tool/yzb-extension-quickstart-ts.git
cd yzb-extension-quickstart-ts
git checkout main
npm install
```

---

### 2.运行 Debug Extension,此时即可使用断点进行调试了

![运行 Debug Extension](../images/1658150046021.jpg ':size=500')

---

### 3.Ctrl + 点击 TERMINAL 中的调试链接

![运行 Debug Extension](../images/1658150204383.jpg ':size=500')

---

### 4.在简单调试工具中发送 topic 消息

![在简单调试工具中发送 topic 消息](../images/20220718211945.jpg ':size=500')

---

!>一般需要将拓展开发和开放平台应用分开开发,开发完成后再联合调试

---

## 与前端联合调试

!>联合调试前端需要`前端`项目添加依赖<a href="https://www.npmjs.com/package/@yuanzhibang/renderer" target="_blank">@yuanzhibang/renderer</a>,`拓展`项目需要依赖<a href="https://www.npmjs.com/package/@yuanzhibang/extension-debugger" target="_blank">@yuanzhibang/extension-debugger</a>

### 1.使用 extension debuger 启动 ws 调试服务

```javascript
import {
  extensionDebugger,
  DebuggerLogger,
} from '@yuanzhibang/extension-debugger';

// !是否在vsc控制台打印
DebuggerLogger.withLog = true;
// !启动ws调试服务
extensionDebugger.startWsServer(8889);
extensionDebugger.setExtensionPath('./debug/extension.ts');
```

### 2.前端对获取的`IpcRendererWorker`实例进行`mock`,并在`猿之棒>设置>调试工具`打开前端页面

```javascript
import {
  ipc,
  IpcDataHelper,
  IpcRendererWorker,
  Renderer,
  JsConfigInfo,
  IpcRendererWorkerMock,
} from '@yuanzhibang/renderer';

this.exeExtensionMessageWorker = ipc.getWorker('run_exe_extension');
// !可在初始化函数里添加tcp调试地址,默认localhost:8889,支持局域网以及远程调试地址
const mock = new IpcRendererWorkerMock('localhost:8889');
mock.mockWorker(this.exeExtensionMessageWorker);
this.exeExtensionMessageWorker.onStart((startInfo) => {
  console.log('onStart');
  console.log(startInfo);
});
this.exeExtensionMessageWorker.onWillInit((willInitInfo) => {
  console.log('onWillInit');
  console.log(willInitInfo);
});
this.exeExtensionMessageWorker.onInit((initInfo) => {
  console.log('onInit');
  console.log(initInfo);
});
this.exeExtensionMessageWorker.onWillExit((info) => {
  console.log('onWillExit');
  console.log(info);
});
this.exeExtensionMessageWorker.onExit((info) => {
  console.log('onExit');
  console.log(info);
});
this.exeExtensionMessageWorker.onClose((info) => {
  console.log('onClose');
  console.log(info);
});
this.exeExtensionMessageWorker.onExit((info) => {
  console.log('onExit');
  console.log(info);
});
this.exeExtensionMessageWorker.onStdOut((info) => {
  console.log('onStdOut');
  if (info) {
    const outString = IpcDataHelper.uint8ArrayToString(info, 'utf8');
    console.log(outString);
  }
});
this.exeExtensionMessageWorker.onStdError((info) => {
  console.log('onStdError');
  if (info) {
    const outString = IpcDataHelper.uint8ArrayToString(info, 'utf8');
    console.log(outString);
  }
});
this.exeExtensionMessageWorker.on('recieved-raw-data', (info) => {
  console.log('recieved-raw-data');
  console.log(info);
});
this.exeExtensionMessageWorker.on('test-renderer-message-topic', (message) => {
  console.log(message);
});
```

!>此时即可完整实现拓展全生命周期的调试,如果拓展重启,请重新刷新前端页面以进行状态重置
