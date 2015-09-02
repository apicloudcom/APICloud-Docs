/*
Title: baiduAuth
Description: baiduAuth
*/
<div class="outline">
[login](#m1)

[logout](#m2)

[getUserInfo](#m3)
</div>

#**概述**

baiduAuth 模块封装了百度授权登录 SDK，可用于实现百度账号登录授权、获取用户信息功能；使用之前需要到[百度开放服务平台](http://developer.baidu.com/console#app/project)创建应用，获取 apiKey；建议把 `apiKey` 配置到 `config.xml` 文件。

**使用此模块之前建议先配置  config 文件，配置方法如下：***

```xml
  <feature name="baidu">
	<param name="apiKey" value="0trswTLaGB6hN820M30Brbhx" />
  </feature>
```

<div id="m1"></div>
#**login**

登录授权

login({parmas}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从百度申请的 API Key，若不传则从当前 widget 的 `config.xml` 中读取

force：

- 类型：布尔
- 描述：（可选项）是否强制登录；若为 false，则 logout 后再 login 时直接返回 token、uid 等信息；若为 true 则再次 login 时跳转到登录页面
- 默认值：true

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true,      	//布尔类型；登录是否成功
	userInfo: {        	//JSON对象；登录成功后获取的用户信息及 token
		uid: '',       	//字符串类型；用户的 ID
		uname: '',     	//字符串类型；用户的昵称，可能为空
		portrait: '',  	//字符串类型；用户的头像地址，可能为空
		accessToken: ''	//字符串类型；百度分配的登录 token 值  
	}
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	code: 0     //数字类型；错误码
				//取值范围：
				//-1（未知错误）
				//0（登录成功）
				//1（apiKey 值非法）
				//2（账号或密码错误）
				//3（用户取消登录）
}
```

##示例代码

```js
var baiduAuth = api.require('baiduAuth');
baiduAuth.login({
	apiKey: '0trswTLaGB6hN820M30Brbhx',
	force: true
},function(ret,err){
	if(ret){
		alert(JSON.stringify(ret));
	}else{
		alert(JSON.stringify(err));
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m2"></div>
#**logout**

退出登录并取消授权

logout()

##示例代码

```js
var baiduAuth = api.require('baiduAuth');
baiduAuth.logout();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>
#**getUserInfo**

获取用户详细信息

getUserInfo({parmas}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从百度申请的 API Key，若不传则从当前 widget 的 `config.xml` 中读取

accessToken：

- 类型：字符串
- 描述：登录后获取的 accessToken

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true,       	//布尔型；true||false是否成功获取用户信息
	userInfo: {				//JSON对象，当前登录用户的信息
		userid: '',     	//字符串类型；用户的 ID
		username: '',   	//字符串类型；用户名，可能为空
		realname: '',   	//字符串类型；真实姓名，可能为空
		portrait: '',   	//字符串类型；头像 url，可能为空
		userdetail: '', 	//字符串类型；自我简介，可能为空
		birthday: '',    	//字符串类型；生日，以 yyyy-mm-dd 格式显示，可能为空
		marriage: '',    	//字符串类型；婚姻状况，可能为空
		sex: '',        	//字符串类型；性别，可能为空
		blood: '',       	//字符串类型；血型，可能为空
		figure: '',      	//字符串类型；体型，可能为空
		education: '',   	//字符串类型；学历，可能为空
		trade: ''       	//字符串类型；当前职业，可能为空
	}
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	code: 0		//数字类型；错误码
				//取值范围如下：
				//-1（未知错误）
				//0（获取信息成功）
				//1（apiKey 值非法）
				//2（accessToken 值过期）
				//3（accessToken 值非法）
}
```

##示例代码

```js
var baiduAuth = api.require('baiduAuth');
baiduAuth.getUserInfo({
  accessToken: '23.d066380144827c5411ee0bd78b9d38f6.2592000.1436063436.739729233-6094198'
}, function(ret, err){
	if(ret){
		alert(JSON.stringify(ret));
	}else{
		alert(JSON.stringify(err));
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
