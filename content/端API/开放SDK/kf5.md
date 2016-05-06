/*
Title: kf5
Description: Domob APICloud 接口文档
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：逸创云客服</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">
</div>
<div class="outline">
[initKF5](#a1)
[showHelpCenter](#a2)
[showRequestCreation](#a3)
[showRequestList](#a4)
[setTopBarColor](#a5)
</div>

概述
=================
本模块已停止更新维护，可使用其升级版[kf5sdk](http://docs.apicloud.com/%E7%AB%AFAPI/%E5%BC%80%E6%94%BESDK/kf5sdk)

kf5提供给开发者发送工单、查看工单列表、查看知识库等功能。本模块封装了kf5的相关接口，使用此模块需先注册kf5来获取appid和hostName。注册kf5：登录kf5官网( www.kf5.com )注册kf5账号,进入控制面板 - 系统设置 - 支持渠道 - 移动APP SDK中添加一个APP以获取appid，hostName为你注册的域名，例如：kf5.kf5.com。

#**initKF5**<div id="a1"></div>
-----------------
###初始化kf5  
```javascript
initKF5({params}, callback(ret, err))  
```
###params   

hostName:  
* 类型：字符串  
* 默认值：无  
* 描述：注册后的域名，不可为空 

appId:  
* 类型：字符串  
* 默认值：无  
* 描述：注册kf5后，从后台添加APP后获取，不可为空

email:  
* 类型：字符串  
* 默认值：无  
* 描述：用户的账号，不能为空  

password:  
* 类型：字符串  
* 默认值：无  
* 描述：用户密码，可以为空。（该用户有密码时，必须填写）    

userName:  
* 类型：字符串  
* 默认值：无  
* 描述：用户的昵称，可以为空    

###callback(ret, err)  
err:  
* 类型：JSON 对象  
* 内部字段：  
{  
	message：""  //错误描述  
}  
ret:  
* 类型：JSON 对象  
* 内部字段：  
{  
	message：""  //成功描述  
}  

###补充说明  
使用此模块，必须先用initKF5进行初始化。email为用户账号，必须为email格式，如果你的kf5系统中没有该用户，则自动创建。password可不填。当为创建用户时，不填写password，则创建的用户没有密码。   
###示例代码  
```js
var param = {  
	hostName : "",  
	appId : "",  
	email : "",  
	userName : "",  
	password : ""  
};  

var kf5 = api.require('kf5');  
kf5.initKF5(param,callback); 

function callback(ret, err){  
	api.alert({  
		msg: ret.message  
	});
}
```
###可用性  
iOS系统  Android系统(SDK10及以上)  
可提供的1.0.0及更高版本  
  
#**showHelpCenter**<div id="a2"></div>
-------------
弹出kf5帮助文档页面  
```javascript
showHelpCenter({params})  
```
params  
type:  
* 类型：整型  
* 默认值：0  
* 描述：显示帮助文档的方式，为0展示分区列表(默认)，为1直接展示所有分类列表，为2直接展示所有文档列表，为3使用默			认，可以为空。  

###示例代码 
```js
var params = {  
	type: 2  
};  
        
var kf5 = api.require('kf5');  
kf5.showHelpCenter({params});
```
###补充说明  
使用此模块,必须先使用initKF5进行初始化。  
###可用性  
iOS系统  Android系统(SDK10及以上)  
可提供的1.0.0及更高版本  

#**showRequestCreation**<div id="a3"></div>
-------------
弹出kf5反馈问题页面  
```javascript
showRequestCreation()  
```
###示例代码 
```js
var kf5 = api.require('kf5');  
kf5.showRequestCreation();  
```
###补充说明  
使用此模块，必须先使用initKF5进行初始化。  
###可用性  
iOS系统  Android系统(SDK10及以上)  
可提供的1.0.0及更高版本  

#**showRequestList**<div id="a4"></div>
----------------
弹出kf5查看反馈页面  
```javascript
showRequestList()  
```
###示例代码  
```js
var kf5 = api.require('kf5');  
kf5.showRequestList(); 
```
###补充说明  
使用此模块，必须先使用initKF5进行初始化。  
###可用性  
iOS系统  Android系统(SDK10及以上)  
可提供的1.0.0及更高版本  

#**setTopBarColor**<div id="a5"></div>
-------------
设置头部nav的颜色样式  
```javascript
setTopBarColor()  
```
###示例代码  
```js
var params = {
	navColor : "",  
	titleColor :""  
}; 

var kf5 = api.require('kf5');  
kf5.setTopBarColor({params});
```
###补充说明  
使用此模块，需配合其他模块一起使用。  
###可用性  
iOS系统  Android系统(SDK10及以上)  
可提供的1.0.0及更高版本  

