/*
Title: wx
Description: wx
*/
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
</div>

#**概述**

wx 封装了微信开放平台的SDK，集成了微信登录、微信分享功能；可用于实现微信账号登录，分享内容到朋友圈或好友；使用之前须从微信开放平台申请开发者账号并创建应用，获取 appid 和 secret。**wx 模块优化了 weiXin 模块的登录、分享功能，不包含微信支付功能。**

**使用此模块之前建议先配置  config.xml 文件，配置完毕，需通过云端编译生效，配置方法如下：**

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

    **urlScheme**：（必须配置）用于实现应用间跳转及数据交换，本应用可以启动微信客户端，也可以从微信客户端跳回本应用。urlScheme 的 value 值是从微信开放平台获取的 appid。
    
    **apiKey**：（必须配置）从微信开放平台获取的 appid，值与 urlScheme 相同。

    **apiSecret**：从微信开放平台获取的 secret。**获取 accessToken 时需要配置此项**。
    
<div id="a1"></div>
#**isInstalled**

判断当前设备是否安装微信客户端

isInstalled(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    installed: true      //布尔型；true||false，当前设备是否安装微信客户端
}
```
err：

- 类型：JSON对象
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
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取。

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

- 类型：JSON对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON对象
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
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取。

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
- 描述：（可选项）缩略图片的地址，支持 fs://，widget:// 协议。**大小不能超过32K，若 contentUrl 为本地图片地址则本参数忽略**

contentUrl：

- 类型：字符串
- 描述：分享图片的 url 地址（支持 fs://、widget:// 和网络路径），长度不能超过10k，**若为网络图片仅当 scene 为 session 时有效，若为本地图片大小不能超过10M**

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON对象
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
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取。

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
- 描述：（可选项）分享网络音频的缩略图地址，要求本地路径（fs://，widget://）**大小不能超过32K**

contentUrl：

- 类型：字符串
- 描述：（可选项）分享网络音频的 url 地址，长度不能超过10k。

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON对象
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
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取。

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
- 描述：（可选项）分享网络视频的缩略图地址，要求本地路径（fs://，widget://）**大小不能超过32K**

contentUrl：

- 类型：字符串
- 描述：（可选项）分享网络视频的 url 地址，长度不能超过10k。

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON对象
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
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取。

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
- 描述：（可选项）分享网页的缩略图地址，要求本地路径（fs://，widget://）**大小不能超过32K**

contentUrl：

- 类型：字符串
- 描述：（可选项）分享网页的 url 地址，长度不能超过10k。

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON对象
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
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取，不传或传入错误的 apiKey，则无法打开微信进行登录。

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
  status: true,       //布尔型；true||false
  code: ''           //字符串类型；getToken 接口需传入此值，用于换取 accessToken
}
```

err：

- 类型：JSON对象
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
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取。

apiSecret

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 secret，若不传则从当前 widget 的 `config.xml` 中读取。

code

- 类型：字符串
- 描述：通过 auth 接口授权成功后返回的 code 参数

##callback(ret, err)

ret：

- 类型：JSON对象
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

- 类型：JSON对象
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

- 类型：JSON对象
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

- 类型：JSON对象
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
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取。

dynamicToken：

- 类型：字符串
- 描述：getToken 接口或 refreshToken 接口获取的 dynamicToken 值


##callback(ret, err)

ret：

- 类型：JSON对象
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

- 类型：JSON对象
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
