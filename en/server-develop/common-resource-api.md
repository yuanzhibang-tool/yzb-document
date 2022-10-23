### Interface to get the total number of users

> Interface to get the total number of users used

**interface address**

`POST /CommonResource/getUserCount`

**Parameter Description**

| Parameter | Required | Description                           |
| --------- | -------- | ------------------------------------- |
| `app_id`  | yes      | `id` of the open platform application |

**return value**

successful return value

```json
{
  "status": "2000",
  "message": "ok",
  "data": {
    "user_count": "15"
  }
}
```

---
