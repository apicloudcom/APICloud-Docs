/*
Title: callRecord
Description: callRecord
*/

<div class="outline">

[openCallRecord](#a1)

</div>

#**概述**

callRecord 模块封装了系统通话记录的相关接口；**本模块暂仅支持 Android 平台**

<div id="a1"></div>
#**openCallRecord**

获取通话记录

openCallRecord(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：


```js
{
    status: true,                      //布尔类型；是否操作成功，true|false
    CallRecord: [
        number : "10086",              //字符串类型；电话号码
        type : "呼出",                  //字符串类型；呼出、呼入、未接、挂断
        time : "2016-01-11 13:13:13",  //字符串类型；呼叫时间
        name : "中国移动",              //字符串类型；备注姓名 
        duration : "12",               //字符串类型；通话时间  单位秒(s)
    ]
}
```

```
##示例代码

```js
var callRecord = api.require('callRecord');	
callRecord.openCallRecord(function(ret){
	alert(JSON.stringify(ret));
});
```

##可用性

Android系统

可提供的1.0.0及更高版本