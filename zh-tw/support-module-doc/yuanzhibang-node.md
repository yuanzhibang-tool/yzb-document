# @yuanzhibang/node <!-- {docsify-ignore} -->

用來進行猿之棒開放平台拓展的調試工具,模擬 renderer 進程和 node 進行進行通信以及回調

**倉庫地址:**

https://github.com/yuanzhibang-tool/yzb-node.git

**issue**

https://github.com/yuanzhibang-tool/yzb-node/issues

**npm**

https://www.npmjs.com/package/@yuanzhibang/node

## 安裝

`npm i @yuanzhibang/node --save-dev`
或者
`yarn add @yuanzhibang/node --dev`

## 使用

!>`@yuanzhibang/node`該模塊僅適用在拓展進程裡,該拓展在初始化後,將自動接收`process.on('message')`的消息回調,請勿在拓展進程的其他部位使用`process.on('message')`來配置消息回調,否則可能會造成模塊工作異常.
