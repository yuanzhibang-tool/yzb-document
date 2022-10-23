## core namespace method call documentation <!-- {docsify-ignore} -->

> Core namespace method calls related documentation

### `core.requestAuthCode`

**Description**

| Key                        | Value                                                                  |
| -------------------------- | ---------------------------------------------------------------------- |
| **Interface description:** | Get the js method for login-free `code`                                |
| **Note**                   | By calling the `/OAuth2/requestJsAuthCode` method of the open platform |

**Parameters**

| Parameters | Description      | Default | Validation Rules                                       |
| ---------- | ---------------- | ------- | ------------------------------------------------------ |
| `app_id`   | Application `id` | None    | Refer to parameter verification instructions `require` |
| `tid`      | Team `id`        | None    | Refer to parameter verification instructions `require` |

**Method parameter example**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "data": {
       "app_id":"100011", //app_id of the open platform
       "tid":"100027" //If it is a team application, this parameter needs to be passed. If the parameter is entered by the app, the team will be added to the parameter
     }
}

```

**Method callback `next` parameter example**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "result": {
        "code":"34TGERVG45GSDFBGERTYE45YGDFBFS"
    }
}

```

!>**Note:**

> This method has only `next` callback, no error callback

---

### `core.requestAccess`

**Description**

| Key                        | Value                                                           |
| -------------------------- | --------------------------------------------------------------- |
| **Interface description:** | Interface for requesting users to grant application permissions |
| **Note**                   | Open the interface of setting application permission page       |

**Parameters**

| Parameters | Description         | Default         | Validation Rules                                                                       |
| ---------- | ------------------- | --------------- | -------------------------------------------------------------------------------------- |
| `app_id`   | Application `id`    | None            | Refer to parameter verification instructions `require`                                 |
| `access`   | list of permissions | `[]`empty array | `array`, add the verification regular of each permission `^[1-9a-zA-Z_-[*]\/]{1,128}$` |

**Method parameter example**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "data": {
       "app_id":"100011" //app_id of the open platform,
       "tid": "100043", //If it is a team app, this parameter must be passed
       "access": ["team/send_team_message", "team/send_app_message", "team/get_team_member_base_info"]
     }
}

```

**Method callback `next` parameter example**

```
{
    "identity": "9100dbeb-95ff-4c03-8355-826b3eaab2b7",
    "result": {}
}

```

!>**Note:**

> This method has only `next` callback, no error callback

---

### `core.config`

!> The parameters required by this interface must be generated on the server side, not on the web page. For specific generation rules, please refer to

**Description**

| Key                        | Value                                                                    |
| -------------------------- | ------------------------------------------------------------------------ |
| **Interface description:** | Inject page configuration information, enable `debug` and verify `jsApi` |
| **Note**                   | None                                                                     |

**Parameters**

| Parameters    | Description                                                                                                                                                        | Default | Validation Rules                                                            |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- | --------------------------------------------------------------------------- |
| `app_id`      | Application `id`                                                                                                                                                   | None    | Refer to parameter verification instructions `require`                      |
| `timestamp`   | timestamp                                                                                                                                                          | none    | `require;int;length:10,11`                                                  |
| `nonce_str`   | random string                                                                                                                                                      | none    | `require;length:4,128`                                                      |
| `signature`   | Signature value                                                                                                                                                    | None    | `require;length:4,128`,regular `^[a-zA-Z0-9_-]{4,128}$`                     |
| `debug`       | This parameter does not need to be processed or obtained at present. Whether the `debug` mode is enabled or not, the returned result and error will pop up `alert` | `false` | `bool`                                                                      |
| `js_api_list` | `js_api_list` to be verified                                                                                                                                       | None    | `require;array;array*min_length:1`,regular `^[1-9a-zA-Z*-[\*][.]]{1,128} $` |
| `is_spa`      | `Single page application`                                                                                                                                          | `false` | `bool`                                                                      |

**Method parameter example**

```
{
"data": {
"app_id": "101000", //The `app_id` of the open platform,
                "tid": "100027", //The `tid` of the team
"timestamp": 1544579311, //Note that it is a digital type, and the timestamp that generates the signature is `unix timestamp`, which is only accurate to seconds
"nonce_str": "fasdfwHlhHLJ", //random string
"signature": "ba0dc6903b0f5ce48a1519604256aec7306ffb5a", //signature value
"debug": true, //This parameter does not need to be processed at present, no need to obtain, whether to enable `debug` mode, after the return result and error will pop up `alert`, the default is `false`
"js_api_list": ["tool.cache.set", "tool.cache.get"] //js_api_list that needs to be verified
},
"identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c"
}

```

**Example of return value**

_The `next`_ called back after success

```
{
    "identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//Note that there are no parameters here
    }
}

```

_and error callback_

`Network error callback` (when the native call has an interface network error, it is not a `200` error, it is a network level error)

```

{
    "identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//Note that there are no parameters here
        "code": "100002",
"description": "Network error",
        "suggestion": "Please check the network status"
    }
}


```

`Network call error callback` (When the native call has an interface return interface data error, `status` is not `2000` error, it is the return result error level)

```

{
    "identity": "core_config_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//Note that there are no parameters here
        "code": "100003",
"description": "core.config parameter validation failed",
        "suggestion": "Please check core.config parameters"
    }
}


```

`When calling a method that needs to be verified, but there is no verified method` The error of the call is used when calling the verified method, **not used in this method**

```
{
    "identity": "cache_set_c8f9a3e3_3bba_4fbe_a130_86208116d31c",
    "result": {//Note that there are no parameters here
        "code": "100004",
"description": "The javascript function is not configured using core.config",
        "suggestion": "Please use this core.config function to configure"
    }
}
```
