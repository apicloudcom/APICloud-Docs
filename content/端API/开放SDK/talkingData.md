/*
Title: talkingData
Description: talkingData
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
    <a href="#getDeviceID-content">getDeviceID</a>
    <a href="#onPageStart-content">onPageStart</a>
    <a href="#onPageEnd-content">onPageEnd</a>
    <a href="#onEvent-content">onEvent</a>
    <a href="#setGlobalKV-content">setGlobalKV</a>
    <a href="#removeGlobalKV-content">removeGlobalKV</a>
    <a href="#setLocation-content">setLocation</a>
</div>
<div id="getDeviceID-content"></div>

#概述
　　talkingData封装了TalkingData App Analytics数据统计平台的SDK，使用此模块可轻松实现移动App的数据统计功能。


**使用此模块之前需先配置config文件的Feature，方法如下：**

    名称：talkingData

    参数：logEnable、exceptionReportEnabled、channel
  
    描述：设置talkingData的log开关，是否收集异常信息的开关，和发包的渠道。

**配置示例：**

```html
    <feature name="TalkingData">
        <param name="logEnable" value="false" />
        <param name="exceptionReportEnabled" value="true" />
        <param name="channel" value="AppStore" />
    </feature>
```
**字段描述：**

    1. logEnable：配置是否显示log，默认值“false”。

    2. exceptionReportEnabled：配置是否捕获异常，默认值“true”。
    
    3. channel：配置渠道标识符，无默认值。

<div id="method"></div>

##getDeviceID

获取TalkingData维护的设备ID  

getDeviceID(callback(ret, err))  

**callback(ret, err)**  
ret：

- 类型：字符串

err：

- 类型：JSON对象
- 内部字段：

        {  
            msg:""    //错误描述，字符串  
        }

**示例代码**

```js
var td = api.require('talkingData');

td.getDeviceID(function(ret,err){
    if(ret){
        api.alert({msg: ret});
    }
});
```

**补充说明**  

无  

**可用性**  

iOS系统，Android系统  

可提供的1.2.0及更高版本

<div id="onPageStart-content"></div>

##onPageStart

进入一个页面  

onPageStart({params})  
**params**  
pageName：

- 类型：字符串
- 默认值：无
- 描述：页面的名称，不能为空

**示例代码：**

```js
var td = api.require('talkingData');
td.onPageStart({pageName:'首页'});  
```

**补充说明**  

调用此接口后，确保在同一页面调用onPageEnd方法。 
　　 
**可用性**  

iOS系统，Android系统  
可提供的1.2.0及更高版本

<div id="onPageEnd-content"></div>

##onPageEnd

离开一个页面  

onPageEnd({params})

**params** 

pageName：

- 类型：字符串
- 默认值：无
- 描述：页面的名称，不能为空

**示例代码**

```js
var td = api.require('talkingData');
td.onPageEnd({pageName:'首页'});
```

**补充说明**  

调用此接口前，确保已调用过onPageStart方法。  

**可用性**  

iOS系统，Android系统  
可提供的1.2.0及更高版本


<div id="onEvent-content"></div>

##onEvent

自定义事件  

onEvent({params})  

**params**  

eventId：

- 类型：字符串
- 默认值：无
- 描述：自定义事件的ID，不能为空

eventLabel：

- 类型：字符串
- 默认值：无
- 描述：自定义事件的标签，可以为空

parameters：

- 类型：JOSN对象
- 默认值：无
- 描述：自定义事件的参数，可以为空

**示例代码**

```js
var td = api.require('talkingData');
td.onEvent({
    eventId:'首页推荐位点击',
    eventLabel:'第一广告位',
    parameters:{
        category:'服装',
        price:10
    }
});
```
    
**补充说明**  

eventId无需提前在数据平台中定义，可自行定义名称，直接加入到应用中需要跟踪的位置即可生效。  
格式：32个字符以内的中文、英文、数字、下划线，注意eventId中不要加空格或其他的转义字符。  
TalkingData最多支持10000个不同的Event ID。  

**可用性**  

iOS系统，Android系统  
可提供的1.2.0及更高版本

<div id="setGlobalKV-content"></div>

##setGlobalKV

设置全局Key-Value

setGlobalKV({params})

**params**

key：

- 类型：字符串
- 默认值：无
- 描述：全局参数的key，不能为空

value：

- 类型：字符串或Number
- 默认值：无
- 描述：全局参数的value，不能为空

**示例代码**

```js
var td = api.require('talkingData');

td.setGlobalKV({
    key:'brand',
    value:'vl'
});
```

**补充说明**  

如果所有事件都需要传输相同的参数，可以设置全局的Key-Value，这些Key-Value会自动添加到所有自定义事件。  
如果onEvent里传入的Key-Value里的key和全局Key-Value里的key冲突，以onEvent里传入的为准。  

**可用性**  

iOS系统，Android系统  
可提供的1.2.0及更高版本

<div id="removeGlobalKV-content"></div>

##removeGlobalKV

移除全局Key-Value  

removeGlobalKV({params})  

**params**  

key：

- 类型：字符串
- 默认值：无
- 描述：全局参数的key，不能为空

**示例代码**

```js
var td = api.require('talkingData');
td.setGlobalKV({
    key:'brand'
});
```

**补充说明**  

无  

**可用性**  

iOS系统，Android系统  
可提供的1.2.0及更高版本

<div id="setLocation-content"></div>

##setLocation

设置用户位置信息 

setLocation({params}}  

**params**  

latitude：

- 类型：float
- 默认值：0
- 描述：纬度

longitude：

- 类型：float
- 默认值：0
- 描述：经度

**示例代码**

```js
var td = api.require('talkingData');
td.setLocation({
    latitude:39.94,
    longitude:116.43
});
```

**补充说明**  

talkingData默认使用设备中收取的MCC（移动国家码）和用户联网IP来判定用户的地区，与地区相关的数据会有一定误差。  
如果您的应用会使用用户的位置信息，可通过接口将信息提交至TalkingData数据中，可使您获得更加精准的数据报表。  

**可用性** 

iOS系统  
可提供的1.2.0及更高版本

