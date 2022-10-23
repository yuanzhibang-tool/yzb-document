> Used to quickly implement user list data, where `secure_content` implements `ssl 2048`-bit certificate encryption to ensure data security

---

### `list.add`

!> This interface has been provided since the container `1.4.2` version

**Main Description**

| primary key                | value                               |
| -------------------------- | ----------------------------------- |
| **Interface description:** | `js` method for adding list entries |
| **Remarks**                | None                                |

**Parameter verification instructions**

| Parameters       | Description                                                                                                                                                                                                              | Default | Validation Rules                                                                             |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- | -------------------------------------------------------------------------------------------- |
| `key`            | Set the identification key of the corresponding list                                                                                                                                                                     | None    | English case, number, underline, forward slash, the shortest `1` bit, the longest `1024` bit |
| `content`        | Sets the corresponding non-secure content, supports objects, and will also be converted to objects when get, and non-objects are directly set to `null`                                                                  | None    | None                                                                                         |
| `secure_content` | Set the corresponding security content, implement `ssl 2048`-bit certificate encryption to ensure data security, support objects, and will also be converted to objects when get, non-objects are directly set to `null` | None    | None                                                                                         |

**Method parameter example**

```json
{
  "key": "test/list",
  "content": { "test": "value" },
  "secure_content": { "test": "value" }
}
```

**Method callback `next` parameter example**

```json
{
  "id": "4",
  "key": "test/list",
  "content": { "test": "value" },
  "secure_content": { "test": "value" },
  "add_time": "1666540531",
  "update_time": "1666540531"
}
```

---

### `list.delete`

!> This interface has been provided since the container `1.4.2` version

**Main Description**

| primary key                | value                              |
| -------------------------- | ---------------------------------- |
| **Interface description:** | `js` method to delete list entries |
| **Remarks**                | None                               |

**Parameter verification instructions**

| Parameters | Description                                                        | Default | Validation Rules                                             |
| ---------- | ------------------------------------------------------------------ | ------- | ------------------------------------------------------------ |
| `id`       | The `id` of the corresponding entry, multiple commas are supported | None    | A positive integer, the shortest is `1`, the longest is `11` |

**Method parameter example**

```json
{
  "id": "12,123"
}
```

**Method callback `next` parameter example**

```json
{}
```

---

### `list.empty`

!> This interface has been provided since the container `1.4.2` version

**Main Description**

| primary key                | value                                                                  |
| -------------------------- | ---------------------------------------------------------------------- |
| **Interface description:** | The `js` method to clear the list corresponding to a `key` of the user |
| **Remarks**                | None                                                                   |

**Parameter verification instructions**

| Parameters | Description                                          | Default | Validation Rules                                                                              |
| ---------- | ---------------------------------------------------- | ------- | --------------------------------------------------------------------------------------------- |
| `key`      | Set the identification key of the corresponding list | None    | English case, number, underscore, forward slash, the shortest `1` bit, the longest `1024` bit |

**Method parameter example**

```json
{
  "key": "test/list"
}
```

**Method callback `next` parameter example**

```json
{}
```

---

### `list.update`

!> This interface has been provided since the container `1.4.2` version

**Main Description**

| primary key                | value                               |
| -------------------------- | ----------------------------------- |
| **Interface description:** | `js` method for adding list entries |
| **Remarks**                | None                                |

**Parameter verification instructions**

| Parameters       | Description                                                                                                                                                                                                              | Default | Validation Rules                             |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- | -------------------------------------------- |
| `id`             | Corresponding entry `id` key                                                                                                                                                                                             | None    | Positive integer, shortest `1`, longest `11` |
| `content`        | Set the corresponding non-secure content, support objects, and will also be converted to objects when get, non-objects are directly set to `null`                                                                        | None    | None                                         |
| `secure_content` | Set the corresponding security content, implement `ssl 2048`-bit certificate encryption to ensure data security, support objects, and will also be converted to objects when get, non-objects are directly set to `null` | None    | None                                         |

**Method parameter example**

```json
{
  "id": "123",
  "content": { "test": "value" },
  "secure_content": { "test": "value" }
}
```

**Method callback `next` parameter example**

```json
{
  "id": "4",
  "key": "test/list",
  "content": { "test": "value" },
  "secure_content": { "test": "value" },
  "add_time": "1666540531",
  "update_time": "1666540531"
}
```

---

### `list.getList`

!> This interface is provided after the container `1.4.2` version, and the list is arranged in reverse order according to `id`

**Main Description**

| primary key                | value                                                     |
| -------------------------- | --------------------------------------------------------- |
| **Interface description:** | Get the `js` method of the list corresponding to the list |
| **Remarks**                | None                                                      |

**Parameter verification instructions**

| Parameters     | Description                                                                    | Default | Validation Rules                                                                              |
| -------------- | ------------------------------------------------------------------------------ | ------- | --------------------------------------------------------------------------------------------- |
| `load_more_id` | The corresponding minimum `id` value obtained, the first time `0` is passed in | None    | Positive integer, the shortest `1` bit, the longest `11` bit                                  |
| `key`          | Set the identification key of the corresponding list                           | None    | English case, number, underscore, forward slash, the shortest `1` bit, the longest `1024` bit |

**Method parameter example**

```json
{
  "load_more_id": "123",
  "key": "test/list"
}
```

**Method callback `next` parameter example**

```json
[
  {
    "id": "4",
    "key": "test/list",
    "content": { "test": "value" },
    "secure_content": { "test": "value" },
    "add_time": "1666540531",
    "update_time": "1666540531"
  },
  {
    "id": "3",
    "key": "test/list",
    "content": { "test": "value" },
    "secure_content": { "test": "value" },
    "add_time": "1666540531",
    "update_time": "1666540531"
  }
]
```

---

---

### `list.getDetail`

!> This interface has been provided since the container `1.4.2` version

**Main Description**

| primary key                | value                                |
| -------------------------- | ------------------------------------ |
| **Interface description:** | `js` method to get list item details |
| **Remarks**                | None                                 |

**Parameter verification instructions**

| Parameters | Description                    | Default | Validation Rules                             |
| ---------- | ------------------------------ | ------- | -------------------------------------------- |
| `id`       | Corresponding entry `id` value | None    | Positive integer, shortest `1`, longest `11` |

**Method parameter example**

```json
{
  "id": "123"
}
```

**Method callback `next` parameter example**

```json
{
  "id": "4",
  "key": "test/list",
  "content": { "test": "value" },
  "secure_content": { "test": "value" },
  "add_time": "1666540531",
  "update_time": "1666540531"
}
```

---
