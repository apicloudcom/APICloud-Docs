/*
Title: kf5sdk
Description: kf5sdk
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	
</ul>

<div class="outline">
[initKF5](#a1)
[showHelpCenter](#a2)
[showRequestCreation](#a3)
[showRequestList](#a4)
[showChatView](#a6)
[setTopBarColor](#a5)
</div>


##概述

kf5提供给开发者发送工单、查看工单列表、查看知识库等功能。本模块封装了kf5的相关接口，使用此模块需先注册kf5来获取appid和hostName。注册kf5：登录kf5官网( www.kf5.com )注册kf5账号,进入控制面板 - 系统设置 - 支持渠道 - 移动APP SDK中添加一个APP以获取appid，hostName为你注册的域名，例如：kf5.kf5.com。

#**initKF5**<div id="a1"></div> 

初始化kf5  

initKF5({params},callback(ret,err))  

###params   

hostName:  

- 类型：字符串  
- 描述：注册后的域名

appId:  

- 类型：字符串  
- 描述：注册kf5后，从后台添加APP后获取

email:  

- 类型：字符串  
- 描述：用户的账号 

appName:  

- 类型：字符串  
- 描述：（可选项）应用名称
- 默认值：IOSAPP/AndroidAPP

deviceToken:  

- 类型：字符串  
- 描述：（可选项）应用推送的deviceToken

userName: 
 
- 类型：字符串  
- 描述：（可选项）用户的昵称 

phone:  

- 类型：字符串  
- 描述：（可选项）用户的电话

###callback(ret,err)  

err:  

- 类型：JSON对象  
- 内部字段：  

```js
{  
	message：""  //错误描述  
}  
```

ret:  

- 类型：JSON对象  
- 内部字段：  

```js
{  
	message：""  //成功描述  
}  
```

###补充说明  

使用此模块，必须先用initKF5进行初始化。email为用户账号，必须为email格式，如果你的kf5系统中没有该用户，则自动创建。password可不填。当为创建用户时，不填写password，则创建的用户没有密码。   

###示例代码  

```javascript
var param = {  
	hostName : "",  
	appId : "",  
	email : "",  
	userName : "",  
	phone : ""  
};  
var kf5 = api.require('kf5sdk');  
kf5.initKF5(param,callback); 
function callback(ret,err){  
	api.alert({  
		msg: ret.message  
	});
}  
```
###可用性  

iOS系统  Android系统(SDK10及以上)  

可提供的1.0.0及更高版本  


#**showHelpCenter**<div id="a2"></div>  

弹出kf5帮助文档页面  

showHelpCenter({params})  

###params  

type:  

- 类型：数字  
- 默认值：0  
- 描述：（可选项）显示帮助文档的方式，为0展示分区列表(默认)，为1直接展示分区列表，为2直接展示所有分类列表，为3直接展示所有文档列表 

###示例代码 

```javascript
var params = {  
	type: 0  
};   
var kf5 = api.require('kf5sdk');  
kf5.showHelpCenter(params);  
```
###补充说明  

使用此接口,必须先使用initKF5进行初始化。 
 
###可用性  

iOS系统  Android系统(SDK10及以上)  

可提供的1.0.0及更高版本  


#**showRequestCreation**<div id="a3"></div> 

弹出kf5反馈问题页面  

showRequestCreation()  

###示例代码 

```javascript
var kf5 = api.require('kf5sdk');  
kf5.showRequestCreation();  
```

###补充说明 
 
使用此接口，必须先使用initKF5进行初始化。  

###可用性  

iOS系统  Android系统(SDK10及以上)  

可提供的1.0.0及更高版本  


#**showRequestList**<div id="a4"></div>  

弹出kf5查看反馈页面  

showRequestList()  

###示例代码  

```javascript
var kf5 = api.require('kf5sdk');  
kf5.showRequestList(); 
```

###补充说明  

使用此接口，必须先使用initKF5进行初始化。  

###可用性  

iOS系统  Android系统(SDK10及以上)  

可提供的1.0.0及更高版本  


#**showChatView**  <div id="a6"></div> 

弹出kf5即时交谈 

showChatView(callback())  

###params

isHideRightButton:  

- 类型：布尔值  
- 描述：（可选项）是否隐藏右侧按钮,Android不可用
- 默认值：flase  

isShowAlertWhenNoAgent: 
 
- 类型：布尔值  
- 描述：（可选项）当没有客服在线时是否弹出alertView,Android不可用
- 默认值：true  

noAgentAlertShowTitle: 
 
- 类型：字符串  
- 描述：（可选项）当没有客服在线时,弹出alertView显示的title,Android不可用
- 默认值："当前没有客服在线,请提交留言"  

ratingAlertTitle:  

- 类型：字符串  
- 描述：（可选项）当客服请求进行满意度评价时的提示文字,Android不可用  
- 默认值："感谢使用我们的服务,请为此次服务评价:"  

ratingFinishSystemTitle: 
 
- 类型：字符串  
- 描述：（可选项）当用户点击评价后的系统提示文字,Android不可用  
- 默认值："感谢您的评价!"  

connectingShowTitle:  

- 类型：字符串  
- 描述：（可选项）正在连接服务器时nav导航栏显示的文字,Android不可用
- 默认值："正在连接..." 

connectErrorShowTitle: 
 
- 类型：字符串  
- 描述：（可选项）连接服务器失败时nav导航栏显示的文字,Android不可用
- 默认值："未连接"

getAgentingShowTitle:  

- 类型：字符串  
- 描述：（可选项）正在分配客服时nav导航栏显示的文字,Android不可用
- 默认值："正在分配客服..."

noAgentShowTitle: 
 
- 类型：字符串  
- 描述：（可选项）当分配客服失败时nav导航栏显示的文字,Android不可用
- 默认值："当前没有客服在线"

chatEndShowTitle:  

- 类型：字符串  
- 描述：（可选项）当客服结束会话时nav导航栏显示的文字,Android不可用
- 默认值："对话已结束"

###callback() 
 
当没有客服在线弹出 alertView，点击"确定"按钮的事件处理，默认跳转到反馈工单界面，Android不可用

###示例代码  

```javascript
var params = {
isShowAlertWhenNoAgent  : true, 
noAgentAlertShowTitle   : "当前没有客服在线,请提交留言",
ratingAlertTitle        : "感谢使用我们的服务,请为此次服务评价:",
ratingFinishSystemTitle : "感谢您的评价!",
connectingShowTitle     : "正在连接...",
connectErrorShowTitle   : "未连接", 
getAgentingShowTitle    :"正在分配客服...",
noAgentShowTitle        : "当前没有客服在线", 
chatEndShowTitle        : "会话已结束"
}; 
var noAgentAlertActionCallback = function(){
api.toast({
msg:"当前没有客服在线"
});
};
var kf5 = api.require('kf5sdk');  
kf5.showChatView(params,noAgentAlertActionCallback); 
```

###补充说明  

使用此接口，必须先使用initKF5进行初始化。 
 
###可用性  

iOS系统  Android系统(SDK10及以上)  

可提供的1.0.0及更高版本 



#**setTopBarColor**<div id="a5"></div>

设置头部nav的颜色样式  

setTopBarColor()  


###params

navColor:  

- 类型：字符串  
- 描述：（可选项）头部nav背景颜色
- 默认值：#3E4245  

textColor:  

- 类型：字符串   
- 描述：（可选项）头部nav TextView字体颜色
- 默认值：#FFFFFF 

centerTextSize:  

- 类型：整型  
- 描述：（可选项）头部Nav 中间Textview字体大小
- 默认值：22  

rightTextSize:  

- 类型：整型  
- 描述：（可选项）头部Nav 右侧TextView字体大小,IOS不可用
- 默认值：20  

centerTextVisible:  

- 类型：布尔型  
- 描述：（可选项）头部Nav中间TextView是否可见,IOS不可用
- 默认值：true  

rightTextVisible:  

- 类型：布尔型  
- 描述：（可选项）头部Nav右侧TextView是否可见,IOS不可用
- 默认值：true  

backImgSrc:  

- 类型：字符串  
- 描述：头部Nav 左侧返回按钮的资源路径,IOS不可用


###示例代码  

```javascript
var params = {
navColor            :"#3E4245", 
textColor           :"#FFFFFF", 
centerTextSize      : 22,
rightTextSize       : 20,
centerTextVisible   : true,	
rightTextVisible    : true,
backImgSrc          : api.wgtRootDir +"/image/refresh.png"
}; 
var kf5 = api.require('kf5sdk');  
kf5.setTopBarColor(params);  
```
###补充说明  

使用此接口，需配合其他接口一起使用。 
 
###可用性  

iOS系统  Android系统(SDK10及以上)  

可提供的1.0.0及更高版本   

