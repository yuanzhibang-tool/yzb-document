## JS related calls are related, follow the following format conventions

---

### Method naming

Methods follow `namespace.operationname` or `namespace.function.operationname`
For example, in `core.requestAuthCode`, `core` is the `namespace`, `requestAuthCode` operation name

### method parameters

```json
{
    data: {
        // data passed to the method
        content:"Jmx0O3AmZ3Q76L+Z6YeM5piv5a+M5paH5pysJmx0Oy9wJmd0Ow==" //The incoming content has been base64 encoded
    },
    next:(result)=>{
        //Successful callback, the callback will only call this method when the method indicates that there is a next callback, and result is also an optional parameter, some methods have, some methods do not, the format of the result, refer to the specific method
        console.log(result);
    },
    cancel:()=>{
        //Cancel the callback, the callback will only be called when the method indicates that there is a cancel callback, the callback has no parameters
    },
    error:(error)=>{
        //Error callback, the callback will only call this method when the method indicates that there is an error callback, and error is a required parameter, all methods have it, please refer to the return code description for the specific format
        console.log(error);
    },
    complete:()=>{
        //This method is executed after each method, whether it succeeds or fails, and there are no parameters
        console.log('complete');
    }
}
```

> [danger] Callback error code, please refer to `Open Platform Application Development/Callback Error Code`
