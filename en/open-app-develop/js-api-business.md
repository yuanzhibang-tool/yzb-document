> Business related interfaces

---

### `business.isChinaIp`

!> This interface has been provided since the container `1.3.2` version

**Description**

| Key                        | Value                                             |
| -------------------------- | ------------------------------------------------- |
| **Interface description:** | Determine whether it is a domestic `ip` interface |
| **Note**                   | None                                              |

**Parameters**

| Parameters | Description | Default | Validation Rules |
| ---------- | ----------- | ------- | ---------------- |
| `none`     | none        | none    | none             |

**Method parameter example**

```json
{}
```

**Method callback `next` parameter example**

!> Whether multiple or one is returned, it will be returned in this format, if not, there is no such value

```json
{
  "is_china_ip": true|false
}
```

---

### `business.isMobileBound`

!> This interface has been provided since the container `1.3.2` version

**Description**

| Key                        | Value                                                                         |
| -------------------------- | ----------------------------------------------------------------------------- |
| **Interface description:** | The interface to determine whether the user is bound to a mobile phone number |
| **Note**                   | For real-name verification in China                                           |

**Parameters**

| Parameters | Description | Default | Validation Rules |
| ---------- | ----------- | ------- | ---------------- |
| `none`     | none        | none    | none             |

**Method parameter example**

```json
{}
```

**Method callback `next` parameter example**

!> Whether multiple or one is returned, it will be returned in this format, if not, there is no such value

```json
{
  "is_mobile_bound": true|false
}
```

---

### `business.showAccountSetting`

!> This interface has been provided since the container `1.3.2` version

**Description**

| Key                        | Value                                                                                                             |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Interface description:** | Judging that the user is not bound with a mobile phone number, enter the binding mobile phone number setting page |
| **Note**                   | For real-name verification in China                                                                               |

**Parameters**

| Parameters   | Description                                             | Default | Validation Rules |
| ------------ | ------------------------------------------------------- | ------- | ---------------- |
| `app_action` | None, `show_mobile_bind` when mobile binding is enabled | None    | None             |

**Method parameter example**

```json
{
  "app_action": "show_mobile_bind"
}
```

**Method callback `next` parameter example**

!> Whether multiple or one is returned, it will be returned in this format, if not, there is no such value

```json
{}
```

---

### `business.showAppUpdator`

!> This interface has been provided since the container `1.3.2` version

**Description**

| Key                        | Value                                                                                                                                     |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **Interface description:** | If the version of `js` does not support the interface, the user will be prompted to upgrade, and the application upgrade page will pop up |
| **Note**                   | For application upgrade                                                                                                                   |

**Parameters**

| Parameters | Description | Default | Validation Rules |
| ---------- | ----------- | ------- | ---------------- |
| `none`     | none        | none    | none             |

**Method parameter example**

```json
{}
```

**Method callback `next` parameter example**

!> Whether multiple or one is returned, it will be returned in this format, if not, there is no such value

```json
{
  "is_mobile_bound": true|false
}
```
