### All parameters that pass `js` need to be verified to avoid abnormal errors caused by passing in illegal parameters.

!> Divided into two types of parameters, one is general parameter verification, the other is parameter verification for each method, for example, `tid` is a general verification parameter

### The general rules are written here, and the others are written in the parameters of the corresponding `json` parameter transfer example.

| Common parameter values | Rules                               | Description |
| ----------------------- | ----------------------------------- | ----------- |
| `tid`                   | `require,int,max_length:11,require` |             |
| `app_id`                | `require,int,max_length:11`         |             |
| `name`                  | `min:1,max:64`                      |             |
