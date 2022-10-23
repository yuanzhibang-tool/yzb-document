!> In order to unify and facilitate debugging, please use `vscode` for development and debugging. All debugging functions in this chapter are based on `vscode` instructions, based on <a href="https://github.com/yuanzhibang-tool/yzb- extension-quickstart-ts.git" target="_blank">yzb-extension-quickstart-ts</a>. If you have any questions, please join the group discussion.

_Note: Please make sure that your system has installed the node environment, please use node version 16 or above, you can refer to [How to install a specified version of node?](/#/question/how-to-install-node-version-specified ':ignore')_

---

### 1. Clone the project locally, switch to the `main` branch, and install dependencies

```shell
git clone https://github.com/yuanzhibang-tool/yzb-extension-quickstart-ts.git
cd yzb-extension-quickstart-ts
git checkout main
npm install
```

---

### 2. Run Debug Extension, then you can use breakpoints for debugging

![Run Debug Extension](../images/1658150046021.jpg ':size=500')

---

### 3. Ctrl + click the debug link in TERMINAL

![Run Debug Extension](../images/1658150204383.jpg ':size=500')

---

### 4. Send topic messages in simple debugging tools

![Send topic message in Simple Debug Tool](../images/20220718211945.jpg ':size=500')

---

!> Generally, it is necessary to develop the expansion development and the open platform application separately, and then jointly debug after the development is completed.

---

## Joint debugging with the front end

!>Joint debugging front-end requires `front-end` project to add dependencies<a href="https://www.npmjs.com/package/@yuanzhibang/renderer" target="_blank">@yuanzhibang/renderer</a>,` The extension project needs to depend on <a href="https://www.npmjs.com/package/@yuanzhibang/extension-debugger" target="_blank">@yuanzhibang/extension-debugger</a>

### 1. Use extension debuger to start ws debugging service

```javascript
import {
  extensionDebugger,
  DebuggerLogger,
} from '@yuanzhibang/extension-debugger';

// ! Whether to print in vsc console
DebuggerLogger.withLog = true;
// ! Start the ws debug service
extensionDebugger.startWsServer(8889);
extensionDebugger.setExtensionPath('./debug/extension.ts');
```

### 2. The front-end `mock` the obtained `IpcRendererWorker` instance, and open the front-end page in `Ape's Stick> Settings> Debugging Tools`

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
// ! You can add the tcp debugging address in the initialization function, the default is localhost:8889, which supports LAN and remote debugging addresses
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

!> At this point, the debugging of the entire life cycle of the extension can be fully realized. If the extension restarts, please refresh the front-end page to reset the state.
