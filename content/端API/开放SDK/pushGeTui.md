/*
Title: pushGeTui
Description: pushGeTui
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#basic-content">基础接口</a></li>
	<li><a href="#extended-content">扩展接口</a></li>
	<li><a href="#advanced-content">高级接口</a></li>
</ul>
<div id="basic-content">

<div class="outline">
[initialize](#a1)

[register](#a2)
</div>

#**概述**

pushGeTui封装了个推消息推送平台的SDK，使用此模块可轻松实现服务端向客户端推送通知和透传消息的功能。

目前仅支持 Android.

###名词解释：

CID：用于标识推送目标的用户ID；CID全局唯一；同一手机不同包名的应用拥有不同的CID；正常情况下，CID会在SD卡进行存储，因此即使应用卸载重装，CID也保持不变；但SD卡缓存文件被清理的情况下，应用卸载重装CID会变更，第三方应用需要及时将最新的CID更新到第三方服务端

APPKEY/APPID：从个推平台上的获得的应用标识

###个推支持以下三种消息推送形式：

1.指定单个CID进行消息单推；

2.指定一组CID进行消息批量推送；

3.指定同一APPID下的所有CID进行全量推送。

###个推消息推送基本流程说明：

1.在个推开放平台（ http://dev.getui.com ）注册帐号，并创建应用，获取APPKEY/APPID/APPSECRET参数。具体流程常见“个推开放API配置指南”

2.在config中配置pushGeTui feature，填写上述应用参数

3.应用启动后调用initialize进行推送SDK初始化，并调用register接口注册透传消息监听器；

4.推送服务获取到推送标识CID后返回给JS层，应用一般需要将该CID和用户ID做一个绑定，记录到服务端；

5.服务端指定CID进行消息推送（可以通过个推开放平台直接操作，也可以使用服务端SDK调用消息推送接口），携带透传消息内容Payload

6.推送服务接收到消息后，通过register接口注册的消息监听器回调给JS层

7.JS层处理透传消息内容Payload，进行相应的处理。

**使用此模块之前需先配置config文件的Feature，方法如下**

	名称：pushGeTui
	参数：android_appkey,android_appid,android_appsecret,android_groupid
	描述：配置个推应用信息
```js
	<feature name="pushGeTui">
		<param name="android_appkey" value="aiMe49ehZa7IK8sevOTiY8" />
		<param name="android_appid" value="h5AH1rK4KW7vfFGZjT7fG" />
		<param name="android_appsecret" value="wx7779c7c063a9d4d9" />
		<param name="android_groupid" value="" />
	</feature>
```
字段描述:

		1.android_appkey：通过个推平台获得
		2.android_appid：应用ID，通过个推平台获得
		3.android_appsecret：通过个推平台获得
		4.android_groupid: 目前留空即可

#**initialize**<div id="a1"></div>

初始化推送服务

initialize(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"                              //操作成功状态值
	cid:"338f45b1bb06d920fbd92d93bf17e995"  // CID信息
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0       //错误码（详见错误码常量）
	msg:""       //错误描述
}
```


##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
	    	
uzgetuisdk.initialize(function(ret) {
	api.alert({msg:"cid:" + ret.cid});
});
```

##补充说明

在每次应用启动的初始化过程中，都需要调用个推SDK初始化函数。

##可用性

Android 系统

可提供的1.0.0及更高版本


#**register**<div id="a2"></div>

注册透传消息监听器

register(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"                                  //操作成功状态值
	taskid:"GT_1012_AKMw2kc2Oj5Tzy1DvXjMQA"     //消息推送任务id
	messageid:"GT_1012_AKMw2kc2Oj5Tzy1DvXjMQA"  //消息推送消息id
	payload:"any_command"                       //消息推送透传内容，第三方应用需要定义payload的格式，并进行相应的处理。建议使用json格式
}
```

err：

- 类型：JSON对象

内部字段：

```js
{

	code:0       //错误码（详见错误码常量）

	msg:""       //错误描述

}
```


##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
uzgetuisdk.register(function(ret) {
	api.alert({msg:"taskid:" + ret.taskid+" messageid:" + ret.messageid+" payload:" + ret.payload});
});
```

##补充说明

接收到服务端透传消息后，会回调通知JS代码。

##可用性

Android系统

可提供的1.0.0及更高版本
</div>


<div id="extended-content">

<div class="outline">
[setTag](#b1)

[bindAlias](#b2)

[unbindAlias](#b3)

[stopService](#b4)

[sendFeedbackMessage](#b5)

</div>

#**setTag**<div id="b1"></div>

为用户设置标签。针对单个CID设置标签（tag）列表，服务端推送可以指定标签进行定向群发

setTag({params},callback(ret, err))

##params

tags：

- 类型：字符串
- 默认值：无
- 描述：标签列表，以逗号(,)分割，标签名建议采用英文和数字的组合

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"               //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
var param = {tags:"tag1,tag2"};
uzgetuisdk.setTag(param,function(ret) {
	api.alert({msg:"setTag result:" + ret.result});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本


#**bindAlias**<div id="b2"></div>

绑定用户别名。针对单个CID设置别名，一个别名可以对应多个CID。可以指定别名进行消息推送

bindAlias({params},callback(ret, err))

##params

alias：

- 类型：字符串
- 默认值：无
- 描述：别名，建议采用英文和数字组合

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"               //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
var param = {alias:"myalias"};
uzgetuisdk.bindAlias(param,function(ret) {
	api.alert({msg:"bindAlias result:" + ret.result});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本


#**unbindAlias**<div id="b3"></div>

解绑用户别名。针对单个CID取消设置别名。

unbindAlias({params},callback(ret, err))

##params

alias：

- 类型：字符串
- 默认值：无
- 描述：别名，建议采用英文和数字组合

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"               //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
var param = {alias:"myalias"};
uzgetuisdk.unbindAlias(param,function(ret) {
	api.alert({msg:"unbindAlias result:" + ret.result});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本


#**stopService**<div id="b4"></div>

完全停止SDK的服务。停止推送服务，停止所有业务逻辑

stopService(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"               //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
uzgetuisdk.stopService(function(ret) {
	api.alert({msg:"stopService result:" + ret.result});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本


#**sendFeedbackMessage**<div id="b5"></div>

上行第三方自定义回执。第三方指定自定义actionid，便于对推送效果做统计分析。

sendFeedbackMessage({params},callback(ret, err))

##params

taskid：

- 类型：字符串
- 默认值：无
- 描述：接收的透传消息任务id

messageid：

- 类型：字符串
- 默认值：无
- 描述：接收的透传消息id

actionid：

- 类型：int
- 默认值：无
- 描述：自定义动作id，范围为90001-90999。第三方可以对支付、页面访问等用户操作进行打点。

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"               //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
var param = {taskid:"GT_1012_AKMw2kc2Oj5Tzy1DvXjMQA",messageid:"GT_1012_AKMw2kc2Oj5Tzy1DvXjMQA",actionid:90001};
uzgetuisdk.sendFeedbackMessage(param,function(ret) {
	api.alert({msg:"sendFeedbackMessage result:" + ret.result});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本

</div>
<div id="advanced-content">

<div class="outline">

[turnOnPush](#c1)

[turnOffPush](#c2)

[isPushTurnedOn](#c3)

[getVersion](#c4)

[setSilentTime](#c5)

[sendMessage](#c6)

</div>


#**turnOnPush**<div id="c1"></div>

开启Push推送。继续服务端连接。常见turnOffPush

turnOnPush(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"               //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
uzgetuisdk.turnOnPush(function(ret) {
	api.alert({msg:"turnOnPush result:" + ret.result});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本


#**turnOffPush**<div id="c2"></div>

关闭Push推送。暂停服务端连接，即使调用initialize也不会继续服务端连接。

turnOffPush(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"               //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
uzgetuisdk.turnOffPush(function(ret) {
	api.alert({msg:"turnOffPush result:" + ret.result});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本


#**isPushTurnedOn**<div id="c3"></div>

获取当前推送服务开关状态。该状态只和turnOnPush和turnOffPush操作相关

isPushTurnedOn(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"                   //操作成功状态值
	isOn:"true"                  //推送服务状态
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
uzgetuisdk.isPushTurnedOn(function(ret) {
	api.alert({msg:"isPushTurnedOn result:" + ret.isOn});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本


#**getVersion**<div id="c3"></div>

获取SDK版本号。

getVerison(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"                    //操作成功状态值
	version:"2.3.0.0.apicloud"    //SDK版本号
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
uzgetuisdk.getVersion(function(ret) {
	api.alert({msg:"getVersion result:" + ret.version});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本



#**setSilentTime**<div id="c4"></div>

设置SDK静默时间。在指定时间段内，暂停推送服务联网，可以避免用户打扰，同时起到省电省流量的作用。

setSilentTime({params},callback(ret, err))

##params

beginHour：

- 类型：int
- 默认值：无
- 描述：静默时间段开始时间点，单位小时，取值范围：0-23

duration：

- 类型：int
- 默认值：无
- 描述：静默时间段持续时间，单位小时，取值范围：0-24

解释说明：
- 例如：beginHour=9、duration=12，含义为早9点到晚9点之间静默
- 例如：beginHour=21、duration=12，含义为晚9点到早9点之间静默

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"               //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
var param = {beginHour:9,duration:12};
uzgetuisdk.setSilentTime(param,function(ret) {
	api.alert({msg:"setSilentTime result:" + ret.result});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本



#**sendMessage**<div id="c5"></div>

发送上行消息，服务端使用MMP SDK接收客户端发送的上行消息。

sendMessage({params},callback(ret, err))

##params

taskid：

- 类型：字符串
- 默认值：无
- 描述：由客户端生成的上行消息任务id，便于后续跟踪消息

extraData：

- 类型：字符串
- 默认值：无
- 描述：上行消息内容，由客户端自行定义，建议采用json格式

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:"0"               //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ""      //错误描述
}
```

##示例代码

```js
var uzgetuisdk = api.require('pushGeTui');
var param = {taskid:"SX_1111_ABCDEFG",extraData:"any_command"};
uzgetuisdk.sendMessage(param,function(ret) {
	api.alert({msg:"sendMessage result:" + ret.result});
});
```

##补充说明

（暂无）

##可用性

Android系统

可提供的1.0.0及更高版本


</div>
