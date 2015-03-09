/*
Title: qq
Description: qq
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[login](#1)

[logout](#2)

[logout](#20)

[shareText](#3)

[shareImage](#4)

[shareNews](#5)

[shareMusic](#6)

[shareVideo](#7)
</div>

#**概述**

qq封装了qq开放平台的SDK，实现了qq登陆，空间分享等大部分功能，后续将会开放获取用户信息相关接口。大大简化了把qq集成到app的流程

**使用此模块之前需先配置config文件的Feature，方法如下：**

	名称：qq
	参数：urlScheme
	描述：配置qq专用的URL Scheme，使得本应用可以启动qq客户端，并与之交换数据，同时可以从qq客户端返回到本应用
	配置示例：
               <feature name="qq">
					<param name="urlScheme" value="tencent101064640" />
					<param name="apiKey" value="101064640" />
			   </feature>
	字段描述：
		1、param-urlScheme：声明此字段为URL Scheme类型
		2、param- value：对应urlScheme类型的值。通过拼接tencent和腾讯开放平台申请的id号获得

#**login**<div id="1"></div>

登陆qq

login({parmas},callback(ret, err))

##params

apiKey：

- 类型：字符串
- 默认值：无
- 描述：从腾讯开放平台申请的app key，可为空，为空则从当前widget的config文件读取

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status: true       	//操作成功状态值
	accessToken:''      //返回token，字符串类型
	openId:''			//返回openID，字符串类型
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''    //错误描述
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

内部字段：

```js
{
    status: true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''    //错误描述
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

内部字段：

```js
{
    status: true           //操作成功状态值
    info：             //json对象，包含用户信息描述
       内部字段说明：
         city     		       //用户所在城市
         figureurl    		    //空间小头像（30）地址 
         figureurl_1    		 //空间中头像（50）地址
         figureurl_2   		    //空间大头像（100）地址
         figureurl_qq_1     	 //用户小头像（40）地址
         figureurl_qq_2    	 //用户大头像（100）地址
         gender   		       //用户性别
         is_yellow_vip        //是否为黄钻用户
         level    		       //用户账号级别
         nickname   		    //用户昵称
         province     		    //用户所在省份
         year             	    //用户出生年份
         yellow_vip_level   	 //用户账户黄钻等级
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''    //错误描述
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

分享纯文本到好友

shareText({params},callBack(ret,err))

##params

text：

- 类型：字符串
- 默认值：无
- 描述：要分享的文本，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status: true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''            //错误描述
	code：            //错误码
	       错误码说明：
	       0     		//EQQAPISENDSUCESS
          1    		//EQQAPIQQNOTINSTALLED
          2   		//EQQAPIQQNOTSUPPORTAPI
          3     		//EQQAPIMESSAGETYPEINVALID
          4    		//EQQAPIMESSAGECONTENTNULL
          5   		//EQQAPIMESSAGECONTENTINVALID
          6     		//EQQAPIAPPNOTREGISTED
          7    		//EQQAPIAPPSHAREASYNC
         -1   		//EQQAPISENDFAILD
         -4     		//用户取消分享
        10000    	//qzone分享不支持text类型分享
        10001   	//qzone分享不支持image类型分享
        10009       //当前设备未安装qq客户端       
}
```

##示例代码

```js
var obj = api.require('qq');
obj.shareText({
	text:'testtext'
});
```

##补充说明

android不支持此接口

##可用性

iOS系统

可提供的1.0.0及更高版本



#**shareImage**<div id="4"></div>

分享图片（本地）到好友

shareImage({params},callBack(ret,err))

##params

title：

- 类型：字符串
- 默认值：无
- 描述：要分享的图片标题，不能为空

description：

- 类型：字符串
- 默认值：无
- 描述：要分享的图片描述，不能为空

imgPath：

- 类型：字符串
- 默认值：无
- 描述：要分享的图片路径，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status: true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''            //错误描述
	code：            //错误码
	       错误码说明：
	       0     		//EQQAPISENDSUCESS
          1    		//EQQAPIQQNOTINSTALLED
          2   		//EQQAPIQQNOTSUPPORTAPI
          3     		//EQQAPIMESSAGETYPEINVALID
          4    		//EQQAPIMESSAGECONTENTNULL
          5   		//EQQAPIMESSAGECONTENTINVALID
          6     		//EQQAPIAPPNOTREGISTED
          7    		//EQQAPIAPPSHAREASYNC
         -1   		//EQQAPISENDFAILD
         -4     		//用户取消分享
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
- 默认值：无
- 描述：要分享的新闻链接地址，不能为空

title：

- 类型：字符串
- 默认值：无
- 描述：要分享的新闻标题，不能为空

description：

- 类型：字符串
- 默认值：无
- 描述：要分享的新闻描述，不能为空

imgUrl：

- 类型：字符串
- 默认值：无
- 描述：要分享的新闻缩略图的url（网络资源图片），不能为空

type：

- 类型：字符串
- 默认值：QZone
- 描述：分享内容到好友或空间，取值范围QZone，QFriend，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status: true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''            //错误描述
	code：            //错误码
	       错误码说明：
	       0     		//EQQAPISENDSUCESS
          1    		//EQQAPIQQNOTINSTALLED
          2   		//EQQAPIQQNOTSUPPORTAPI
          3     		//EQQAPIMESSAGETYPEINVALID
          4    		//EQQAPIMESSAGECONTENTNULL
          5   		//EQQAPIMESSAGECONTENTINVALID
          6     		//EQQAPIAPPNOTREGISTED
          7    		//EQQAPIAPPSHAREASYNC
         -1   		//EQQAPISENDFAILD
         -4     		//用户取消分享
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
- 默认值：无
- 描述：要分享的音乐链接地址，不能为空

title：

- 类型：字符串
- 默认值：无
- 描述：要分享的音乐名，不能为空

description：

- 类型：字符串
- 默认值：无
- 描述：要分享的音乐描述，不能为空

imgUrl：

- 类型：字符串
- 默认值：无
- 描述：要分享的音乐缩略图url（网络资源图片），不能为空

type：

- 类型：字符串
- 默认值：QZone
- 描述：分享内容到好友或空间，取值范围QZone，QFriend，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status: true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''            //错误描述
	code：            //错误码
	       错误码说明：
	       0     		//EQQAPISENDSUCESS
          1    		//EQQAPIQQNOTINSTALLED
          2   		//EQQAPIQQNOTSUPPORTAPI
          3     		//EQQAPIMESSAGETYPEINVALID
          4    		//EQQAPIMESSAGECONTENTNULL
          5   		//EQQAPIMESSAGECONTENTINVALID
          6     		//EQQAPIAPPNOTREGISTED
          7    		//EQQAPIAPPSHAREASYNC
         -1   		//EQQAPISENDFAILD
         -4     		//用户取消分享
        10000    	//qzone分享不支持text类型分享
        10001   	//qzone分享不支持image类型分享
        10009       //当前设备未安装qq客户端       
}
```

##示例代码

```js
var obj = api.require('qq');
obj.shareMusic({
	url:' http://y1.eoews.com/assets/ringtones/2012/6/29/36195/mx8an3zgp2k4s5aywkr7wkqtqj0dh1vxcvii287a.mp3',
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
- 默认值：无
- 描述：要分享的视频链接地址，不能为空

title：

- 类型：字符串
- 默认值：无
- 描述：要分享的视频标题，不能为空

description：

- 类型：字符串
- 默认值：无
- 描述：要分享的视频描述，不能为空

imgUrl：

- 类型：字符串
- 默认值：无
- 描述：要分享的视频缩略图路径（本地图片），不能为空

type：

- 类型：字符串
- 默认值：QZone
- 描述：分享内容到好友或空间，取值范围QZone，QFriend，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status: true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''            //错误描述
	code：            //错误码
	       错误码说明：
	       0     		//EQQAPISENDSUCESS
          1    		//EQQAPIQQNOTINSTALLED
          2   		//EQQAPIQQNOTSUPPORTAPI
          3     		//EQQAPIMESSAGETYPEINVALID
          4    		//EQQAPIMESSAGECONTENTNULL
          5   		//EQQAPIMESSAGECONTENTINVALID
          6     		//EQQAPIAPPNOTREGISTED
          7    		//EQQAPIAPPSHAREASYNC
         -1   		//EQQAPISENDFAILD
         -4     		//用户取消分享
        10000    	//qzone分享不支持text类型分享
        10001   	//qzone分享不支持image类型分享
        10009       //当前设备未安装qq客户端       
}
```

示例代码

```js
var obj = api.require('qq');
obj.shareVideo({
	url:'http://whtbj.com/wht002/data/attachment/video/201209/24/163611a3azvn0ena3vvae0.mp4',
	title:'视频',
	description:'王力宏',
	imgUrl:'widget://res/filterMe.png'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
