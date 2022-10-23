> Notify related namespace method invocation related documentation

### `notification.vibrate`

**Description**

| Key                        | Value                                            |
| -------------------------- | ------------------------------------------------ |
| **Interface description:** | Call the vibration method                        |
| **Note**                   | Call this interface, the whole window will shake |

**Parameters**

| Parameters | Description | Default | Validation Rules |
| ---------- | ----------- | ------- | ---------------- |
| none       | none        | none    | none             |

**Method parameter example**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "data": {}
}

```

**Method callback `next` parameter example (only `next` callback, no error callback)**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "result": {}
}
```

!>**Note:**

> no error callback

---

### `notification.showToast`

**Description**

| Key                        | Value                                                             |
| -------------------------- | ----------------------------------------------------------------- |
| **Interface description:** | How to display toast light tips                                   |
| **Note**                   | Information will be prompted on the upper part of the application |

**Parameters**

| Parameters | Description | Default | Validation Rules |
| ---------- | ----------- | ------- | ---------------- |
| none       | none        | none    | none             |

**Method parameter example**

```
{
    type: "info", //Message type, info|warning|success|error
    content: "This is the prompt content!"
}

```

**Method callback `next` parameter example (only `next` callback, no error callback)**

!> Note: no error callback
