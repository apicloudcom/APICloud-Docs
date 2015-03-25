/*
Title: bmobPush
Description: bmobPush
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[init](#a1)

[push](#a2)

[saveLocation](#a3)

[addChannel](#a4)

[removeChannel](#a5)
</div>

#**概述**

Bmob封装了Bmob后端云SDK中的推送功能，使用此模块可轻松实现推送到各种限制条件的用户端



#**init**<div id="a1"></div>

注册应用

init({params}, callback(ret, err))

##params

appid：

- 类型：字符串
- 默认值：无
- 描述：从Bmob后端应用管理找到的Application Id，不能为空

##callback(ret, err)

ret：

- 类型：String对象

	用于后面接受推送信息

err：

- 类型：JSON对象

内部字段：

```
{
	result:"error"		//操作结果
	error:""           //操作错误描述
}
```

##示例代码

```
var applicationId = "1234567890123";
var param = {appid:applicatioinId};
var resultCallback = function(ret, err){
	document.getElementById("pushinfo").innerHTML = JSON.stringify(ret);
	if(err)
		api.alert(err);
}
var bmob = api.require('bmobPush');
bmob.init(param,resultCallback);
```

##补充说明

注册应用

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**push**<div id="a2"></div>

推送信息

push({params}, callback(ret, err))

##params

content：

- 类型：字符串
- 默认值：无
- 描述：发表的内容，不能为空

type：

- 类型：字符串
- 默认值：无
- 描述：推送规则（详见[推送类型](!Constant)常量），不能为空

channel：

- 类型：字符串
- 默认值：无
- 描述：推送到的频道，当type为channel时，该字段有效且不能为空。可用；分隔

ios_deviceToken：

- 类型：字符串
- 默认值：无
- 描述：推送到IOS端的设备token，当type为ios时该字段有效，如果空则表示推送到所有IOS设备，否则推送单个


android_installationId：

- 类型：字符串
- 默认值：无
- 描述：推送到Android端的设备id，当type为android时该字段有效，如果空则表示推送到所有Android设备，否则推送单个


latitude：
- 类型：double类型
- 默认值：无
- 描述：推送到地球上某点一定半径范围内的所有设备，由latitude指示该点的纬度，当type为location时该字段有效，注意纬度的取值范围

longitude：

- 类型：double类型
- 默认值：无
- 描述：推送到地球上某点一定半径范围内的所有设备，由latitude指示该点的经度，当type为location时该字段有效，注意经度的取值范围

distance：
- 类型：double类型
- 默认值：无
- 描述：推送到地球上某点一定半径范围内的所有设备，由distance指示距离该点的范围（单位：公里），当type为location时该字段有效

time：

- 类型：String类型
- 默认值：无
- 描述：按时间推送，推送给最后一次登录在某日期前的用户（不活跃用户），当type为time时该字段有效，是以字符串表示的日期，格式为yyyyMMdd或者yyyyMMddhhmmss



##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
{
	result:"succeed"	//操作结果
}
```
err：

- 类型：JSON对象

内部字段：

```
{
	result:"error"		//操作结果
	error:""           //操作错误描述
}
```

##示例代码

```
//按Android设备ID推送
var type_str = "android";
var installationId = "1234567890";//请在Bmob后台查看
var content_str = 'Hello from Bmob';
var param = {content:content_str,type:type_str,android_installationId：installationId};
var resultCallback = function(ret, err){
	document.getElementById("result").innerHTML = JSON.stringify(ret);
	if(err)
		api.alert(err);
}
var bmob = api.require('bmobPush');
bmob.push(param,resultCallback);
```

```
//按经纬度和范围进行推送
var type_str = "location";
var latitude_double = 23.25;
var longitude_double = 103.66;
var distance_double = 10.00;
var content_str = 'Hello from Bmob';
var param = {content:content_str,type:type_str,latitude：latitude_double,longitude:longitude_double,distance:distance_double};
var resultCallback = function(ret, err){
	document.getElementById("result").innerHTML = JSON.stringify(ret);
	if(err)
		api.alert(err);
}
var bmob = api.require('bmobPush');
bmob.push(param,resultCallback);
```

```
//给所有用户推送
var type_str = "all";
var content_str = 'Hello from Bmob';
var param = {content:content_str,type:type_str};
var resultCallback = function(ret, err){
	document.getElementById("result").innerHTML = JSON.stringify(ret);
	if(err)
		api.alert(err);
}
var bmob = api.require('bmobPush');
bmob.push(param,resultCallback);
```

##补充说明

推送信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**saveLocation**<div id="a3"></div>

保存地理信息

saveLocation({params}, callback(ret, err))


##params

longitude：

- 类型：double类型
- 默认值：无
- 描述：给当前用户设定地理位置，经度，不能为空（地理坐标从其它模块获得）


latitude：

- 类型：double类型
- 默认值：无
- 描述：给当前用户设定地理位置，纬度，不能为空（地理坐标从其它模块获得）

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
{
	result:"succeed"	//操作结果
}
```
err：

- 类型：JSON对象

内部字段：

```
{
	result:"error"		//操作结果
	error:""           //操作错误描述
}
```

##示例代码

```
//设定本用户经纬度为23.56,130.12
var longitude_double = 130.12;
var latitude_double = 23.56;
var param = {latitude:latitude_double,longitude:longitude_double};
var resultCallback = function(ret, err){
	document.getElementById("result").innerHTML = JSON.stringify(ret);
	if(err)
		api.alert(err);
}
var bmob = api.require('bmobPush');
bmob.saveLocation(param,resultCallback);
```


##补充说明

调用此接口前应通过其它模块获得当前用户所在位置，再调用bmobPush模块保存，请注意检查经纬度的取值范围

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**addChannel**<div id="a4"></div>

addChannel({params})


##params

channel：

- 类型：字符串
- 默认值：无
- 描述：给当前用户添加频道（相当于给用户贴自定义标签，一个用户可以有多个标签，一个标签有多个用户），不能为空，多个频道可用；分隔


##示例代码

```
//给当前用户添加运动和教育两个频道
var channel_array = 'Sport;Education';
var param = {channel:channel_array};
var resultCallback = function(ret, err){
	document.getElementById("result").innerHTML = JSON.stringify(ret);
	if(err)
		api.alert(err);
}
var bmob = api.require('bmobPush');
bmob.addChannel(param,resultCallback);
```


##补充说明

相当于给用户贴自定义标签，一个用户可以有多个标签，一个标签有多个用户，按频道推送时用得上

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**removeChannel**<div id="a5"></div>

removeChannel({params})


##params

channel：

- 类型：字符串
- 默认值：无
- 描述：给当前用户移除出某频道（相当于给用户去掉自定义标签），不能为空，想移除多个频道可用；分隔


##示例代码

```
//给当前用户移除天气和教育两个频道
var channel_array = 'Weather;Education';
var param = {channel:channel_array};
var resultCallback = function(ret, err){
	document.getElementById("result").innerHTML = JSON.stringify(ret);
	if(err)
		api.alert(err);
}
var bmob = api.require('bmobPush');
bmob.removeChannel(param,resultCallback);
```


##补充说明

相当于给用户将原有的自定义标签删掉

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

</div>

#**Constant**<div id="const-content"></div>#

##推送类型##

push方法里面type的类型


<table>
    <tr>
        <th>类型</th>
        <th>影响的其它参数</th>
		<th>说明</th>
    </tr>
    <tr>
        <td>all</td>
        <td>无</td>
        <td>给所有用户推送</td>
    </tr>
    <tr>
        <td>channel</td>
        <td>channel</td>
        <td>给某频道的用户推送，可用；分隔</td>
    </tr>
    <tr>
        <td>ios</td>
        <td>ios_deviceToken</td>
        <td>推送给某IOS用户，ios_deviceToken为空时推送给所有IOS用户</td>
    </tr>
    <tr>
        <td>android</td>
        <td>android_installationId</td>
        <td>推送给某android用户，android_installationId为空时推送给所有android用户</td>
    </tr>
	<tr>
        <td>location</td>
        <td>latitude;longitude;distance</td>
        <td>推送给某点附近一定公里的用户</td>
    <tr>
        <td>time</td>
        <td>time</td>
        <td>推送给不活跃用户，time指定不活跃的时间，格式为yyyyMMdd或者yyyyMMddhhmmss</td>
    </tr>
</table>
