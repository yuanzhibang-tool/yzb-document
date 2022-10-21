## JS 相關調用相關,遵照如下格式約定

---

### 方法命名

方法遵照 `命名空間.操作名`或者 `命名空間.功能.操作名 `
例如 `core.requestAuthCode`中,`core`是`命名空間`,`requestAuthCode`操作名

### 方法參數

```json
{
    data: {
        //傳遞給方法的數據
        content:"Jmx0O3AmZ3Q76L+Z6YeM5piv5a+M5paH5pysJmx0Oy9wJmd0Ow==" //傳入的內容已進行base64編碼
    },
    next:(result)=>{
        //成功回調,該回調只有該方法指明有next回調時才會調用該方法,而result也是可選參數,有些方法有,有些方法沒有,result的格式,參考具體方法
        console.log(result);
    },
    cancel:()=>{
        //取消回調,該回調只有該方法指明有cancel回調時才會調用該方法,該回調沒有參數
    },
    error:(error)=>{
        //錯誤回調,該回調只有該方法指明有error回調時才會調用該方法,而error是必選參數,所有方法均有,具體格式參照返回碼說明
        console.log(error);
    },
    complete:()=>{
        //該方法為每次方法後,無論成功還是失敗必定會執行,且無參數
        console.log('complete');
    }
}
```

> [danger]回調的錯誤碼,請參照 `開放平台應用開發/回調錯誤code`
