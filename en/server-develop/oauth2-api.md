### Use the interface to get the user's open_id using the login-free code

!> Note: The `access_token` obtained here is conceptually different from the `access_token` obtained in service development. `access_token` needs attention here. The server `access_token` is mainly used to obtain and operate application-related resources. The user's `access_token` is the credential used to operate the user-related resources.

**interface address**

`POST /OAuth2/token`

**Parameter Description**

| Parameter    | Required | Description                                                                                      |
| ------------ | -------- | ------------------------------------------------------------------------------------------------ |
| `app_id`     | Yes      | Open platform provides more application ids                                                      |
| ` secret`    | yes      | secret key provided by the open platform                                                         |
| `grant_type` | Yes      | Always `authorization_code` here                                                                 |
| `code`       | Yes      | Use `yzb.core.requestAuthCode` for temporary authorization code for `JS in web development` here |

**return value**
successful return value

```json
{
  "status": 2000,
  "message": "ok",
  "data": {
    "open_id": "bkNhRE1LN2FGb3pnWEJKS2l0MzZ0OCt3cVMwRkE0SXJTaDd6T2FNSWp0UjhhMUt1N29Db3ltcEZabXFMaGp0d0c1WDU3czk5QVkwbmlTSHVoblZ0elZoMWhXT2tFYW1FSElzaFZuU3VRSWhzM1VKd3RxL3ozSU1rUWMwaUt2TGk4OHA5c21lS3pRTmV1YTRRTEJ6L0c1N3pyU3NVYlUwM01qd203WTRVUDZBPQ",
    "access_token": "5cc928f1eadd0a25bf18e08269c2309741e94b0b51585d987d24488331ca50de",
    "expires_in": 7200,
    "refresh_token": "1503c423d5303ccab35cb26792f403fcae48eec2bedca99b2e9259683f2a31ac",
    "scope": "sns_base"
  }
}
```

!> Note: `access_token` and `refresh_token` here are temporarily useless and cannot be used to update user information. To obtain user information, please refer to: User Resource Interface API/Get User Information.

wrong return value

```json
{
  "status": "4102",
  "message": "authorization_code is invalid",
  "data": []
}
```

### Get the interface of js_ticket

> `js_ticket` is the value used to sign the `JS` method called on the current page in the `core.config` method in web page development, which is equivalent to the key

**interface address**

`POST /OAuth2/ticket`

**Parameter Description**

| Parameter       | Required | Description                                                            |
| --------------- | -------- | ---------------------------------------------------------------------- |
| `app_id`        | Yes      | Open platform provides more application ids                            |
| ` access_token` | Yes      | The access_token obtained from the `Get server access_token interface` |
| `type`          | yes      | always `js_ticket` here                                                |

**return value**

successful return value

```json
{
  "status": "2000",
  "message": "ok",
  "data": {
    "ticket": "36bd5645fbadaf5e3ef4a889f0ac26ee14fa7ab0578e8e0108519a4706f2ab4c",
    "expires_in": 7200 //The validity period is 7200 seconds
  }
}
```

!>Note: Please reserve 128-bit storage space for `ticket`. Avoid length out of bounds and cause errors

> Note: Before the acquired `js_ticket` expires, after re-acquiring, the previous `js_ticket` will set the valid time to `10 minutes`, and it will expire automatically. Avoid the replacement of `js_ticket` and cause call errors.

wrong return value

```json
{
  "status": "4102",
  "message": "server_access_token is invalid",
  "data": []
}
```

---

### Interface to check whether the obtained access_token or js_ticket is valid

!>In the best practice, you do not need to call this interface to check if you use Alibaba Cloud Function Compute or docker to get the update `code` centrally.

> `access_token` or `js_ticket` are values ​​of type `code`, so the interface is named after `checkCode`

**interface address**

`POST /OAuth2/checkCode`

**Parameter Description**

| Parameter | Required | Description                                                                                            |
| --------- | -------- | ------------------------------------------------------------------------------------------------------ |
| `app_id`  | Yes      | Open platform provides more application ids                                                            |
| `type`    | Yes      | `access_token` when the detected `code` type is `access_token`, `js_ticket` if the type is `js_ticket` |
| `code`    | yes      | `code` value to detect                                                                                 |
| `open_id` | No       | This is the required value when the user's authorization `access_token` is detected                    |

**return value**
successful return value

```json
{
  "status": "2000",
  "message": "ok",
  "data": {
    "expires_in": 1654576906
  }
}
```

wrong return value

```json
{
  "status": "4102",
  "message": "server_access_token is invalid",
  "data": []
}
```

!> Invalid return is `status` is `4102`, other than `2000` is an error

---
