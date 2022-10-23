> An interface for quickly synchronizing user settings information to help open platform applications synchronize settings

---

### `setting.set`

!> This interface has been provided since the container `1.3.0` version

**Description**

| Key                        | Value                                 |
| -------------------------- | ------------------------------------- |
| **Interface description:** | `js` method for setting configuration |
| **Note**                   | None                                  |

**Parameters**

| Parameters | Description                                                                                  | Default | Validation Rules |
| ---------- | -------------------------------------------------------------------------------------------- | ------- | ---------------- |
| `key`      | set the corresponding key                                                                    | none    | none             |
| `value`    | Set the corresponding value, support objects, and will also be converted to objects when get | None    | None             |

**Method parameter example**

```json
{
  "key": "test-setting",
  "value": "123456"
}
```

**Method callback `next` parameter example**

```json
{}
```

---

### `setting.get`

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

---

---

### `setting.remove`

!> This interface has been provided since the container `1.3.0` version

**Description**

| Key                        | Value                                       |
| -------------------------- | ------------------------------------------- |
| **Interface description:** | Delete the `js` method of the configuration |
| **Note**                   | None                                        |

**Parameters**

| Parameters | Description                                                                                                      | Default | Validation Rules |
| ---------- | ---------------------------------------------------------------------------------------------------------------- | ------- | ---------------- |
| `key`      | If not passed, all the configuration under the user will be cleared. Support multiple passes separated by commas | None    | None             |

**Method parameter example**

```json
{
  "key": "test-setting"
}
```

**Method callback `next` parameter example**

!> Whether multiple or one is returned, it will be returned in this format, if not, there is no such value

```json
{}
```

---
