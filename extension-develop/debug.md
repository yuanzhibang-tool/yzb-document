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

### 2.运行 Debug Extension

![运行 Debug Extension](../images/1658150046021.jpg ':size=500')

---

### 3.Ctrl + 点击 TERMINAL 中的调试链接

![运行 Debug Extension](../images/1658150204383.jpg ':size=500')

---

### 4.在简单调试工具中发送 topic 消息

![在简单调试工具中发送 topic 消息](../images/20220718211945.jpg ':size=500')

---

!>一般需要将拓展开发和开放平台应用分开开发,开发完成后再联合调试
