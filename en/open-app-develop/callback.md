## Related general callback methods

> Methods of related generic callbacks

### bridge ready callback

> bridge ready callback

`yzb.ready`

**Description**

| Key                        | Value                          |
| -------------------------- | ------------------------------ |
| **Interface description:** | `bridge` ready callback        |
| **Note**                   | Proxy method, cannot be called |

**Example of calling js method natively**

```javascript
yzb.ready(() => {
  console.log('bridge is ready now!');
});
```

---

### bridge prepare callback for error

> bridge prepares a callback for an error

`yzb.error`

**Description**

| Key                        | Value                                                                                  |
| -------------------------- | -------------------------------------------------------------------------------------- |
| **Interface description:** | `bridge` prepares an error callback                                                    |
| **Note**                   | It is recommended to refresh the page after receiving this error, which rarely happens |

**Example of calling js method natively**

```javascript
yzb.error(() => {
  console.log('bridge init error!');
});
```
