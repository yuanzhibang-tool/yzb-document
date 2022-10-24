> By using `js bridge` api, the server OAuth api and the extensions, your app can implement rich functionality.

### `js bridge` section

| Index | Capability                                                                                                                           |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| 1     | User identification (requires server oauth api)                                                                                      |
| 2     | Get user resources .                                                                                                                 |
| 3     | File Operations                                                                                                                      |
| 4     | Close the application                                                                                                                |
| 5     | Show modal window for showing `url` content                                                                                          |
| 6     | Receive callbacks for opening open platform applications through `url` through external (such as browsers, third-party applications) |
| 7     | Display images and pdf files through windows                                                                                         |
| 8     | Vibrate window to notice user                                                                                                        |
| 9     | Run `binary` or [extension](/#/en/extension-develop/default ':ignore') or `script`                                                   |
| 10    | Save, get, delete the settings of open platform applications                                                                         |
| 11    | Get app online configs which you saved on `https://open.yuanzhibang.com`                                                             |

### `Server Interface` section

| Serial number | Capability                                                                              |
| ------------- | --------------------------------------------------------------------------------------- |
| 1             | User identification (need to work with `js bridge`)                                     |
| 2             | Get information such as the user's avatar, nickname, etc. (user permission is required) |
| 3             | Get the total number of users who have added apps                                       |
| 3             | `OAuth2.0` related `code`                                                               |

### `Extension` section

> Using the capabilities given by `node.js`, most of the native capabilities of `node` can be realized. For more, please refer to the [Extension Development](/#/en/extension-develop/default ':ignore') chapter
