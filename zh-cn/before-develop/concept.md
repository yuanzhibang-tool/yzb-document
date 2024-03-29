!> 本章节说明了一些猿之棒开发中使用到的概念,例如二进制,拓展等.

### 开放平台应用

> 是指在猿之棒开放平台提交的应用,包含`1.引用第三方开发的网页应用`,`2.开发者自己开发的开放平台应用`

### 二进制

> 猿之棒`js bridge`接口 `native`下的接口支持管理运行二进制打包的应用,如`windows`上的命令行`exe`,`macOS` 或者 `linux`上的命令行应用,为了用户使用安全,这些二进制需要在开放平台提交,审核通过后可以使用,请务必保证二进制安全,不要未经用户同意获取用户隐私,安全性相关的内容,擅自传播病毒,木马,非法二进制内容.拓展上传通过审核后,将在用户调用后自动分发.

### 拓展

> 通过使用`node.js`开发拥有丰富原生能力的应用,为开放平台应用提供更加丰富的能力,拓展开发具有自己的规范,具体请参见[拓展开发](/#/extension-develop/default ':ignore')章节

### 公共拓展

> 指的只,为了方便开发者开发,猿之棒开放平台提供的已经开发好的拓展,支持开发者 `js bridge`调用
