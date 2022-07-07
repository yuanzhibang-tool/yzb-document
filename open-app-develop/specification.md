## JS 相关调用相关,遵照如下格式约定

---

### 方法命名

方法遵照 `命名空间.操作名`或者 `命名空间.功能.操作名 `
例如 `core.requestAuthCode`中,`core`是`命名空间`,`requestAuthCode`操作名

### 方法参数

```json
{
    data: {
        //传递给方法的数据
        content:"Jmx0O3AmZ3Q76L+Z6YeM5piv5a+M5paH5pysJmx0Oy9wJmd0Ow==" //传入的内容已进行base64编码
    },
    next:(result)=>{
        //成功回调,该回调只有该方法指明有next回调时才会调用该方法,而result也是可选参数,有些方法有,有些方法没有,result的格式,参考具体方法
        console.log(result);
    },
    cancel:()=>{
        //取消回调,该回调只有该方法指明有cancel回调时才会调用该方法,该回调没有参数
    },
    error:(error)=>{
        //错误回调,该回调只有该方法指明有error回调时才会调用该方法,而error是必选参数,所有方法均有,具体格式参照返回码说明
        console.log(error);
    },
    complete:()=>{
        //该方法为每次方法后,无论成功还是失败必定会执行,且无参数
        console.log('complete');
    }
}
```

> [danger]回调的错误码,请参照 `开放平台应用开发/回调错误code`
