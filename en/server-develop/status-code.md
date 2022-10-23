#### Return status code description

> Since the important role of the status code is to guide the program to automatically analyze and process, whether to retry or stop retrying, we divide errors into two types of errors. Classes require special handling

| Error code | Description                    |
| ---------- | ------------------------------ |
| `2000`     | Success                        |
| `2011`     | Success, but no data           |
| `4000`     | Generic error                  |
| `4102`     | Invalid `code` passed in       |
| `4103`     | No permission                  |
| `4104`     | The user did not add the `app` |
