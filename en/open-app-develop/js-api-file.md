---

### `file.exist`

**Description**

| Key | Value |
| ------------- | ------------------- |
| **Interface description:** | How to get whether the file exists |
| **Note** | None |

**Parameters**

| Parameters | Description | Default | Validation Rules |
| --- | --- | --- | --- |
| `path` | file absolute path | none | refer to parameter verification instructions `require` |

**Method parameter example**

````json
{
  "path": "C:\\Users\\Admin\\Downloads\\c.png"
}
````

**Method callback `next` parameter example**

````json
{
        "exist":true|false
}

````

---

### `file.getFileHash`

**Description**

| Key                        | Value                                                    |
| -------------------------- | -------------------------------------------------------- |
| **Interface description:** | Get the `js` method of the file `hash`                   |
| **Note**                   | Can return `md5`, `sha1`, `sha256`, `sha512` of the file |

**Parameters**

| Parameters  | Description        | Default | Validation Rules                                       |
| ----------- | ------------------ | ------- | ------------------------------------------------------ |
| `hash_name` | hash type          | none    | `md5`,`sha1`,`sha256`,`sha512`                         |
| `path`      | file absolute path | none    | refer to parameter verification instructions `require` |

**Method parameter example**

```json
{
  "hash_name": "sha1",
  "path": "C:\\Users\\Admin\\Downloads\\c.png"
}
```

**Method callback `next` parameter example**

```json
{
  "hash": "3b84de2d341b3bb66d891b3982e77e8d3bb93d59082e56d236ad897f5e631909"
}
```

---

### `file.getInfo`

**Description**

| Key                        | Value                                           |
| -------------------------- | ----------------------------------------------- |
| **Interface description:** | `js` method to get file or file information     |
| **Note**                   | Can return the relevant information of the file |

**Parameters**

| Parameters | Description        | Default | Validation Rules                                       |
| ---------- | ------------------ | ------- | ------------------------------------------------------ |
| `path`     | file absolute path | none    | refer to parameter verification instructions `require` |

**Method parameter example**

```json
{
  "path": "C:\\Users\\Admin\\Downloads\\c.png"
}
```

**Method callback `next` result example**

```json
{
  "executable": true, //Whether executable
  "is_dir": false, //Is it a folder
  "readable": true, //whether readable
  "size": 454, //file size, in bytes
  "update_time": 1654441257838.4453, //Update time
  "writable": true //Writable
}
```

---

### `file.read`

**Description**

| Key                        | Value                                              |
| -------------------------- | -------------------------------------------------- |
| **Interface description:** | Get the `js` method of file content                |
| **Note**                   | You can return the content information of the file |

**Parameters**

| Parameters | Description        | Default | Validation Rules                                       |
| ---------- | ------------------ | ------- | ------------------------------------------------------ |
| `path`     | file absolute path | none    | refer to parameter verification instructions `require` |

**Method parameter example**

```json
{
  "path": "C:\\Users\\Admin\\Downloads\\c.png"
}
```

**Method callback `next` parameter example**

```json
{
  "content": "dmVyc2lvbjogMC4wLjM5NgpmaWxlczoKICAtIHVybDogWXVhbn…8LQogIDEu5LyY5YyW5oCn6IO9CiAgMi7kv67lpI1idWdzCg=="
  //The content of the file content after `base64`, read the content for the binary content, please convert it as needed
}
```

---

### `file.write`

**Description**

| Key                        | Value                                |
| -------------------------- | ------------------------------------ |
| **Interface description:** | `js` method for writing file content |
| **Note**                   | None                                 |

**Parameters**

| Parameters | Description                                                                         | Default | Validation Rules                                          |
| ---------- | ----------------------------------------------------------------------------------- | ------- | --------------------------------------------------------- | ------ |
| `path`     | file absolute path                                                                  | none    | refer to parameter verification instructions `require`    |
| `content`  | The content written in the file, which is the content after `base64` of the content | None    | Refer to the parameter verification description `require` |
| `mode`     | append or write new                                                                 | none    | `append                                                   | write` |

**Method parameter example**

```json
{
  "content": "5Y+R55Sf55qE5Y+R55qE",
  "path": "C:\\Users\\Admin\\Downloads\\c.png",
  "mode": "append"
}
```

**Method callback `next` parameter example**

```json
{}
```

---

### `file.mkdir`

**Description**

| Key                        | Value                        |
| -------------------------- | ---------------------------- |
| **Interface description:** | `js` method to create folder |
| **Note**                   | None                         |

**Parameters**

| Parameters | Description          | Default | Validation Rules |
| ---------- | -------------------- | ------- | ---------------- |
| `path`     | Folder absolute path | none    | none             |

**Method parameter example**

```json
{
  "path": "C:\\Users\\Admin\\Downloads"
}
```

**Method callback `next` parameter example**

```json
{}
```

---

### `file.remove`

**Description**

| Key                        | Value                          |
| -------------------------- | ------------------------------ |
| **Interface description:** | `js` method for deleting files |
| **Note**                   | None                           |

**Parameters**

| Parameters | Description        | Default | Validation Rules |
| ---------- | ------------------ | ------- | ---------------- |
| `path`     | absolute file path | none    | none             |

**Method parameter example**

```json
{
  "path": "C:\\Users\\Admin\\Downloads\\c.png"
}
```

**Method callback `next` parameter example**

```json
{}
```

---

### `file.getAppHome`

**Description**

| Key                        | Value                                         |
| -------------------------- | --------------------------------------------- |
| **Interface description:** | Get the working directory of this application |
| **Note**                   | None                                          |

**Parameters**

| Parameters | Description | Default | Validation Rules |
| ---------- | ----------- | ------- | ---------------- |
| `none`     | none        | none    | none             |

**Method parameter example**

```json
{}
```

**Method callback `next` parameter example**

```json
{
  "app_home": "C:\\Users\\Shandawei\\.yzb\\app-data\\bb8fa894-50c7-4972-9527-bb12f15ae918\\123456"
}
```

---

### `file.showItemInFolder`

**Description**

| Key                        | Value                                          |
| -------------------------- | ---------------------------------------------- |
| **Interface description:** | Display the file or folder in the file browser |
| **Note**                   | None                                           |

**Parameters**

| Parameters | Description        | Default | Validation Rules |
| ---------- | ------------------ | ------- | ---------------- |
| `path`     | absolute file path | none    | none             |

**Method parameter example**

```json
{
  "path": "C:\\Users\\Admin\\Downloads\\c.png"
}
```

**Method callback `next` parameter example**

```json
{}
```

---

### `file.openPath`

**Description**

| Key                        | Value                          |
| -------------------------- | ------------------------------ |
| **Interface description:** | Open a specific file or folder |
| **Note**                   | None                           |

**Parameters**

| Parameters | Description        | Default | Validation Rules                                       |
| ---------- | ------------------ | ------- | ------------------------------------------------------ |
| `path`     | file absolute path | none    | refer to parameter verification instructions `require` |

**Method parameter example**

```json
{
  "path": "C:\\Users\\Admin\\Downloads\\c.png"
}
```

**Method callback `next` parameter example**

```json
{}
```
