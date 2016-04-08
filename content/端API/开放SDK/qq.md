/*
Title: qq
Description: qq
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[installed](#0)

[login](#1)

[logout](#2)

[getUserInfo](#20)

[shareText](#3)

[shareImage](#4)

[shareNews](#5)

[shareMusic](#6)

[shareVideo](#7)
</div>

#**概述**

腾讯QQ（简称“QQ”）是腾讯公司开发的一款基于Internet的即时通信（IM）软件。腾讯QQ支持在线聊天、视频通话、点对点断点续传文件、共享文件、网络硬盘、自定义面板、QQ邮箱等多种功能，并可与多种通讯终端相连。2015年，QQ继续为用户创造良好的通讯体验！其标志是一只戴着红色围巾的小企鹅。

qq 模块封装了 qq 开放平台的移动端 SDK，开发者集成此模块可以实现登陆、获取用户信息、分享内容到 QQ 客户端等功能。登陆授权时，模块内部会先判断当前设备是否已安装 QQ 客户端，若没安装则弹出网页版登陆页面，若已安装则跳转到 QQ 客户端提示用户登陆授权。

开发者使用本模块之前需要先到[腾讯开放平台](http://open.qq.com)申请开发者账号，并在账号内填写相应信息创建自己的 APP，从而获取 APP ID。详情参考[腾讯开放平台应用接入简介](http://opensns.qq.com/apps/)

##模块使用攻略

**使用此模块之前需先配置config文件的Feature，方法如下：**

- 名称：qq
- 参数：urlScheme、apiKey
- 配置示例：

```xml
 <feature name="qq">
	<param name="urlScheme" value="tencent101064640" />
	<param name="apiKey" value="101064640" />
 </feature>
```
          
- 字段描述：
    
    **urlScheme**：（必须配置）用于实现应用间跳转及数据交换，本应用可以启动QQ客户端，也可以从QQ客户端跳回本应用。urlScheme 的 value 值是从腾讯开放平台获取的 APP ID 与 tencent 拼接而成。APP ID 申请方法参考[腾讯开放平台应用接入简介](http://opensns.qq.com/apps/)。
    
    **apiKey**：（必须配置）从腾讯开放平台获取的 APP ID，申请方法参考[腾讯开放平台应用接入简介](http://opensns.qq.com/apps/)。

##**模块接口**

#**installed**<div id="0"></div>

判断当前设备是否安装了 QQ 客户端

installed(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
       status:         	//布尔类型，是否安装了QQ客户端
}
```

##示例代码

```js
var obj = api.require('qq');
obj.installed(function(ret,err){
    if(ret.status){
       api.alert({msg: "安装"});
    }else{
        api.alert({msg: "没有安装"});
    } 
});
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**login**<div id="1"></div>

登陆qq

login({parmas},callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从腾讯开放平台申请的APP ID，为空则从当前widget的config文件读取

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true       	 //布尔类型；操作成功状态值
	accessToken:''       //字符串类型；返回token
	openId:''			 //字符串类型；返回openID
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:''             //字符串类型；错误描述
}
```

##示例代码

```js
var obj = api.require('qq');
obj.login(function(ret,err){
	api.alert({
        title: 'id和token',
		msg: ret.openId + ret.accessToken
    });
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**logout**<div id="2"></div>

登出qq

logout(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true           //布尔类型；操作成功状态值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:''                  //字符串类型；错误描述
}
```

##示例代码

```js
var obj = api.require('qq');
obj.logout(function(ret,err) {
	if (ret.status) {
		api.alert({msg:'登出成功'});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getUserInfo**<div id="20"></div>

获取用户信息

getUserInfo(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true           //布尔类型；操作成功状态值
    info:                  //JSON对象；包含用户信息描述，内部字段如下：
					        // city ：用户所在城市
					        // figureurl  ：空间小头像（30）地址 
					        // figureurl_1  ：空间中头像（50）地址
					        // figureurl_2  ：空间大头像（100）地址
					        // figureurl_qq_1  ：用户小头像（40）地址
					        // figureurl_qq_2   ：用户大头像（100）地址
					        // gender   	 ：用户性别
					        // is_yellow_vip  ：是否为黄钻用户
					        // level    	 ：用户账号级别
					        // nickname  ：用户昵称
					        // province    ：用户所在省份
					        // year    ：用户出生年份
					        // yellow_vip_level   ：用户账户黄钻等级               
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:''                 //字符串类型；错误描述
}
```

##示例代码

```js
var obj = api.require('qq');
obj.getUserInfo(function(ret,err) {
   if (ret.status) {
      api.alert({msg:'获取成功'});
   }else{
      api.alert({msg:err.msg});
   }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**shareText**<div id="3"></div>

分享纯文本到好友，**在 android 平台上此接口不支持回调**

shareText({params},callBack(ret,err))

##params

text：

- 类型：字符串
- 描述：要分享的文本

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true     //布尔类型；操作成功状态值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:''           //字符串类型；错误描述
	code：           //数字类型；错误码，错误码说明：
				      0     	//EQQAPISENDSUCESS
			          1    		//EQQAPIQQNOTINSTALLED
			          2   		//EQQAPIQQNOTSUPPORTAPI
			          3     	//EQQAPIMESSAGETYPEINVALID
			          4    		//EQQAPIMESSAGECONTENTNULL
			          5   		//EQQAPIMESSAGECONTENTINVALID
			          6     	//EQQAPIAPPNOTREGISTED
			          7    		//EQQAPIAPPSHAREASYNC
			         -1   		//EQQAPISENDFAILD
			         -4     	//用户取消分享
			        10000    	//qzone分享不支持text类型分享
			        10001   	//qzone分享不支持image类型分享
			        10009      //当前设备未安装qq客户端       
}
```

##示例代码

```js
var obj = api.require('qq');
obj.shareText({
	text:'testtext'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**shareImage**<div id="4"></div>

分享图片（本地）到好友

shareImage({params},callBack(ret,err))

##params

title：

- 类型：字符串
- 描述：要分享的图片标题

description：

- 类型：字符串
- 描述：要分享的图片描述

imgPath：

- 类型：字符串
- 描述：要分享的图片路径，要求本地路径（widget://、fs://）

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true      //布尔类型；操作成功状态值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:''            //字符串类型；错误描述
	code：            //数字类型；错误码，错误码说明：
				      0     	//EQQAPISENDSUCESS
			          1    		//EQQAPIQQNOTINSTALLED
			          2   		//EQQAPIQQNOTSUPPORTAPI
			          3     	//EQQAPIMESSAGETYPEINVALID
			          4    		//EQQAPIMESSAGECONTENTNULL
			          5   		//EQQAPIMESSAGECONTENTINVALID
			          6     	//EQQAPIAPPNOTREGISTED
			          7    		//EQQAPIAPPSHAREASYNC
			         -1   		//EQQAPISENDFAILD
			         -4     	//用户取消分享
			        10000    	//qzone分享不支持text类型分享
			        10001   	//qzone分享不支持image类型分享
			        10009       //当前设备未安装qq客户端       
}
```

##示例代码

```js
var obj = api.require('qq');
obj.shareImage({
	title:'test',
	description:'testd',
	imgPath:'widget://res/filterMe.png'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**shareNews**<div id="5"></div>

分享新闻到空间/好友

shareNews({params},callBack(ret,err))

##params

url：

- 类型：字符串
- 描述：要分享的新闻链接地址

title：

- 类型：字符串
- 描述：要分享的新闻标题

description：

- 类型：字符串
- 描述：要分享的新闻描述

imgUrl：

- 类型：字符串
- 描述：要分享的新闻缩略图的url（网络/本地资源图片），**若 type 为 QZone 则本参数在 Android 上仅支持网络图片**

type：

- 类型：字符串
- 默认值：QZone
- 描述：分享内容到好友或空间，取值范围：QZone、QFriend

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true       //布尔类型；操作成功状态值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:''            //字符串类型；错误描述
	code：            //数字类型；错误码，错误码说明：
				      0     	//EQQAPISENDSUCESS
			          1    		//EQQAPIQQNOTINSTALLED
			          2   		//EQQAPIQQNOTSUPPORTAPI
			          3     	//EQQAPIMESSAGETYPEINVALID
			          4    		//EQQAPIMESSAGECONTENTNULL
			          5   		//EQQAPIMESSAGECONTENTINVALID
			          6     	//EQQAPIAPPNOTREGISTED
			          7    		//EQQAPIAPPSHAREASYNC
			         -1   		//EQQAPISENDFAILD
			         -4     	//用户取消分享
			        10000    	//qzone分享不支持text类型分享
			        10001   	//qzone分享不支持image类型分享
			        10009       //当前设备未安装qq客户端       
}
```

##示例代码

```js
var obj = api.require('qq');
obj.shareNews({
	url:'http://www.uzmap.com',
    title:'新闻分享',
    description:'新闻描述',
	imgUrl:'http://upload.wabei.cn/2011/0807/20110807025817844.jpg'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**shareMusic**<div id="6"></div>

分享音乐到空间/好友

shareMusic({params},callBack(ret,err))

##params

url：

- 类型：字符串
- 描述：要分享的音乐链接地址

title：

- 类型：字符串
- 描述：要分享的音乐名

description：

- 类型：字符串
- 描述：要分享的音乐描述

imgUrl：

- 类型：字符串
- 描述：要分享的音乐缩略图url（网络/本地资源图片），**若 type 为 QZone 则本参数在 Android 上仅支持网络图片**

type：

- 类型：字符串
- 默认值：QZone
- 描述：分享内容到好友或空间，取值范围：QZone、QFriend

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true      //布尔类型；操作成功状态值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:''            //字符串类型；错误描述
	code：            //数字类型；错误码，错误码说明：
				      0     	//EQQAPISENDSUCESS
			          1    		//EQQAPIQQNOTINSTALLED
			          2   		//EQQAPIQQNOTSUPPORTAPI
			          3     	//EQQAPIMESSAGETYPEINVALID
			          4    		//EQQAPIMESSAGECONTENTNULL
			          5   		//EQQAPIMESSAGECONTENTINVALID
			          6     	//EQQAPIAPPNOTREGISTED
			          7    		//EQQAPIAPPSHAREASYNC
			         -1   		//EQQAPISENDFAILD
			         -4     	//用户取消分享
			        10000    	//qzone分享不支持text类型分享
			        10001   	//qzone分享不支持image类型分享
			        10009       //当前设备未安装qq客户端       
}
```

##示例代码

```js
var obj = api.require('qq');
obj.shareMusic({
	url:'http://7xq864.com1.z0.glb.clouddn.com/apicloud/591bde468d4e44b21cc225b7b6e1129a.mp3',
    title:'桔子香水',
    description:'任贤齐',
	imgUrl:'http://upload.wabei.cn/2011/0807/20110807025817844.jpg'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**shareVideo**<div id="7"></div>

分享视频到空间/好友

shareVideo({params},callBack(ret,err))

##params

url：

- 类型：字符串
- 描述：要分享的视频链接地址

title：

- 类型：字符串
- 描述：要分享的视频标题

description：

- 类型：字符串
- 描述：要分享的视频描述

imgUrl：

- 类型：字符串
- 描述：要分享的视频缩略图路径（网络/本地资源图片），**若 type 为 QZone 则本参数在 Android 上仅支持网络图片**

type：

- 类型：字符串
- 默认值：QZone
- 描述：分享内容到好友或空间，取值范围：QZone、QFriend

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true        //布尔类型；操作成功状态值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:''            //字符串类型；错误描述
	code：            //数字类型；错误码，错误码说明：
				      0     	//EQQAPISENDSUCESS
			          1    		//EQQAPIQQNOTINSTALLED
			          2   		//EQQAPIQQNOTSUPPORTAPI
			          3     	//EQQAPIMESSAGETYPEINVALID
			          4    		//EQQAPIMESSAGECONTENTNULL
			          5   		//EQQAPIMESSAGECONTENTINVALID
			          6     	//EQQAPIAPPNOTREGISTED
			          7    		//EQQAPIAPPSHAREASYNC
			         -1   		//EQQAPISENDFAILD
			         -4     	//用户取消分享
			        10000    	//qzone分享不支持text类型分享
			        10001   	//qzone分享不支持image类型分享
			        10009       //当前设备未安装qq客户端       
}
```

示例代码

```js
var obj = api.require('qq');
obj.shareVideo({
	url:'http://7xq864.com1.z0.glb.clouddn.com/apicloud/903ca10851a482ccd1383b62abb3ec5c.mp4',
	title:'视频',
	description:'王力宏',
	imgUrl:'widget://res/filterMe.png'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
