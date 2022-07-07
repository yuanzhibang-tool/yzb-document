### 用户通过app.openModal打开新的modal窗口
>该窗口从中无法使用`bridge yzb`注入的对象,但是注入了一个名为`modalHelper`的全局对象.
*****
**该对象有如下几个方法:**
### **接口名称**:`modalHelper.getInitData`
**主要描述**
| 主键          | 值                         |
| ------------- | ------------------- |
| **接口描述:** | 获取通过`app.openModal`中传入的`initData`值 |  
| **备注** | 为同步接口直接赋值即可 |  
*示例*
```javascript
var passInitData = modalHelper.getInitData();
```
*****
### **接口名称**:`modalHelper.cancel`
**主要描述**
| 主键          | 值                         |
| ------------- | ------------------- |
| **接口描述:** | 关闭该modal窗口并返回空内容 |  
| **备注** | 在`app.openModal`中传入的`next`接收回调,如果modal窗口失焦后关闭也会触发该方法. |  
*示例*
```javascript
// 在应用窗口中
yzb.app.showModal({
    data:{
	"url": "https://www.baidu.com/",  //modal视图要打开的url
	"width": 500,  //打开窗口的宽
	"height": 400, //打开窗口的高
	"init_data": {  //给modal窗口传入的内容,具体如何使用参考
		"k1": "v1",
		"k2": "v2"
        }
    },
    next:(result)=>{
        console.log(result);
        //调用modalHelper.cancel(),result为空,调用modalHelper.confirm(confirmData),result为传入的confirmData
    },
    error:()=>{},
    complete:()=>{}
    });

// 在modal窗口中
modalHelper.cancel();
```
*****
### **接口名称**:`modalHelper.confirm`
**主要描述**
| 主键          | 值                         |
| ------------- | ------------------- |
| **接口描述:** | 关闭该modal窗口并返回需要回调给调用窗口的内容 |  
| **备注** | 在`app.openModal`中传入的`next`接收回调参数 |  
*示例*
```javascript
// 在应用窗口中
yzb.app.showModal({
    data:{
	"url": "https://www.baidu.com/",  //modal视图要打开的url
	"width": 500,  //打开窗口的宽
	"height": 400, //打开窗口的高
	"init_data": {  //给modal窗口传入的内容,具体如何使用参考
		"k1": "v1",
		"k2": "v2"
        }
    },
    next:(result)=>{
        console.log(result);
        //调用modalHelper.cancel(),result为空,调用modalHelper.confirm(confirmData),result为传入的confirmData
    },
    error:()=>{},
    complete:()=>{}
    });

// 在modal窗口中
var comfirmData = {
    ck1:"cv1",
    ck2:"cv2",
};
modalHelper.comfirm(comfirmData);
```