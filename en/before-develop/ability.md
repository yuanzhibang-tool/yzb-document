> By using `js bridge`, the interface provided by the server can be extended to achieve different application capabilities

### `js bridge` section

| Serial number | Capability                                                                                                                           |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| 1             | User identification (requires server interface)                                                                                      |
| 2             | User resource permission application                                                                                                 |
| 3             | File Operations                                                                                                                      |
| 4             | Open platform application closes the application itself                                                                              |
| 5             | Show modal box showing `url` content                                                                                                 |
| 6             | Receive callbacks for opening open platform applications through `url` through external (such as browsers, third-party applications) |
| 7             | Display images and pdf files through windows                                                                                         |
| 8             | Vibrate window to alert user                                                                                                         |
| 9             | Run `binary` or [extension](/#/extension-develop/default ':ignore') or `script`                                                      |
| 10            | Save, get, delete the settings of open platform applications                                                                         |

### `Server Interface` section

| Serial number | Capability                                                                              |
| ------------- | --------------------------------------------------------------------------------------- |
| 1             | User identification (need to cooperate with `js bridge`)                                |
| 2             | Get information such as the user's avatar, nickname, etc. (user permission is required) |
| 3             | Get the total number of users who have added apps                                       |
| 3             | `OAuth2.0` related `code` acquisition                                                   |

### `Extension` section

> Using the capabilities given by `node.js`, most of the native capabilities of `node` can be realized. For specific development, please refer to the [Extension Development](/#/extension-develop/default ':ignore') chapter
