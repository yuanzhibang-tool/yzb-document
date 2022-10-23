### The interface for obtaining permission information owned by the application

> For specific permission information, please refer to the permission introduction page

**interface address**

`POST /UserResource/getAppAccess`

**Parameter Description**

| Parameter | Required | Description                           |
| --------- | -------- | ------------------------------------- |
| `open_id` | yes      | user's `open_id`                      |
| `app_id`  | yes      | `id` of the open platform application |

**return value**

successful return value

```json
{
  "status": "2000",
  "message": "ok",
  "data": ["user/send_app_message"]
}
```

Error return value, see error message introduction

```json
{
  "status": "4102",
  "message": "authorization_code is invalid",
  "data": []
}
```

---

### Interface for obtaining basic user information

**interface address**

`POST /UserResource/getUserBaseInfo`

**Parameter Description**

| Parameter | Required | Description                           |
| --------- | -------- | ------------------------------------- |
| `open_id` | yes      | user's `open_id`                      |
| `app_id`  | yes      | `id` of the open platform application |

**return value**

successful return value

```json
{
  "status": "2000",
  "message": "ok",
  "data": {
    "nick": "angel",
    "avatar": "https://upload.yuanzhibang.com/file/2019-07-21/0B4C96B3-DD62-47F9-B9BF-080CAF090DBA.jpeg",
    "sex": "1" //1 male, 2 female, 3 unknown
  }
}
```

Error return value, see error message introduction

```json
{
  "status": "4102",
  "message": "authorization_code is invalid",
  "data": []
}
```
