The user opens a new modal window via app.openModal from which the `bridge yzb` injected object is not available, but a global object called `modalHelper` is injected.

---

**This object has the following methods:**

### `modalHelper.getInitData`

**Main Description**

| primary key                | value                                                         |
| -------------------------- | ------------------------------------------------------------- |
| **Interface description:** | Get the value of `initData` passed in `app.openModal`         |
| **Remarks**                | You can directly assign values ​​to the synchronous interface |

_Example_

```javascript
var passInitData = modalHelper.getInitData();
```

---

### `modalHelper.cancel`

**Main Description**

| primary key                | value                                                                                                                                         |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Interface description:** | Close the modal window and return empty content                                                                                               |
| **Remarks**                | The `next` passed in `app.openModal` receives a callback, and this method is also triggered if the modal window is closed after losing focus. |

_Example_

```javascript
// in the application window
yzb.app.showModal({
  data: {
    url: 'https://www.baidu.com/', //url to open the modal view
    width: 500, //the width of the open window
    height: 400, //height of the open window
    init_data: {
      //The content passed to the modal window, how to use the reference
      k1: 'v1',
      k2: 'v2',
    },
  },
  next: (result) => {
    console.log(result);
    //Call modalHelper.cancel(), the result is empty, call modalHelper.confirm(confirmData), the result is the incoming confirmData
  },
  error: () => {},
  complete: () => {},
});

// in the modal window
modalHelper.cancel();
```

---

### `modalHelper.confirm`

**Main Description**

| primary key                | value                                                                                            |
| -------------------------- | ------------------------------------------------------------------------------------------------ |
| **Interface description:** | Close the modal window and return the content that needs to be called back to the calling window |
| **Remarks**                | `next` passed in `app.openModal` receives callback parameters                                    |

_Example_

```javascript
// in the application window
yzb.app.showModal({
  data: {
    url: 'https://www.baidu.com/', //url to open the modal view
    width: 500, //the width of the open window
    height: 400, //height of the open window
    init_data: {
      //The content passed to the modal window, how to use the reference
      k1: 'v1',
      k2: 'v2',
    },
  },
  next: (result) => {
    console.log(result);
    //Call modalHelper.cancel(), the result is empty, call modalHelper.confirm(confirmData), the result is the incoming confirmData
  },
  error: () => {},
  complete: () => {},
});

// in the modal window
var comfirmData = {
  ck1: 'cv1',
  ck2: 'cv2',
};
modalHelper.comfirm(comfirmData);
```
