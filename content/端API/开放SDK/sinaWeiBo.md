/*
Title: sinaWeiBo
Description: sinaWeiBo
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[auth](#1)

[cancelAuth](#2)

[sendRequest](#3)

[getUserInfo](#4)
</div>

#**概述**

sinaWeiBo封装了新浪微博开放平台的sdk，使用此模块可实现新浪登陆、分享消息到新浪微博账号等功能。大大缩短了新浪微博集成到app的流程，更加方便快捷

**使用此模块之前需先配置config文件的Feature，方法如下：**

	名称：sinaWeiBo
	参数：urlScheme
	描述：配置新浪微博专用的URL Scheme，使得本应用可以启动新浪微博客户端，并与之交换数据，同时可以从新浪微博客户端返回到本应用
	配置示例：
      <feature name="sinaWeiBo">
        <param name="urlScheme" value="wb1132217156" />
        <param name="apiKey" value="1132217156" />
        <param name="registUrl" value="http://www.apicloud.com" />
      </feature>
	字段描述：
		1、param-urlScheme：声明此字段为URL Scheme类型
		2、param-value：对应urlScheme类型的值。通过新浪微博开放平台申请appId，再加上‘wb’前缀构成
		3、param-apiKey：声明此字段为apiKey类型
		4、param-value：对应从新浪开放平台申请的appKey
		5、param-registUrl：声明此字段为registUrl类型
		6、param-value：对应在新浪开放平台申appkey时填写的的回调url

#**auth**<div id="1"></div>

授权

auth({params},callback(ret, err))

##params

apiKey：

- 类型：字符串
- 默认值：无
- 描述：从新浪开放平台申请的key，可为空，若为空则从当前widget的config文件读取

registUrl：

- 类型：字符串
- 默认值：无
- 描述：在新浪开放平台填写的回调url，可为空，若为空则从当前widget的config文件读取

isAuth：

- 类型：布尔
- 默认值：true
- 描述：是否登录授权，可为空，若为false则仅注册，分享消息只需注册，获取用户信息需登录授权

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
	accessToken:''        //token字符串
	userID:''             //userID字符串
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0      //错误码（详见错误码常量）
    msg:""      //错误描述
}
```

##示例代码

```js
var sinaWeiBo = api.require('sinaWeiBo');
sinaWeiBo.auth(function(ret,err){
    if (ret.status) {
		api.alert({
            title: '微博授权',
            msg: '授权成功'
        });
    }else{
		api.alert({msg:'授权失败'+err.msg});
    }
});
```

##补充说明

授权

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**cancelAuth**<div id="2"></div>

登出当前账号

cancelAuth(callback(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg: ""    //错误描述
}
```

##示例代码

```js
var sinaWeiBo = api.require('sinaWeiBo');
sinaWeiBo.cancelAuth(function(ret,err){
	if(ret.status){
		api.alert({msg:'登出成功'});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

登出当前已授权账号

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**sendRequest**<div id="3"></div>

发表内容

sendRequest({params}, callback(ret, err))

##params

contentType：

- 类型：字符串
- 默认值：无
- 描述：发表的内容类型（详见[内容类型](!Constant)常量），不能为空

text：

- 类型：字符串
- 默认值：无
- 描述：文本内容，contentType为text时不能为空

imageUrl：

- 类型：字符串
- 默认值：无
- 描述：图片url地址，仅支持本地图片，contentType为image时不能为空

media：

- 类型：JSON对象
- 默认值：无
- 描述：多媒体内容，contentType为text或image时可以为空

内部参数：

```js
{
	title：			//多媒体标题，字符串类型，不能为空
	description：	    //多媒体描述，字符串类型，不能为空
	thumbUrl：		    //多媒体缩略图本地路径，字符串类型，不能为空
	musicUrl：		    //音乐网页url，字符串类型，contentType为music时不能为空
	videoUrl：		    //视频网页url，字符串类型，contentType为video时不能为空
	webpageUrl：		//网页url，字符串类型，contentType为web_page时不能为空
}
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0    //错误码（详见错误码常量）
    msg:""    //错误描述
};
```

##示例代码

```js
//当contentType为music,video或webpage时，内容地址不能为流媒体地址;
var sinaWeiBo = api.require('sinaWeiBo');
sinaWeiBo.sendRequest({
    contentType: 'video',
    text: '这里是测试的内容',
    imageUrl: 'fs://a.png',
    media: {
        title: '多媒体标题',
        description: '多媒体描述',
        thumbUrl: 'fs://b.png',
        videoUrl: 'http://v.ku6.com/show/ZgeIWrUgvfSuDN_fl_qNsQ...html'
    }
},function(ret,err){
    if (ret.status) {
		api.alert({
            title: '发表微博',
            msg: '发表成功',
            buttons: ['确定']
        });
    }else{
		api.alert({
            title: '发表失败',
            msg: err.msg,
            buttons: ['确定']
        });
    };
});
//当contentType为text或image时，多媒体内容可以为空;
var sinaWeiBo = api.require('sinaWeiBo');
sinaWeiBo.sendRequest({
    contentType: 'text',
    text: '这是测试用的文本',
    imageUrl: 'fs://a.png'
},function(ret,err){
    if (ret.status) {
		api.alert({
            title: '发表微博',
            msg: '发表成功',
            buttons: ['确定']
        });
    }else{
		api.alert({
            title: '发表微博',
            msg: '发表失败',
            buttons: ['确定']
		});
    };
});
```

##补充说明

由于新浪微博SDK目前暂不完全支持iPad分享，发表音乐、视频等内容时有可能不成功

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getUserInfo**<div id="4"></div>

获取用户账户信息

getUserInfo({params}, callback(ret, err))

##params

token：

- 类型：字符串
- 默认值：当前已登录账号的token
- 描述：登录账号获取的token值，可为空

uid：

- 类型：字符串
- 默认值：当前已登录账号的userid
- 描述：登录账号获取的userid，可为空


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:true           //操作成功状态值
	 userInfo:''           //获取的用户信息，json对象
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
};
```

##示例代码

```js
var sinaWeiBo = api.require('sinaWeiBo');sinaWeiBo.getUserInfo(function(ret,err){    if (ret.status) {        api.alert({msg: '获取成功'});    }else{        api.alert({msg:err.msg});    }});
```

##补充说明

需先登录

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

</div>


<div id="const-content">

<div class="outline">
[内容类型](#a1)

[错误码](#a2)
</div>

#**内容类型**<div id="a1"></div>

内容类型

##取值范围：

- text		//文本
- image		//图片
- music		//音乐
- video		//视频
- web_page		//网页


#**错误码**<div id="a2"></div>

错误类型

##取值范围：

- 0		//没有错误
- 1		//用户取消
- 2		//发送失败
- 3		//授权失败
- 4		//取消安装
- 5		//不支持
- 6		//未知错误
