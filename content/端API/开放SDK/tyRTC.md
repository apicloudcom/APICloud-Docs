/*
Title: tyRTC
Description: tyRTC
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#init-content">初始化设置类接口</a></li>
	<li><a href="#single-content">点对点通信类接口</a></li>
	<li><a href="#constt-content">常量</a></li>
</ul>
<div id="init-content">

<div class="outline">
[setAppKeyAndAppId](#a1)

[login](#a2)

[logout](#a3)

[setGlobalStatusListener](#a4)

[setLogStatusListener](#a5)

[setCallStatusListener](#a6)

[setRemotePicPathListener](#a7)

[setMessageListener](#a8)
</div>

#**概述**

天翼RTC平台运行在公共互联网上，定位于纯互联网方式提供OTT实时通信服务的通信能力平台，未来将与中国电信的IMS/软交换/PSTN等网络通信系统互通。为客户端应用提供应用内、应用间的语音、视频和数据实时通信沟通(初期主要提供语音和视频沟通)，其应用接口包括：，面向PC、Pad和手机终端以及Web应用前端，支持多种编程语言和终端平台的SDK(包括Android、iOS和JS SDK)； 面向第三方应用前端以及服务器后台发起的REST API (如在页面发起两个终端应用间的IP语音呼叫)。
tyRTC模块封装了天翼RTC平台的SDK，使用此模块可轻松实现点对点音视频通话、多人语音视频通话、IM消息的功能。

天翼RTC平台官方网站：[http://www.chinartc.com/dev/](http://www.chinartc.com/dev/)

天翼RTC开发者支持QQ群：172898609

天翼RTC公有云咨费标准：[http://www.chinartc.com/dev/rtcweb/price.html](http://www.chinartc.com/dev/rtcweb/price.html)

#**准备工作**
**在RTC开放者门户或者集成RTC能力的开放平台门户上注册开发者资料，提交并接受平台审核，审核通过将成为开发者并获得开发者帐号。（目前门户暂未对外开放，而是采用RTC后台分配方式注册开发者）
系统将自动分配AccountId和AppKey，AccountId将会和SDK配置时使用。**


**iOS平台使用此模块之前需先配置config文件的Feature，方法如下**

- 名称：tyRTC
- 参数：enablelog
- 描述：是否允许生成log，1为打开，0为关闭。开启后会在控制台输出RTC的log信息，并且保存在应用沙盒内，方便开发者调试，建议正式发布时关闭log。
- 配置示例:

```js
  <feature name="tyRTC">
    <param name="enablelog" value="0" />
  </feature>
```

#**setAppKeyAndAppId**<div id="a1"></div>

设置应用程序的appKey和appId

setAppKeyAndAppId({params})

##params

appId：

- 类型：字符串
- 默认值：无
- 描述：从RTC平台申请的appid，不能为空

appKey：

- 类型：字符串
- 默认值：无
- 描述：从RTC平台申请的appkey，不能为空

##示例代码

```js
var setparam = {
    appId:"70038",
    appKey:"MTQxMDkyMzU1NTI4Ng=="
};
var demo = api.require('tyRTC');
demo.setAppKeyAndAppId(setparam);
```

##补充说明

在登录之前需要先调用此接口设置appId和appKey

##可用性

iOS系统，Android系统

#**login**<div id="a2"></div>

初始化RTC客户端，并注册至RTC平台

login({params})

##params

jsonViewConfig：

- 类型：字符串
- 默认值：无
- 描述：通话视频窗口位置和大小数据，不能为空，为一个json字符串，格式为：
   {localView = {x, y, w, h}, remoteView = {x, y, w, h}}，"localView"表示本地窗口配置信息，"remoteView"表示远程窗口配置信息，"x"表示窗口起始x坐标，"y"表示窗口起始y坐标，"w"表示窗口宽度，"h"表示窗口高度。视频窗口在发起视频呼叫或接听视频来电时创建。

username：

- 类型：字符串
- 默认值：无
- 描述：本地用户账号，不能为空，账号不可包含“~”、空格、中文字符

##示例代码

```js
var jsonObj1 = {};
jsonObj1.x = 55;
jsonObj1.y = 240;
jsonObj1.w = 130;
jsonObj1.h = 170;
var jsonObj2 = {};
jsonObj2.x = 190;
jsonObj2.y = 240;
jsonObj2.w = 130;
jsonObj2.h = 170;
var json = {};
json.localView = jsonObj1;
json.remoteView = jsonObj2;
var setparam = {
    jsonViewConfig:JSON.stringify(json),
    userName:"5668"
};
var demo = api.require('tyRTC');
demo.login(setparam);
```

##补充说明

登录结果返回至cbLogStatus回调函数

##可用性

iOS系统，Android系统

#**logout**<div id="a3"></div>

退出RTC平台

logout()

##示例代码

```js
var demo = api.require(‘tyRTC’);
demo.logout();
```

##补充说明

注销结果返回至cbLogStatus回调函数

##可用性

iOS系统，Android系统

#**setGlobalStatusListener**<div id="a4"></div>

设置回调函数，监听客户端全局状态

setGlobalStatusListener(onGlobalStatus(data))

##onGlobalStatus(data)

data：

- 类型：字符串
- 描述：返回客户端实时状态，详情如下：
       "ClientListener:onInit,result=":result为初始化结果
       "获取token: reason:":获取token结果，reason为失败原因
       "DeviceListener:onNewCall,call=":有新来电，call为来电信息，其中"ci"为对方携带的呼叫信息，"t"为呼叫类型（1：音频，3：音+视频），"dir"为呼叫方向（1：去电，2：来电），"uri"为对方账号
       "ConnectionListener:onConnecting":通话请求连接中
       "ConnectionListener:onConnected":通话已接通
       "ConnectionListener:onDisconnect,code=":通话连接中断，code为错误码
       "StateChanged,result=200":登录成功
       "StateChanged,result=-1001":没有网络
       "StateChanged,result=-1002":切换网络
       "StateChanged,result=-1003":网络较差
       "StateChanged,result=-1004":重连失败需要重新登录
       "StateChanged,result=-1500":同一账号在多个终端登录被踢下线
       "StateChanged,result=-1501":同一账号在多个设备类型登录
       "call hangup":主动挂断
	   "onReceiveIm:from:,msg:":接收到文本消息，from为发送账号，msg为消息内容

##示例代码

```js
var demo = api.require(‘tyRTC’);
demo.setGlobalStatusListener(onGlobalStatus); 
                                
function onGlobalStatus(data){
  alert(data);
}
```

##补充说明

可在登录之前调用此接口设置回调函数

##可用性

iOS系统，Android系统

#**setLogStatusListener**<div id="a5"></div>

设置客户端注册至RTC平台的回调函数

setLogStatusListener(cbLogStatus(data))

##cbLogStatus(data)

data：

- 类型：字符串
- 描述：返回客户端注册至RTC平台的结果，详情如下：
       “OK:LOGIN”:登录成功
       “OK:LOGOUT”:退出成功 
       “ERROR:PARM_ERROR”:登录参数有误 
       “ERROR:UNINIT”:RTC平台未初始化 
       “ERROR:error_msg”:error_msg为其他错误信息，如获取token失败

##示例代码

```js
var demo = api.require(‘tyRTC’);
demo.setLogStatusListener(cbLogStatus); 
                                
function cbLogStatus(data){
  alert(data);
}
```

##补充说明

可在登录之前调用此接口设置回调函数

##可用性

iOS系统，Android系统

#**setCallStatusListener**<div id="a6"></div>

设置呼叫状态的回调函数

setCallStatusListener(cbCallStatus(data))

##cbCallStatus(data)

data：

- 类型：字符串
- 描述：返回呼叫的结果，详情如下：
       “OK:NORMAL”：正常状态（未通话，也无来电）
       “OK:INCOMING”：有来电，等待接听
       “OK:CALLING”：呼叫中
       “ERROR:PARM_ERROR”：呼叫参数有误
       “ERROR:UNREGISTER”：未注册至RTC平台

##示例代码

```js
var demo = api.require(‘tyRTC’);
demo.setCallStatusListener(cbCallStatus); 
                                
function cbCallStatus(data){
  alert(data);
}
```

##补充说明

可在登录之前调用此接口设置回调函数

##可用性

iOS系统，Android系统

#**setRemotePicPathListener**<div id="a7"></div>

设置截屏的回调函数

setRemotePicPathListener(cbRemotePicPath(data))

##cbRemotePicPath(data)

data：

- 类型：字符串
- 描述：返回截屏图片存储的路径
}

##示例代码

```js
var demo = api.require(‘tyRTC’);
demo.setRemotePicPathListener(cbRemotePicPath); 
                                
function cbRemotePicPath(data){
  alert(data);
}
```

##补充说明

可在登录之前调用此接口设置回调函数

##可用性

iOS系统，Android系统

#**setMessageListener**<div id="a8"></div>

设置回调函数，监听文本消息状态

setMessageListener(cbMessageStatus(data))

##cbMessageStatus(data)

data：

- 类型：字符串
- 描述：返回收发文本消息状态，详情如下：
	   "OK:SEND":发送文本消息成功
       "ERROR:code":发送文本消息失败，code为错误码
       "OK:RECEIVE":接收文本消息成功

##示例代码

```js
var demo = api.require(‘tyRTC’);
demo.setMessageListener(cbMessageStatus); 
                                
function cbMessageStatus(data){
  alert(data);
}
```

##补充说明

可在登录之前调用此接口设置回调函数

##可用性

iOS系统，Android系统
</div>

<div id="single-content">

<div class="outline">
[call](#b1)

[acceptCall](#b2)

[hangUp](#b3)

[mute](#b4)

[loudSpeaker](#b5)

[setVideoAttr](#b6)

[takeRemotePicture](#b7)

[sendMessage](#b8)

[switchCamera](#b9)

[rotateCamera](#b10)

[switchView](#b11)
</div>

#**call**<div id="b1"></div>

创建呼叫

call({params})

##params

callType：

- 类型：整数
- 默认值：无
- 描述：呼叫类型，不能为空。1：音频，2：音+视频，3：音+视频单向接收，4：音+视频单向发送

callName：

- 类型：字符串
- 默认值：无
- 描述：远端账号，不能为空。账号不可包含“~”、空格、中文字符

callInfo：

- 类型：字符串
- 默认值：无
- 描述：应用自定义传递的字符串，如昵称等。不可包含逗号，可以为空。

##示例代码

```js
var param = {
    callType:2,
    callName:"8889",
	callInfo:"myName"
};
var demo = api.require(‘tyRTC’);
demo.call(param);
```

##补充说明

结果上报至cbCallStatus回调函数

##可用性

iOS系统，Android系统

#**acceptCall**<div id="b2"></div>

接听呼叫

acceptCall({params})

##params

callType：

- 类型：整数
- 默认值：无
- 描述：接听类型，不能为空。1：音频，2：音+视频，3：音+视频单向接收，4：音+视频单向发送

##示例代码

```js
var param = {
    callType:2
};
var demo = api.require(‘tyRTC’);
demo.acceptCall(param);
```

##补充说明

结果上报至cbCallStatus回调函数

##可用性

iOS系统，Android系统

#**hangUp**<div id="b3"></div>

挂断呼叫或通话

hangUp()

##示例代码

```js
var demo = api.require(‘tyRTC’);
demo.hangUp();
```

##补充说明

结果上报至cbCallStatus回调函数

##可用性

iOS系统，Android系统

#**mute**<div id="b4"></div>

设置静音/取消静音

mute({params})

##params

value：

- 类型：字符串
- 默认值：无
- 描述：静音：”true”，取消静音：”false”

##示例代码

```js
var muteparam = {
    value:"true"
};
var demo = api.require(‘tyRTC’);
demo.mute(muteparam);
```

##补充说明

无

##可用性

iOS系统，Android系统

#**loudSpeaker**<div id="b5"></div>

设置扬声器/电话听筒

loudSpeaker({params})

##params

value：

- 类型：字符串
- 默认值：无
- 描述：扬声器：”true”，电话听筒：”false”

##示例代码

```js
var param = {
    value:"true"
};
var demo = api.require(‘tyRTC’);
demo.loudSpeaker(param);
```

##补充说明

无

##可用性

iOS系统，暂不支持Android系统

#**setVideoAttr**<div id="b6"></div>

设置视频清晰度

setVideoAttr({params})

##params

value：

- 类型：整数
- 默认值：无
- 描述：视频分辨率。0：标清；1：流畅；2：高清

##示例代码

```js
var param = {
    value:0
};
var demo = api.require(‘tyRTC’);
demo.setVideoAttr(param);
```

##补充说明

无

##可用性

iOS系统，Android系统

#**takeRemotePicture**<div id="b7"></div>

截取远端画面

takeRemotePicture()

##示例代码

```js
var demo = api.require(‘tyRTC’);
demo.takeRemotePicture();
```

##补充说明

无

##可用性

iOS系统，Android系统

#**sendMessage**<div id="b8"></div>

发送文本消息

sendMessage({params})

##params

userName：

- 类型：字符串
- 默认值：无
- 描述：远端账号，不能为空。账号不可包含“~”、空格、中文字符

msg：

- 类型：字符串
- 默认值：无
- 描述：文本消息，不能为空。

##示例代码

```js
var demo = api.require(‘tyRTC’);
var param = {
    userName:@"8889",
    msg:"Hello RTC!"
};
demo.sendMessage(param);
```

##补充说明

结果上报至cbMessageStatus回调函数

##可用性

iOS系统，Android系统

#**switchCamera**<div id="b9"></div>

切换摄像头

switchCamera({params})

##params

value：

- 类型：字符串
- 默认值：无
- 描述：前置摄像头：”front”，后置摄像头：”back”

##示例代码

```js
var param = {
    value:"back"
};
var demo = api.require(‘tyRTC’);
demo.switchCamera(param);
```

##补充说明

无

##可用性

iOS系统，Android系统

#**rotateCamera**<div id="b10"></div>

旋转摄像头

rotateCamera({params})

##params

value：

- 类型：整数
- 默认值：无
- 描述：画面逆时针旋转。0：旋转0度；1：旋转90度；2：旋转180度，3：旋转270度

##示例代码

```js
var param = {
    value:1
};
var demo = api.require(‘tyRTC’);
demo.rotateCamera(param);
```

##补充说明

无

##可用性

iOS系统，Android系统

#**switchView**<div id="b11"></div>

交换本地与远端视频画面

switchView()

##示例代码

```js
var demo = api.require(‘tyRTC’);
demo.switchView();
```

##补充说明

无

##可用性

iOS系统，Android系统
</div>

<div id="constt-content">

<div class="outline">

[错误码](#c1)
</div>

#**错误码**<div id="c1"></div>

错误类型

##取值范围：

- 400   //请求类错误4xx的下界
- 403   //禁止 token失效，请重新获取token，重新注册
- 404   //呼叫的号码不存在，请检查号码格式是否正确（例如10-18901012345~123~Phone）
- 408   //超时，请求服务器超时或被呼叫方网络异常
- 480   //对方不在线，对方未登陆，或网络异常断开一段时间
- 486   //正忙
- 487   //取消呼叫
- 488   //媒体协商失败
- 500   //服务器类错误5xx的下界
- 503   //网络不可用或服务器错误
- 600   //全局错误6xx的下界
- 603   //被叫拒接，或服务器拒绝请求
- 891   //已经在其他地方接听
- 1001  //内存错误
- 1002  //参数错误
- 1003  //缺少参数
- 1004  //重置参数失败
- 1005  //呼叫失败
- 1006  //呼叫结束
- 1007  //动作失败
- 1008  //sdk已初始化
- 1009  //sdk初始化不完整
- 1010  //容量溢出
- 1011  //无效函数


</div>
