!> 為了統一方便調試,請使用 `vscode` 進行開發調試,本章節的所有調試功能,均基於`vscode`說明,基於 <a href="https://github.com/yuanzhibang-tool/yzb-oapp-quick-start-angular" target="_blank">yzb-oapp-quick-start-angular</a> 項目進行說明,`vue`等其他框架的項目,`typescript`語言的項目,請務必開啟`sourceMap`,請參照調試.如有問題請加群討論.

_注意:請確保您的系統已安裝好 node 環境,請使用 16 版本以上的 node,可以參考[如何安裝指定版本的 node?](/#/question/how-to-install-node-version-specified ':ignore')_

### 1.開啟猿之棒桌面端遠程調試功能,開啟後,應用將會自動重啟

![開啟猿之棒桌面端遠程調試功能](../images/20220718173345.jpg ':size=500')

---

### 2.克隆項目到本地,切換到`main`分支,安裝依賴

```shell
git clone https://github.com/yuanzhibang-tool/yzb-oapp-quick-start-angular
cd yzb-oapp-quick-start-angular
git checkout main
npm install
```

---

### 3.啟動調試項目

```shell
npm run start
```

![啟動調試項目](../images/1658136140277.jpg ':size=700')

---

### 4.打開猿之棒調試工具

![打開猿之棒調試工具](../images/1658135684767.jpg ':size=700')

---

### 5.輸入 2 中啟動的項目`url`

![輸入url](../images/1658136323277.jpg ':size=700')

---

### 6.展示調試頁面

![展示調試頁面](../images/1658136583251.jpg ':size=700')

---

### 7.在 `vscode` 中打上斷點,啟動調試`Debug Renderer`

!>請先使用 `設置>調試工具`打開頁面後再執行 該步操作,否則會造成頁面無法加載.

![打上斷點](../images/20220718175515.jpg ':size=700')

---

### 8.進入斷點進行調試

您可以根據需要進行斷點調試

---

### 9.如何使用 chrome 調試拓展?

> 開發者們經常會使用 `chrome` 調試拓展來提高調試效率,如 `angular`,`vue` 調試拓展,猿之棒支持加載 `chrome` 調試拓展

1. 在 chrome 中安裝`CRX Extractor/Downloader`拓展
2. 在 chrome 拓展介紹頁麵點擊 `CRX Extractor/Downloader`拓展
3. 該拓展包會自動下載下來
4. 將拓展壓縮包解壓後放置在`設置>打開調試拓展文件目錄`中
5. 之後再使用調試工具調試後,會自動加載該目錄下的所有`chrome`調試拓展

![調試拓展](../images/1658139335141.jpg ':size=700')
