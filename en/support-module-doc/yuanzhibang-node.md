# @yuanzhibang/node <!-- {docsify-ignore} -->

A debugging tool used to expand the Ape Stick open platform, simulate the renderer process and node to communicate and call back

**Warehouse Address:**

https://github.com/yuanzhibang-tool/yzb-node.git

**issue**

https://github.com/yuanzhibang-tool/yzb-node/issues

**npm**

https://www.npmjs.com/package/@yuanzhibang/node

## Install

`npm i @yuanzhibang/node --save-dev`
or
`yarn add @yuanzhibang/node --dev`

## use

!>`@yuanzhibang/node`This module is only applicable to the extension process. After the extension is initialized, it will automatically receive the message callback of `process.on('message')`. Please do not use it in other parts of the extension process. process.on('message')` to configure the message callback, otherwise it may cause the module to work abnormally.
