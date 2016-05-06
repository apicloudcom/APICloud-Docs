/*
Title: wx
Description: wx
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<div class="outline">
[isInstalled](#a1)

[shareText](#a2)

[shareImage](#a3)

[shareMusic](#a4)

[shareVideo](#a5)

[shareWebpage](#a6)

[auth](#a7)

[getToken](#a8)

[getUserInfo](#a9)

[refreshToken](#a10)

[shareMutableImg](#a11)
</div>

#**概述**

**微信简介**

微信 (WeChat) 是腾讯公司于2011年1月21日推出的一个为智能终端提供即时通讯服务的免费应用程序，微信支持跨通信运营商、跨操作系统平台通过网络快速发送免费（需消耗少量网络流量）语音短信、视频、图片和文字。截止到2016年第一季度，微信已经覆盖中国 90% 以上的智能手机，月活跃用户达到 5.49 亿，用户覆盖 200 多个国家、超过 20 种语言。此外，各品牌的微信公众账号总数已经超过 800 万个，移动应用对接数量超过 85000 个，微信支付用户则达到了 4 亿左右。

微信提供公众平台、朋友圈、消息推送等功能，用户可以通过“摇一摇”、“搜索号码”、“附近的人”、扫二维码方式添加好友和关注公众平台，同时微信将内容分享给好友以及将用户看到的精彩内容分享到微信朋友圈。

**微信功能服务**

- 朋友圈：用户可以通过朋友圈发表文字和图片，同时可通过其他软件将文章或者音乐分享到朋友圈。用户可以对好友新发的照片进行“评论”或“赞”，用户只能看相同好友的评论或赞。
- 语音提醒：用户可以通过语音告诉Ta提醒打电话或是查看邮件。[19] 
- 通讯录安全助手：开启后可上传手机通讯录至服务器，也可将之前上传的通讯录下载至手机。[24] 
- QQ邮箱提醒：开启后可接收来自QQ邮件的邮件，收到邮件后可直接回复或转发。[24] 
- 私信助手：开启后可接收来自QQ微博的私信，收到私信后可直接回复。[24] 
- 漂流瓶：通过扔瓶子和捞瓶子来匿名交友。
- 查看附近的人：微信将会根据您的地理位置找到在用户附近同样开启本功能的人。（LBS功能）
- 语音记事本：可以进行语音速记，还支持视频、图片、文字记事。
- 微信摇一摇：是微信推出的一个随机交友应用，通过摇手机或点击按钮模拟摇一摇，可以匹配到同一时段触发该功能的微信用户，从而增加用户间的互动和微信粘度。
- 群发助手：通过群发助手把消息发给多个人。
- 微博阅读：可以通过微信来浏览腾讯微博内容。
- 流量查询：微信自身带有流量统计的功能，可以在设置里随时查看微信的流量动态。
- 游戏中心：可以进入微信玩游戏（还可以和好友比高分）例如“飞机大战”。
- 微信公众平台：通过这一平台，个人和企业都可以打造一个微信的公众号，可以群发文字、图片、语音三个类别的内容。目前有200万公众账号。
- 微信在IPhone、Android、Windows Phone、Symbian、BlackBerry等手机平台上都可以使用，并提供有多种语言界面。

**wx 模块概述**

本模块封装了微信开放平台的原生 SDK，集成了微信登录、微信分享功能；可用于实现微信账号登录，分享内容到朋友圈或好友、收藏等功能；轻松、高效集成微信功能到自己的 app 内。使自己的 app 和微信实现无缝链接。

**模块使用攻略**

使用之前须从微信开放平台申请开发者账号并创建应用，获取 appid 和 secret。**wx 模块优化了 weiXin 模块的登录、分享功能，不包含微信支付功能。**

微信平台接入流程参考[微信平台接入文档](http://docs.apicloud.com/APICloud/开放平台接入指南/weChat)

**使用此模块之前建议先配置  [config.xml](/APICloud/技术专题/app-config-manual) 文件，配置完毕，需通过云端编译生效，配置方法如下：**

- 名称：wx
- 参数：urlScheme、apiKey、apiSecret
- 配置示例:

```xml
  <feature name="wx">
    <param name="urlScheme" value="wxd0d84bbf23b4a0e4"/>
    <param name="apiKey" value="wxd0d84bbf23b4a0e4"/>
    <param name="apiSecret" value="a354f72aa1b4c2b8eaad137ac81434cd"/>
  </feature>
```
- 字段描述:

    **urlScheme**：（必须配置）用于实现应用间跳转及数据交换，本应用可以启动微信客户端，也可以从微信客户端跳回本应用。urlScheme 的 value 值是从微信开放平台获取的 appid。appid 申请方法参考[微信开放平台接入文档](http://docs.apicloud.com/APICloud/开放平台接入指南/weChat)。
    
    **apiKey**：（必须配置）从微信开放平台获取的 appid，值与 urlScheme 相同。appid 申请方法参考[微信开放平台接入文档](http://docs.apicloud.com/APICloud/开放平台接入指南/weChat)。

    **apiSecret**：从微信开放平台获取的 secret。**获取 accessToken 时需要配置此项**。appid 申请方法参考[微信开放平台接入文档](http://docs.apicloud.com/APICloud/开放平台接入指南/weChat)。
    
    
**Android 系统平台上需注意事项请参考[微信集成注意事项](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=9307)**


## [实例widget下载地址](https://github.com/XM-Right/wx-Example/archive/master.zip)
    
##**模块接口**
    
<div id="a1"></div>
#**isInstalled**

判断当前设备是否安装微信客户端

isInstalled(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    installed: true      //布尔型；true||false，当前设备是否安装微信客户端
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误），
                //0（成功）
}
```
##示例代码

```js
var wx = api.require('wx');
wx.isInstalled(function(ret, err){
	if(ret.installed){
        alert("当前设备已安装微信客户端");
	}else{
        alert('当前设备未安装微信客户端');
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a2"></div>
#**shareText**

分享文本内容

shareText({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 [config.xml](/APICloud/技术专题/app-config-manual) 中读取。

scene：

- 类型：字符串
- 描述：（可选项）场景
- 默认值：timeline
- 取值范围：
    * timeline（朋友圈）

text：

- 类型：字符串
- 描述：分享的文本

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误）
                //0（成功）
                //1（apiKey非法）
                //2（用户取消）
                //3（发送失败）
                //4（授权拒绝）
                //5（微信服务器返回的不支持错误）
                //6 (当前设备未安装微信客户端)
                //7 (注册SDK失败)
}
```

##示例代码

```js
var wx = api.require('wx');
wx.shareText({
    apiKey: '',
    scene: 'timeline',
    text: '我分享的文本'
}, function(ret, err){
    if(ret.status){
        alert('分享成功');
    }else{
        alert(err.code);
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a3"></div>
#**shareImage**

分享图片内容

shareImage({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 [config.xml](/APICloud/技术专题/app-config-manual) 中读取。

scene：

- 类型：字符串
- 描述：（可选项）场景
- 默认值：timeline
- 取值范围：
    * session（会话）
    * timeline（朋友圈）
    * favorite（收藏）

thumb：

- 类型：字符串
- 描述：缩略图片的地址，支持 fs://、widget:// 协议。**大小不能超过32K，若 contentUrl 为本地图片地址则本参数忽略,需要路径包含图片格式后缀，否则如果原图片为非png格式，会分享失败**

contentUrl：

- 类型：字符串
- 描述：分享图片的 url 地址（支持 fs://、widget:// 和网络路径），长度不能超过10k，**若为网络图片仅当 scene 为 session 时有效，若为本地图片大小不能超过10M**

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误）
                //0（成功）
                //1（apiKey非法）
                //2（用户取消）
                //3（发送失败）
                //4（授权拒绝）
                //5（微信服务器返回的不支持错误）
                //6 (当前设备未安装微信客户端)
                //7 (注册SDK失败)
}
```

##示例代码

```js
var wx = api.require('wx');
wx.shareImage({
    apiKey: '',
    scene: 'timeline',
    thumb: 'widget://a.jpg',
    contentUrl: 'http://pic68.nipic.com/file/20150602/17961491_181130435000_2.jpg'
}, function(ret, err){
    if(ret.status){
        alert('分享成功');
    }else{
        alert(err.code);
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a4"></div>
#**shareMusic**

分享网络音频资源

shareMusic({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 [config.xml](/APICloud/技术专题/app-config-manual) 中读取。

scene：

- 类型：字符串
- 描述：（可选项）场景
- 默认值：timeline
- 取值范围：
    * session（会话）
    * timeline（朋友圈）
    * favorite（收藏）

title：

- 类型：字符串
- 描述：（可选项）分享网络音频的标题。

description：

- 类型：字符串
- 描述：（可选项）分享网络音频的描述。

thumb：

- 类型：字符串
- 描述：（可选项）分享网络音频的缩略图地址，要求本地路径（fs://、widget://）**大小不能超过32K,需要路径包含图片格式后缀，否则如果原图片为非png格式，会分享失败**

musicDataUrl：

- 类型：字符串
- 描述：（可选项）分享的音频数据 url 地址，长度不能超过10k。

contentUrl：

- 类型：字符串
- 描述：（可选项）分享网络音频的 url 地址，长度不能超过10k。

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误）
                //0（成功）
                //1（apiKey非法）
                //2（用户取消）
                //3（发送失败）
                //4（授权拒绝）
                //5（微信服务器返回的不支持错误）
                //6 (当前设备未安装微信客户端)
                //7 (注册SDK失败)
}
```

##示例代码

```js
var wx = api.require('wx');
wx.shareMusic({
    apiKey: '',
    scene: 'timeline',
    title: '测试标题',
    description: '分享内容的描述',
    thumb: 'widget://a.jpg',
    contentUrl: 'http://docs.apicloud.com/test/m.mp3'
}, function(ret, err){
    if(ret.status){
        alert('分享成功');
    }else{
        alert(err.code);
    }
});
```
##补充说明

仅支持分享网络音频资源

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a5"></div>
#**shareVideo**

分享网络视频资源

shareVideo({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 [config.xml](/APICloud/技术专题/app-config-manual) 中读取。

scene：

- 类型：字符串
- 描述：（可选项）场景
- 默认值：timeline
- 取值范围：
    * session（会话）
    * timeline（朋友圈）
    * favorite（收藏）

title：

- 类型：字符串
- 描述：（可选项）分享网络视频的标题。

description：

- 类型：字符串
- 描述：（可选项）分享网络视频的描述。**由于微信平台限制，对不同平台部分场景本参数无效**

thumb：

- 类型：字符串
- 描述：（可选项）分享网络视频的缩略图地址，要求本地路径（fs://、widget://）**大小不能超过32K,需要路径包含图片格式后缀，否则如果原图片为非png格式，会分享失败**

contentUrl：

- 类型：字符串
- 描述：（可选项）分享网络视频的 url 地址，长度不能超过10k。

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误）
                //0（成功）
                //1（apiKey非法）
                //2（用户取消）
                //3（发送失败）
                //4（授权拒绝）
                //5（微信服务器返回的不支持错误）
                //6 (当前设备未安装微信客户端)
                //7 (注册SDK失败)
}
```

##示例代码

```js
var wx = api.require('wx');
wx.shareVideo({
    apiKey: '',
    scene: 'timeline',
    title: '测试标题',
    description: '分享内容的描述',
    thumb: 'widget://a.jpg',
    contentUrl: 'http://resource.apicloud.com/video/apicloud.mp4'
}, function(ret, err){
    if(ret.status){
        alert('分享成功');
    }else{
        alert(err.code);
    }
});
```
##补充说明

仅支持分享网络视频资源

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a6"></div>
#**shareWebpage**

分享网页

shareWebpage({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 [config.xml](/APICloud/技术专题/app-config-manual) 中读取。

scene：

- 类型：字符串
- 描述：（可选项）场景
- 默认值：timeline
- 取值范围：
    * session（会话）
    * timeline（朋友圈）
    * favorite（收藏）

title：

- 类型：字符串
- 描述：（可选项）分享网页的标题

description：

- 类型：字符串
- 描述：（可选项）分享网页的描述。**由于微信平台限制，对不同平台部分场景本参数无效**

thumb：

- 类型：字符串
- 描述：（可选项）分享网页的缩略图地址，要求本地路径（fs://、widget://）**大小不能超过32K,需要路径包含图片格式后缀，否则如果原图片为非png格式，会分享失败**

contentUrl：

- 类型：字符串
- 描述：（可选项）分享网页的 url 地址，长度不能超过10k。

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误）
                //0（成功）
                //1（apiKey非法）
                //2（用户取消）
                //3（发送失败）
                //4（授权拒绝）
                //5（微信服务器返回的不支持错误）
                //6 (当前设备未安装微信客户端)
                //7 (注册SDK失败)
}
```

##示例代码

```js
var wx = api.require('wx');
wx.shareWebpage({
    apiKey: '',
    scene: 'timeline',
    title: '测试标题',
    description: '分享内容的描述',
    thumb: 'widget://a.jpg',
    contentUrl: 'http://apicloud.com'
}, function(ret, err){
    if(ret.status){
        alert('分享成功');
    }else{
        alert(err.code);
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a7"></div>
#**auth**

登录授权（**用于实现第三方登录**）

auth({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 [config.xml](/APICloud/技术专题/app-config-manual) 中读取，不传或传入错误的 apiKey，则无法打开微信进行登录。

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
  status: true,       //布尔型；true||false
  code: ''           //字符串类型；getToken 接口需传入此值，用于换取 accessToken
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误），
                //0（成功，用户同意）
                //1 (用户取消)
                //2 (用户拒绝授权)
                //3 (当前设备未安装微信客户端)
}
```

##示例代码

```js
var wx = api.require('wx');
wx.auth({
    apiKey: ''
}, function(ret, err){ 
	if(ret.status){
    	alert(JSON.stringify(ret));
	}else{
    	alert(err.code);
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a8"></div>
#**getToken**

获取授权 accessToken（**需要登录授权成功**）

getToken({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 [config.xml](/APICloud/技术专题/app-config-manual) 中读取。

apiSecret

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 secret，若不传则从当前 widget 的 [config.xml](/APICloud/技术专题/app-config-manual) 中读取。

code

- 类型：字符串
- 描述：通过 auth 接口授权成功后返回的 code 参数

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
  status: true,      //布尔型；true||false
  accessToken: '',   //字符串类型；接口调用凭证，传给 getUserInfo 接口 获取用户信息；有效期2小时
  dynamicToken: '',  //字符串类型；当 accessToken 过期时把该值传给 refreshToken 接口刷新 accessToken 的有效期。dynamicToken 的有效期为30天
  expires: 7200,     //数字类型；accessToken 有效期，单位（秒）
  openId: ''         //字符串类型；授权用户唯一标识
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误），
                //0 （成功）
                //1 (apiKey值为空或非法)
                //2 (apiSecret值为空或非法)
                //3 (code值为空或非法)
                //4 (网络超时)
}
```

##示例代码

```js
var wx = api.require('wx');
wx.getToken({
    apiKey: '',
    apiSecret: '',
    code: "12346857684"
},function(ret, err){ 
	if(ret.status){
    	alert(JSON.stringify(ret));
	}else{
    	alert(err.code);
	}
});
```

##补充说明

此接口需要访问网络，异步调用 callback 需要一段时间才能返回 accessToken

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a9"></div>
#**getUserInfo**

获取用户信息（**需要获取 accessToken 成功**）

getUserInfo({params}, callback(ret, err))

##params

accessToken：

- 类型：字符串
- 描述：getToken 接口或 refreshToken 接口成功获取的 accessToken 值

openId：

- 类型：字符串
- 描述：getToken 接口或 refreshToken 接口成功获取的 openId 值

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true,      //布尔型；true||false
	openid: '',        //字符串类型；普通用户的标识，对当前开发者帐号唯一
	nickname: '',      //字符串类型；普通用户昵称
	sex: 1,            //数字类型；普通用户性别，1为男性，2为女性
	headimgurl: '',    //字符串类型；用户头像，最后一个数值代表正方形头像大小（有0、46、64、96、132数值可选，0代表640*640正方形头像），用户没有头像时该项为空
	privilege: [],     //数组类型；用户特权信息，如微信沃卡用户为（chinaunicom）
	unionid: ''        //字符串类型；用户统一标识。针对一个微信开放平台帐号下的应用，同一用户的unionid是唯一的。
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误），
                //0 （成功）,
                //1 （accessToken 过期）,
				//2  (openId非法),
				//3  (openId值为空),
				//4	 (accessToken值为空),
				//5	 (accessToken非法)
				//6	 (网络超时)
}
```

##示例代码

```js
var wx = api.require('wx');
wx.getUserInfo({
	accessToken: '',
    openId: ''
}, function(ret,err){ 
	if(ret.status){
		alert(JSON.stringify(ret));
	}else{
    	alert(err.code);
	}
});
```

##补充说明

此接口需要访问网络，异步调用 callback 需要一段时间才能返回用户信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a10"></div>
#**refreshToken**

调用 getUserInfo 接口错误码返回1时，代表 accessToken 过期，调用此接口刷新 accessToken

refreshToken({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 [config.xml](/APICloud/技术专题/app-config-manual) 中读取。

dynamicToken：

- 类型：字符串
- 描述：getToken 接口或 refreshToken 接口获取的 dynamicToken 值


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,      //布尔型；true||false
    accessToken: '',   //字符串类型；接口调用凭证，传给 getUserInfo 接口 获取用户信息；有效期2小时
    dynamicToken: '',  //字符串类型；当 accessToken 过期时把该值传给 refreshToken 接口刷新 accessToken 的有效期。dynamicToken 的有效期为30天
    expires: 7200,     //数字类型；accessToken 有效期，单位（秒）
    openId: ''         //字符串类型；授权用户唯一标识
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；
                //错误码：
                //-1（未知错误），
                //0（成功）,
                //1（apiKey值为空或非法），
                //2（refreshToken值为空）,
                //3（refreshToken非法），
                //4（网络超时）
}
```

##示例代码

```js
var wx = api.require('wx');
wx.refreshToken({
    apiKey: '',
	dynamicToken: ''
},function(ret,err){ 
	if(ret.status){
		alert(JSON.stringify(ret));
	}else{
    	alert(err.code);
	}
});
```

##补充说明

此接口需要访问网络，异步调用 callback 需要一段时间才能返回 accessToken

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="a11"></div>
#**shareMutableImg**

分享多张图片到朋友圈，**暂仅支持 Android 平台。注意：由于不是使用的官方sdk进行的分享，而是直接调用的微信客户端的分享界面，分享后无法回到原应用，且微信端不会给出是否分享成功的反馈，所以本接口暂无回调**

shareMutableImg({params})

##params

imgs：

- 类型：数组
- 描述：要分享的图片的路径组成的数组，要求本地路径（fs://、widget://）

description：

- 类型：字符串
- 描述：分享的文字


##示例代码

```js
var wx = api.require('wx');
wx.shareMutableImg({
    description: 'weixin share image test description',
	imgs:['widget://res/1.png','widget://res/12.jpg','widget://res/123.jpg']
});
```

##可用性

Android系统

可提供的1.0.0及更高版本