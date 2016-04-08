/*
Title: mobVerify
Description: mobVerify
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
    
</ul>
<div id="method-content">

<div class="outline">
[register](#a1)

[send](#a2)

[voice](#a3)

[verify](#a4)

</div>

#**概述**

mobVerify封装了mob提供的免费短信+语音验证码的SDK，使用此模块可轻松实现验证手机号码真实性的功能，当前版本支持mob短信验证2.0版本，对于老版本用户请重新到mob官网申请新的appkey，并验证，可以从原来每天10000条免费短信升级到完全免费！

#**register**<div id="a1"></div>

注册应用

register({param})

##param
appkey:

- 类型：字符串
- 描述：mob 官网注册获取的 key

appsecret:

- 类型：字符串
- 描述：mob 官网注册获取的 secret

##示例代码

```js

	    var mob = null;
		apiready = function() {
			 mob = api.require('mobVerify');
			mob.register({
				appkey : '6680ba14a5**',
				appsecret : '95b67202d004b9f4ab2a38f3eda2e8**'
			});
			

		};

```

##补充说明

请在有需要短信验证的页面的apiready中运行该方法

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**send**<div id="a2"></div>

发送短信

send({params}, callback(ret, err))

##params

phone：

- 类型：字符串
- 描述：需要验证的手机号码

country：

- 类型：字符串
- 描述：（可选项）手机号码对应国家号，国内手机可以不填该值
- 默认值：'86'

##callback(err)

err：

- 类型：JSON 对象
- 描述：当err为null时短信发送成功
- 内部字段：
```js
{
    status: -1,
    detaul: '错误内容'
}
```

##示例代码

```js
function sendCode(){
    var phone = document.getElementById('phone').value;
	mob.send({
		phone: phone
	}, function(ret, err){
		if(err){
			api.alert({msg: JSON.stringify(err)});
		}else{
			api.alert({msg: '短信已发送'});
		}
	});
}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**voice**<div id="a3"></div>

发送语音短信

voice({params}, callback(ret, err))

##params

phone：

- 类型：字符串
- 描述：需要验证的手机号码

country：

- 类型：字符串
- 默认值：'86'
- 描述：（可选项）手机号码对应国家号，国内手机可以不填该值

##callback(err)

err：

- 类型：JSON 对象
- 描述：当err为null时语音发送成功
- 内部字段：
```js
{
    status: -1,
    detaul: '错误内容'
}
```

##示例代码

```js
function sendVoiceCode(){
    var phone = document.getElementById('phone').value;
	mob.voice({
		phone: phone
	}, function(ret, err){
		if(err){
			api.alert({msg: JSON.stringify(err)});
		}else{
			api.alert({msg: '语音短信已发送'});
		}
	});
}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**verify**<div id="a4"></div>

校对验证码

verify({params}, callback(ret, err))

##params

phone：

- 类型：字符串
- 描述：需要校对的手机号码

code：

- 类型：字符串
- 描述：收到的验证码

##callback(err)

err：

- 类型：JSON 对象
- 描述：当err为null时语音发送成功
- 内部字段：
```js
{
    status: -1,
    detaul: '错误内容'
}
```

##示例代码

```js
function verifyCode(){
    var phone = document.getElementById('phone').value,
        code = document.getElementById('code').value;
	mob.verify({
		phone: phone,
		code: code
	}, function(ret, err){
		if(err){
			api.alert({msg: '验证码错误'});
		}else{
			api.alert({msg: '验证码正确'});
		}
	});
}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本