/*
Title: weibo
Description: weibo
*/
<div class="outline">
[shareText](#1)

[shareImage](#2)

[shareMusic](#3)

[shareVideo](#4)

[shareWebPage](#5)

[auth](#6)

[cancelAuth](#7)

[getUserInfo](#8)

[isInstalled](#9)
</div>

#**概述**

微博是一个由新浪网推出，提供微型博客服务类的社交网站。用户可以通过网页、WAP页面、手机客户端、手机短信、彩信发布消息或上传图片。新浪可以把微博理解为“微型博客”或者“一句话博客”。用户可以将看到的、听到的、想到的事情写成一句话，或发一张图片，通过电脑或者手机随时随地分享给朋友，一起分享、讨论；还可以关注朋友，即时看到朋友们发布的信息。

**模块概述**

weibo 封装了新浪微博开放平台的移动端 SDK，使用此模块可实现新浪微博授权登录，获取用户信息，分享文本、图片、音频、视频、网页等信息到微博移动客户端的功能。登陆授权时，模块内部会先判断当前设备是否安装微博客户端，若没安装则弹出网页版登陆页面，若已安装则跳转到微博客户端提示用户登陆授权。

开发者使用本模块之前须从[新浪微博开放平台](http://open.weibo.com)申请微博开发者账号，微博开发者账号申请成功后需要填写相应信息创建一个app应用，从而获取 App Key。注意：新浪微博服务器不允许在短时间内连续发布两条相同内容的微博，测试时如果连续发送两条内容相同的微博，后者可能不显示。**weibo 模块是 sinaWeibo 模块的优化版。**

##模块使用攻略

**使用此模块之前建议先配置  config.xml 文件，配置完毕，需通过云端编译生效，配置方法如下：**

- 名称：weibo
- 参数：urlScheme、apiKey、registUrl
- 配置示例：

```xml
 <feature name="weibo">
   <param name="urlScheme" value="wb1132217156" />
   <param name="apiKey" value="1132217156" />
   <param name="registUrl" value="http://www.apicloud.com" />
 </feature>
```
- 字段描述：

     **urlScheme**：（必须配置）用于实现应用间跳转及数据交换，本应用可以启动新浪微博客户端，也可以从新浪微博客户端跳回本应用。urlScheme 的 value 值是从新浪微博开放平台获取到的 App Key 拼接前缀 wb 而成的。
     
    **apiKey**：从新浪微博开放平台获取的 App Key。

    **registUrl**：在新浪微博开放平台创建应用时（应用信息 -> 高级信息 -> 授权设置）自定义填写的回调 url。

#**模块接口**

<div id="1"></div>

#**shareText**

分享文本内容

shareText({params}, callback(ret, err))

##params


apiKey：

- 类型：字符串
- 描述：（可选项）从新浪开放平台申请的 App Key ，若不传则从当前 widget 的 `config.xml` 文件读取

text：

- 类型：字符串
- 描述：分享的文本，**长度小于140个汉字**

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true      //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1        //数字类型；
                   //错误码：
                   //-1 （apiKey值非法）
                   //1 （用户取消）
                   //2 （发送失败）
                   //3 （授权失败）
                   //4 （不支持的请求）
                   //5 （未知错误）
}

```

##示例代码

```js
var weibo = api.require('weibo');
weibo.shareText({
    text: '这里是测试的内容',
},function(ret,err){
    if (ret.status) {
      alert('分享文本内容成功');
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="2"></div>

#**shareImage**

分享图片内容

shareImage({params}, callback(ret, err))

##params


apiKey：

- 类型：字符串
- 描述：（可选项）从新浪开放平台申请的 App Key ，若不传则从当前 widget 的 `config.xml` 文件读取

text：

- 类型：字符串
- 描述：（可选项）分享的文本，**长度小于140个汉字**

imageUrl：

- 类型：字符串
- 描述：分享的图片路径，要求本地路径（fs://，widget://），**大小不能超过10M**

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true      //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1        //数字类型；
                   //错误码：
                   //-2 （imageUrl图片资源未找到）
                   //-1 （apiKey值非法）
                   //1 （用户取消）
                   //2 （发送失败）
                   //3 （授权失败）
                   //4 （不支持的请求）
                   //5 （未知错误）
}
```

##示例代码

```js
var weibo = api.require('weibo');
weibo.shareImage({
    text: '这里是测试的内容',
    imageUrl: 'widget://image/xxx.png'
},function(ret,err){
    if (ret.status) {
		  alert('分享图片内容成功');
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="3"></div>

#**shareMusic**

分享网络音频资源

shareMusic({params}, callback(ret, err))

##params


apiKey：

- 类型：字符串
- 描述：（可选项）从新浪开放平台申请的 App Key ，若不传则从当前 widget 的 `config.xml` 文件读取

text：

- 类型：字符串
- 描述：（可选项）分享的文本，**长度小于140个汉字**

title：

- 类型：字符串
- 描述：分享网络音频的标题，**不能为空且长度小于1k**

description：

- 类型：字符串
- 描述：（可选项）分享网络音频的描述，**长度小于1k**

thumb：

- 类型：字符串
- 描述：分享网络音频的缩略图地址，要求本地路径（fs://，widget://），**大小小于32k**

contentUrl：

- 类型：字符串
- 描述：分享网络音频的 url 地址，**不能为空且长度不能超过255**

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true      //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1        //数字类型；
                   //错误码：
                   //-1 （ apiKey 值非法）
                   //1 （用户取消）
                   //2 （发送失败）
                   //3 （授权失败）
                   //4 （不支持的请求）
                   //5 （未知错误）
}
```

##示例代码

```js
var weibo = api.require('weibo');
weibo.shareMusic({
    text: '这里是测试的内容',
    title: '测试标题',
    description: '分享内容的描述',
    thumb: 'widget://a.jpg',
    contentUrl: 'http://docs.apicloud.com/test/m.mp3'
},function(ret,err){
    if (ret.status) {
		  alert('分享成功');
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="4"></div>

#**shareVideo**

分享网络视频资源

shareVideo({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从新浪开放平台申请的 App Key ，若不传则从当前 widget 的 `config.xml` 文件读取

text：

- 类型：字符串
- 描述：（可选项）分享的文本，**长度小于140个汉字**

title：

- 类型：字符串
- 描述：分享网络视频的标题，**不能为空且长度小于1k**

description：

- 类型：字符串
- 描述：（可选项）分享网络视频的描述，**长度小于1k**

thumb：

- 类型：字符串
- 描述：分享网络视频的缩略图地址，要求本地路径（fs://，widget://），**大小小于32k**

contentUrl：

- 类型：字符串
- 描述：分享网络视频的 url 地址，**不能为空且长度不能超过255**

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true      //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1        //数字类型；
                   //错误码：
                   //-1 （ apiKey 值非法）
                   //1 （用户取消）
                   //2 （发送失败）
                   //3 （授权失败）
                   //4 （不支持的请求）
                   //5 （未知错误）
}
```

##示例代码

```js
var weibo = api.require('weibo');
weibo.shareVideo({
    text: '这里是测试的内容',
    title: '测试标题',
    description: '分享内容的描述',
    thumb: 'widget://a.jpg',
    contentUrl: 'http://resource.apicloud.com/video/apicloud.mp4'
},function(ret,err){
    if (ret.status) {
		  alert('分享成功');
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="5"></div>

#**shareWebPage**

分享网页

shareWebPage({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从新浪开放平台申请的 App Key ，若不传则从当前 widget 的 `config.xml` 文件读取

text：

- 类型：字符串
- 描述：（可选项）分享的文本，**长度小于140个汉字**

title：

- 类型：字符串
- 描述：分享网页的标题，**不能为空且长度小于1k**

description：

- 类型：字符串
- 描述：（可选项）分享网页的描述，**长度小于1k**

thumb：

- 类型：字符串
- 描述：分享网页的缩略图地址，要求本地路径（fs://，widget://），**大小小于32k**

contentUrl：

- 类型：字符串
- 描述：分享网页的 url 地址，**不能为空且长度不能超过255**

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true      //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1        //数字类型；
                   //错误码：
                   //-1 （ apiKey 值非法）
                   //1 （用户取消）
                   //2 （发送失败）
                   //3 （授权失败）
                   //4 （不支持的请求）
                   //5 （未知错误）
}
```

##示例代码

```js
var weibo = api.require('weibo');
weibo.shareWebPage({
    text: '这里是测试的内容',
    title: '测试标题',
    description: '分享内容的描述',
    thumb: 'widget://a.jpg',
    contentUrl: 'http://apicloud.com'
},function(ret,err){
    if (ret.status) {
		  alert('分享成功');
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="6"></div>

#**auth**

授权登录（**用于实现第三方登录**）

auth({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从新浪微博开放平台申请的 App Key，若不传则从当前 widget 的 `config.xml` 中读取，不传或传入错误的 apiKey，则无法打开新浪微博进行登录。

registUrl：

- 类型：字符串
- 描述：（可选项）在新浪微博开放平台创建应用时（应用信息 -> 高级信息 -> 授权设置）自定义填写的回调 url，若为空则从当前 widget 的 `config.xml` 中读取

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true,  //布尔型；true||false
	token: '',     //字符串类型；从新浪微博服务器获取的 accessToken，接口调用凭证，传给 getUserInfo 接口获取用户信息
	expire: '',    //字符串类型：token 有效期（时间戳）
	userId: ''     //字符串类型；从新浪微博服务器获取的 userId，新浪微博分配的用户id，传给 getUserInfo 接口获取用户信息
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1     //数字类型；错误码
                //取值范围：
                //-1（apiKey 或 registUrl 值非法）
                //1（用户取消）
                //2 （发送失败）
                //3 （授权失败）
                //4 （不支持的请求）
                //5 （未知错误）
}
```

##示例代码

```js
var weibo = api.require('weibo');
weibo.auth(function(ret,err){
    if (ret.status) {
      alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="7"></div>

#**cancelAuth**

取消授权，退出登录状态

cancelAuth(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true      //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1     //数字类型；错误码
                //取值范围：
                //1（尚未登录）
}
```

##示例代码

```js
var weibo = api.require('weibo');
weibo.cancelAuth(function(ret,err){
	if(ret.status){
		api.alert({msg:'登出成功'});
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="8"></div>

#**getUserInfo**

获取用户账户信息，**调用本接口前，需要先调用  auth 接口授权**

getUserInfo({params}, callback(ret, err))

##params

token：

- 类型：字符串
- 描述：（可选项）登录账号获取的token值
- 默认值：当前已登录账号的 token

userId：

- 类型：字符串
- 描述：（可选项）登录账号获取的 userId
- 默认值：当前已登录账号的 userId

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：返回结果 userInfo 详情参考[获取用户信息-返回结果](http://open.weibo.com/wiki/2/users/show)

```js
{
	 status: true,        //布尔型；true||false
	 userInfo: {}         //JSON对象；获取的用户信息（微博返回）
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1              //数字类型：错误码
                         //取值范围：
                         //-1 (token 或 userId 非法)
                         //1 (网络超时)
}
```

##示例代码

```js
var weibo = api.require('weibo');
weibo.getUserInfo({
  token: '',
  userId: ''
},function(ret,err){
    if (ret.status) {
        alert(JSON.stringify(ret.userInfo));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="9"></div>

#**isInstalled**

判断是否已安装新浪微博客户端

isInstalled({params}, callback(ret, err))


##params

apiKey：

- 类型：字符串
- 描述：（可选项）从新浪微博开放平台申请的 App Key，若不传则从当前 widget 的 `config.xml` 中读取，不传或传入错误的 apiKey，则无法判断是否已安装新浪微博客户端。

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：
```js
{
	 status: true,        //布尔型；true||false
}
```

##示例代码

```js
var weibo = api.require('weibo');
weibo.isInstalled(
	function(ret,err){
    	if (ret.status) {
        	alert('已安装新浪微博客户端');
    	}else{
			alert('未安装新浪微博客户端');
		}
	}
);
```

##可用性

Android系统

可提供的1.0.0及更高版本