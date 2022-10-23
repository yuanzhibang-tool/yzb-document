### work process

> Please refer to the flowchart

![](../images/screenshot_1654686997675.png)

### Import js, inject Bridge Object

Import `js bridge` in the `header` of the `html` file, get the latest version [Bridge Info](en/open-app-develop/js-bridge-note)

```html
<script src="https://static.yuanzhibang.com/app/open/js/bridge/js-yzb-bridge-vx.x.x.js"></script>
<script>
// Set ready callback after introduction
yzb.ready(
()=>{
    // configure in callback
    var configData = {};
    yzb.core.config(configData);
}
);
<script>
```

> The injected object is named yzb, and all methods and properties are on the injected object.

---

### variable list

!> All version number information is in `0.0.0` format, released in accordance with the `major.minor.patch` version format, `major` is a major update version including `break change`, the changes are large, the calling process needs to be paid attention to.` minor` is a small update, no need to pay attention to api changes, only add api, unless necessary, will not make changes to the original interface, `patch` only fixes `bug`.

| variable name      | description                                                                                                                                                                 |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `version`          | Get the version number currently injected into `js bridge`                                                                                                                  |
| `appVersion`       | Get the version number of the desktop application                                                                                                                           |
| `containerVersion` | Get the version number of the desktop container, generally all interfaces are related to this value, and the container version number will be updated if there is an update |

**Example**

```javascript
var containerVersion = yzb.containerVersion;
```

---

### API List

!> The principles that need to be verified, one is that it will affect the operation of the page, and the other is that there will be security concerns.
| namespace | method name | whether `config` validation is required | user confirmation using popup | description |
| ------------ | ----------------------------- | -------- ------------ | -------------------- | ---------------- ----------------------------------------- |
| core | `core.config` | No | No | Used to inject page configuration information, enable `debug` and verify `jsApi` |
| core | `core.requestAuthCode` | yes | no | js method to get login-free `code` |
| core | `core.requestAccess` | Yes | No | Configure the `js` method that needs to be verified above, and get the `open_id` |
| app | `app.close` | yes | no | close the container page |
| app | `app.setUrlOpenAction` | no | no | set open app via external url pass the incoming full url to the app |
| app | `app.showModal` | yes | no | open modal window |
| notification | `notification.vibrate` | yes | no | shake window |
| preview | `preview.showImage` | yes | yes | open image player |
| preview | `preview.showPDF` | yes | yes | pdf presenter |
| setting | `setting.set` | yes | no | set application configuration |
| setting | `setting.get` | yes | no | get application configuration |
| setting | `setting.remove` | yes | no | remove application configuration |
| native | `native.run` | yes | yes | run native binaries |
| native | `native.stop` | yes | no | stop running native binaries |
| native | `native.setCallback` | Yes | No | Set various message callbacks for native binary programs |
| native | `native.getProcessInfo` | yes | no | get process info |
| native | `native.sendProcessMessage` | yes | no | send native `message` message to process |
| native | `native.getNativeInfo` | Yes | No | Get native related information |
| file | `file.exist` | yes | no | determine whether the file exists |
| file | `file.getFileHash` | yes | no | get file hash value |
| file | `file.getInfo` | yes | no | get file/folder info |
| file | `file.read` | yes | yes | read file |
| file | `file.write` | yes | yes | write file |
| file | `file.mkdir` | yes | yes | create directory |
| file | `file.remove` | yes | yes | remove file/folder |
| file | `file.getAppHome` | yes | no | get app data directory |
| file | `file.showItemInFolder` | yes | no | show file/folder in file manager/Finder/other file manager |
| file | `file.openPath` | yes | yes | open a folder or file |
| config | `config.get` | Yes | No | Get online configuration, added in container version `1.3.0`, add configuration on open platform |
