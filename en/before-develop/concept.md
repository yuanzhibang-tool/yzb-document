!> This chapter explains some concepts used in the development of Yuanzhibang Apps, such as binary, extension, etc.

### Open App

> Refers to the applications submitted on the Yuanzhibang Open Platform, including:

1. Referencing web applications developed by third parties.
2. Open platform applications developed by developers themselves.

### Binary

> Yuanzhibang `js bridge` namespace [`native`](/#/en/open-app-develop/js-api-native ' :ignore') api supports management binary packaged exe file, such as the command line `exe` on `windows`, `macOS` or `linux` command line applications, for security reasons, these binaries need to be submitted on the open platform and only can be used after review. Please ensure the security of the binaries. Do not obtain user privacy and security-related content without the consent of the user, and spread viruses, Trojan horses, and illegal binary. Expand upload After passing the review, it will be automatically distributed after user invocation.

### Extension

> By using `node.js` to develop applications with rich native capabilities, it provides more abundant capabilities for open applications, and extension development has its own specifications. For details, please refer to [Extension Development](/#/en/extension-develop/default ' :ignore') chapter

### Public Extension

> In order to facilitate the development of developers, Yuanzhibang provides some extensions to speedup the development, developers can run directly through `yzb.native.run`.
