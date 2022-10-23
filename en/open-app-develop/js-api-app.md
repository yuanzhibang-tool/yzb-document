---

### `app.close`

**Main Description**

| primary key | value |
| ------------- | ------------------- |
| **Interface description:** | Close the `js` method of the current application |
| **Remarks** | None |

**Parameter verification instructions**

| Parameters | Description | Default | Validation Rules |
| --- | --- | --- | --- |
| `none` | none | none |none |

**Method parameter example**

````json
{}
````

**Method callback `next` parameter example**

````json
{}
````

---

### `app.showModal`

**Main Description**

| primary key                | value                                              |
| -------------------------- | -------------------------------------------------- |
| **Interface description:** | `js` method to display new url content using modal |
| **Remarks**                | None                                               |

**Parameter verification instructions**

| Parameters  | Description                                                                                      | Default | Validation Rules                          |
| ----------- | ------------------------------------------------------------------------------------------------ | ------- | ----------------------------------------- |
| `url`       | The url to open the modal view                                                                   | none    | none                                      |
| `width`     | The width of the open window, if it is too small or too large, it will be automatically adjusted | None    | None                                      |
| `height`    | The height of the open window, it will be automatically adjusted if it is too small or too large | None    | None                                      |
| `init_data` | The content passed to the modal window, how to use the reference                                 | Empty   | Please use the object to pass the content |

**Method parameter example**

```json
{
  "url": "https://www.baidu.com/", //url to open the modal view
  "width": 500, //The width of the open window
  "height": 400, //height of the open window
  "init_data": {
    //The content passed to the modal window, how to use the reference
    "k1": "v1",
    "k2": "v2"
  }
}
```

**Method callback `next` parameter example**

```json
{}
```

---

### `app.setUrlOpenAction`

**Main Description**

| primary key                | value                                                                                                                                 |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Interface description:** | Set the callback interface for opening the application through url, the interface will call back the complete url to the set function |
| **Remarks**                | None                                                                                                                                  |

**Parameter Description**

Pass in a function whose parameter is url

```javascript
// url example: yzb://yuanzhibang.com?action=open_app&app_action=app_detail&app_id=101170
yzb.app.setUrlOpenAction((url) => {
  console.log(`open app by url: ${url}`);
});
```

---

### `app.setVersion`

**Main Description**

| primary key                | value                                                                                          |
| -------------------------- | ---------------------------------------------------------------------------------------------- |
| **Interface description:** | Set the current application version number, which will be included in the application feedback |
| **Remarks**                | None                                                                                           |

**Parameter Description**

Pass in a version number parameter, it is recommended to be in `1.0.1` format

```javascript
yzb.app.setVersion('1.0.1');
```
