> Interface for fast online configuration of applications

---

### `config.get`

!> This interface has been provided since the container `1.3.0` version

**Description**

| Key                        | Value                                |
| -------------------------- | ------------------------------------ |
| **Interface description:** | Get the `js` method of configuration |
| **Note**                   | None                                 |

**Parameters**

| Parameters | Description                                                                                           | Default | Validation Rules |
| ---------- | ----------------------------------------------------------------------------------------------------- | ------- | ---------------- |
| `key`      | If you don't pass it, get all the configurations under the user, support multiple separated by commas | None    | None             |

**Method parameter example**

```json
{
  "key": "test-setting,123"
}
```

**Method callback `next` parameter example**

!> Whether multiple or one is returned, it will be returned in this format, if not, there is no such value

```json
{
  "test-setting": "test-value",
  "123": {
    "key1": "v1"
  }
}
```
