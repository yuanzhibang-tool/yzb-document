### 所有通过`js`的参数均需要进行验证,以免传入非法的参数问题造成异常错误

>[danger]分为两类参数,一类是通用的参数验证,另外一类是针对每个方法的参数验证,例如,`tid`为通用验证参数

### 通用规则写于此,其他的则写在对应的`json`传参示例中参数中.

| 通用参数值   | 规则 | 说明  |                                                                                  
| ------------ | -------------- | ---------------------- |
| `tid`| `require|int|max_length:11`  | `require`有时必传和非必传,注意 |
| `did` | `int|max_length:11`   | `require`有时必传和非必传,注意 |                                                      
| `work_id`    | 正则`^[a-zA-Z0-9_-]{4,128}$` | `work_id` 提示`仅允许大小写英文,数字,半角中划线,下划线组成,且大于等于4位,小于等于128位` |
| `identity`   | `^[a-zA-Z0-9_]{36,128}$`     | 提示为参数`非法`  |                                                                      
| `max_count`  | `min:1|max:1000`             |  `max`有时会传`50000`  |                                                                               
| `min_count`  | `min:1|max:1000`             |   `max`有时会传`50000`  |                                                                                      
| `title`      | `max_length:256`             |                                                                                         
| `app_id`     | `require|int|max_length:11`  |
| `open_patient_id` | 正则`^[a-zA-Z0-9_-]{4,512}$` | `openPatientId`,`仅允许大小写英文,数字,半角中划线,下划线组成,且大于等于4位,小于等于512位`   |
| `longitude`  | `require|min:-90|max:90`     |                                                                                         
| `latitude`   | `require|min:-180|max:180`   |                                                                                         
| `name`   | `min:1|max:64`   |                                                                                         

>[danger]如果参数值是 bool 类型的不验证,代码中采用`if else`进行处理,非基础类型的