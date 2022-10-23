> Used to quickly implement user list data, the `secure_content` will store with `ssl 2048 bit` certificate encryption to ensure data security in the cloud.

---

### `list.add`

!> Supported since the container version `1.4.2`

**Description**

| Key                        | Value                               |
| -------------------------- | ----------------------------------- |
| **Interface description:** | `js` method for adding list entries |
| **Note**                   | None                                |

**Parameters**

| Parameters       | Description                                                                                                                                                                                                          | Default | Validation Rules                                                                                                     |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | -------------------------------------------------------------------------------------------------------------------- |
| `key`            | Identity of the list                                                                                                                                                                                                 | None    | English case `[A-Za-z]`, number `[0-9]`, underline`[_]`, dash `[-]`, forward slash`[/]`, the length is in `[1,1024]` |
| `content`        | Normal content, supports json object, and will also be converted to objects when get, and non-objects are directly set to `null`                                                                                     | None    | None                                                                                                                 |
| `secure_content` | Security content, store with `ssl 2048 bit` certificate encryption to ensure data security in the cloud, support json object, and will also be converted to objects when get, non-objects are directly set to `null` | None    | None                                                                                                                 |

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

!> Supported since the container version `1.4.2`

**Description**

| Key                        | Value                              |
| -------------------------- | ---------------------------------- |
| **Interface description:** | `js` method to delete list entries |
| **Note**                   | None                               |

**Parameters**

| Parameters | Description                                                      | Default | Validation Rules                              |
| ---------- | ---------------------------------------------------------------- | ------- | --------------------------------------------- |
| `id`       | The `id` of the entry, multiple id split by commas are supported | None    | A positive integer, the length is in `[1,11]` |

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

!> Supported since the container version `1.4.2`

**Description**

| Key                        | Value                                                             |
| -------------------------- | ----------------------------------------------------------------- |
| **Interface description:** | The `js` method to empty the user's list with the specified `key` |
| **Note**                   | None                                                              |

**Parameters**

| Parameters | Description          | Default | Validation Rules                                                                                                     |
| ---------- | -------------------- | ------- | -------------------------------------------------------------------------------------------------------------------- |
| `key`      | Identity of the list | None    | English case `[A-Za-z]`, number `[0-9]`, underline`[_]`, dash `[-]`, forward slash`[/]`, the length is in `[1,1024]` |

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

!> Supported since the container version `1.4.2`

**Description**

| Key                        | Value                                 |
| -------------------------- | ------------------------------------- |
| **Interface description:** | `js` method for updating list entries |
| **Note**                   | None                                  |

**Parameters**

| Parameters       | Description                                                                                                                                                                                                          | Default | Validation Rules                              |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | --------------------------------------------- |
| `id`             | The `id` of the entry, multiple id split by commas are supported                                                                                                                                                     | None    | A positive integer, the length is in `[1,11]` |
| `content`        | Normal content, supports json object, and will also be converted to objects when get, and non-objects are directly set to `null`                                                                                     | None    | None                                          |
| `secure_content` | Security content, store with `ssl 2048 bit` certificate encryption to ensure data security in the cloud, support json object, and will also be converted to objects when get, non-objects are directly set to `null` | None    | None                                          |

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

!> Supported since the container version `1.4.2`, and the list is order by `id desc`

**Description**

| Key                        | Value                                                |
| -------------------------- | ---------------------------------------------------- |
| **Interface description:** | Get the `js` method of the list with specified `key` |
| **Note**                   | None                                                 |

**Parameters**

| Parameters     | Description                                              | Default | Validation Rules                                                                                                     |
| -------------- | -------------------------------------------------------- | ------- | -------------------------------------------------------------------------------------------------------------------- |
| `load_more_id` | The minimum `id` in the list you got, use `0` when first | None    | A positive integer, the length is in `[1,11]`                                                                        |
| `key`          | Set the identification key of the corresponding list     | None    | English case `[A-Za-z]`, number `[0-9]`, underline`[_]`, dash `[-]`, forward slash`[/]`, the length is in `[1,1024]` |

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

!> Supported since the container version `1.4.2`

**Description**

| Key                        | Value                                |
| -------------------------- | ------------------------------------ |
| **Interface description:** | `js` method to get list item details |
| **Note**                   | None                                 |

**Parameters**

| Parameters | Description           | Default | Validation Rules                              |
| ---------- | --------------------- | ------- | --------------------------------------------- |
| `id`       | Id of the list entity | None    | A positive integer, the length is in `[1,11]` |

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
