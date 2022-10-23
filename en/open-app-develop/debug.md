!> In order to unify and facilitate debugging, please use `vscode` for development and debugging. All debugging functions in this chapter are based on `vscode` instructions, based on <a href="https://github.com/yuanzhibang-tool/yzb- oapp-quick-start-angular" target="_blank">yzb-oapp-quick-start-angular</a> project description, `vue` and other framework projects, `typescript` language projects, please be sure to open `sourceMap`, please refer to debugging. If you have any questions, please join the group discussion.

_Note: Please make sure that your system has installed the node environment, please use node version 16 or above, you can refer to [How to install a specified version of node?](/#/question/how-to-install-node-version-specified ':ignore')_

### 1. Turn on the remote debugging function on the desktop of Ape's Stick. After turning it on, the application will restart automatically

![Enable the remote debugging function of Ape's Stick on the desktop](../images/20220718173345.jpg ':size=500')

---

### 2. Clone the project locally, switch to the `main` branch, and install dependencies

```shell
git clone https://github.com/yuanzhibang-tool/yzb-oapp-quick-start-angular
cd yzb-oapp-quick-start-angular
git checkout main
npm install
```

---

### 3. Start the debug project

```shell
npm run start
```

![Start debug project](../images/1658136140277.jpg ':size=700')

---

### 4. Open the ape stick debugging tool

![Open the ape stick debugging tool](../images/1658135684767.jpg ':size=700')

---

### 5. Enter the project `url` started in 2

![input url](../images/1658136323277.jpg ':size=700')

---

### 6. Display the debug page

![Show debug page](../images/1658136583251.jpg ':size=700')

---

### 7. Set a breakpoint in `vscode` and start debugging `Debug Renderer`

!>Please use `Settings>Debugging Tools` to open the page before performing this step, otherwise the page will fail to load.

![Breakpoint](../images/20220718175515.jpg ':size=700')

---

### 8. Enter breakpoints for debugging

You can debug with breakpoints as needed

---

### 9. How to use chrome to debug extensions?

> Developers often use `chrome` debugging extensions to improve debugging efficiency, such as `angular`, `vue` debugging extensions, and the ape stick supports loading `chrome` debugging extensions

1. Install the `CRX Extractor/Downloader` extension in chrome
2. Click the `CRX Extractor/Downloader` extension on the chrome extension introduction page
3. The expansion pack will be downloaded automatically
4. Unzip the extension archive and place it in `Settings>Open Debugging Extension File Directory`
5. After debugging with the debugging tool, all `chrome` debugging extensions in this directory will be automatically loaded

![Debug extension](../images/1658139335141.jpg ':size=700')
