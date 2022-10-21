!> 為了統一方便調試,請使用 `vscode` 進行開發調試,本章節的所有調試功能,均基於`vscode`說明,基於 <a href="https://github.com/yuanzhibang-tool/yzb-extension-quickstart-ts.git" target="_blank">yzb-extension-quickstart-ts</a>.如有問題請加群討論.

_注意:請確保您的系統已安裝好 node 環境,請使用 16 版本以上的 node,可以參考[如何安裝指定版本的 node?](/#/question/how-to-install-node-version-specified ':ignore')_

---

### 1.克隆項目到本地,切換到`main`分支,安裝依賴

```shell
git clone https://github.com/yuanzhibang-tool/yzb-extension-quickstart-ts.git
cd yzb-extension-quickstart-ts
git checkout main
npm install
```

---

### 2.運行 Debug Extension,此時即可使用斷點進行調試了

![運行 Debug Extension](../images/1658150046021.jpg ':size=500')

---

### 3.Ctrl + 點擊 TERMINAL 中的調試鏈接

![運行 Debug Extension](../images/1658150204383.jpg ':size=500')

---

### 4.在簡單調試工具中發送 topic 消息

![在簡單調試工具中發送 topic 消息](../images/20220718211945.jpg ':size=500')

---

!>一般需要將拓展開發和開放平台應用分開開發,開發完成後再聯合調試

---

## 與前端聯合調試

!>聯合調試前端需要`前端`項目添加依賴<a href="https://www.npmjs.com/package/@yuanzhibang/renderer" target="_blank">@yuanzhibang/renderer</a>,`拓展`項目需要依賴<a href="https://www.npmjs.com/package/@yuanzhibang/extension-debugger" target="_blank">@yuanzhibang/extension-debugger</a>

### 1.使用 extension debuger 啟動 ws 調試服務

```javascript
import {
  extensionDebugger,
  DebuggerLogger,
} from '@yuanzhibang/extension-debugger';

// !是否在vsc控制台打印
DebuggerLogger.withLog = true;
// !啟動ws調試服務
extensionDebugger.startWsServer(8889);
extensionDebugger.setExtensionPath('./debug/extension.ts');
```

### 2.前端對獲取的`IpcRendererWorker`實例進行`mock`,並在`猿之棒>設置>調試工具`打開前端頁面

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
// !可在初始化函數里添加tcp調試地址,默認localhost:8889,支持局域網以及遠程調試地址
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

!>此時即可完整實現拓展全生命週期的調試,如果拓展重啟,請重新刷新前端頁面以進行狀態重置
