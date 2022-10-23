### Network interface calls uniformly use the `https` protocol

---

### Network interface calls uniformly use the `POST` method

---

### The format returned by the network interface is unified as `json` format

!> The `leaf` nodes (the last level node) in `json` format returned by the interface are all of `string` type, and users can forcibly convert specific types according to specific needs

---

**refer to:**

```json
{
  "status": "4102",
  "message": "authorization_code is invalid",
  "data": []
}
```

_Return value description_

| Key       | type                          | description                                                                                                                                                  |
| --------- | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `status`  | `Four-digit positive integer` | Current operation status code, used to mark success or error type, 2xxx is success, 4xxx is failure, please refer to the status code description for details |
| `message` | `String`                      | User-readable description of the current operation result                                                                                                    |
| `data`    | `array or dictionary`         | The content returned by the current operation to be obtained, if there is no required parameter, an empty array is returned by default                       |

---

> For the status code, please refer to [Return Status Code Description](/#/server-develop/status-code ':ignore')
