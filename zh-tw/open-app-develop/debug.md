!> 为了统一方便调试,请使用 `vscode` 进行开发调试,本章节的所有调试功能,均基于`vscode`说明,基于 <a href="https://github.com/yuanzhibang-tool/yzb-oapp-quick-start-angular" target="_blank">yzb-oapp-quick-start-angular</a> 项目进行说明,`vue`等其他框架的项目,`typescript`语言的项目,请务必开启`sourceMap`,请参照调试.如有问题请加群讨论.

_注意:请确保您的系统已安装好 node 环境,请使用 16 版本以上的 node,可以参考[如何安装指定版本的 node?](/#/question/how-to-install-node-version-specified ':ignore')_

### 1.开启猿之棒桌面端远程调试功能,开启后,应用将会自动重启

![开启猿之棒桌面端远程调试功能](../images/20220718173345.jpg ':size=500')

---

### 2.克隆项目到本地,切换到`main`分支,安装依赖

```shell
git clone https://github.com/yuanzhibang-tool/yzb-oapp-quick-start-angular
cd yzb-oapp-quick-start-angular
git checkout main
npm install
```

---

### 3.启动调试项目

```shell
npm run start
```

![启动调试项目](../images/1658136140277.jpg ':size=700')

---

### 4.打开猿之棒调试工具

![打开猿之棒调试工具](../images/1658135684767.jpg ':size=700')

---

### 5.输入 2 中启动的项目`url`

![输入url](../images/1658136323277.jpg ':size=700')

---

### 6.展示调试页面

![展示调试页面](../images/1658136583251.jpg ':size=700')

---

### 7.在 `vscode` 中打上断点,启动调试`Debug Renderer`

!>请先使用 `设置>调试工具`打开页面后再执行 该步操作,否则会造成页面无法加载.

![打上断点](../images/20220718175515.jpg ':size=700')

---

### 8.进入断点进行调试

您可以根据需要进行断点调试

---

### 9.如何使用 chrome 调试拓展?

> 开发者们经常会使用 `chrome` 调试拓展来提高调试效率,如 `angular`,`vue` 调试拓展,猿之棒支持加载 `chrome` 调试拓展

1. 在 chrome 中安装`CRX Extractor/Downloader`拓展
2. 在 chrome 拓展介绍页面点击 `CRX Extractor/Downloader`拓展
3. 该拓展包会自动下载下来
4. 将拓展压缩包解压后放置在`设置>打开调试拓展文件目录`中
5. 之后再使用调试工具调试后,会自动加载该目录下的所有`chrome`调试拓展

![调试拓展](../images/1658139335141.jpg ':size=700')
