/*
Title: sendSms
Description: sendSms
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[regSms](#a1)

[sendMessage](#a2)

[enterCode](#a3)
</div>

#**概述**

sendSms实现了注册时短信验证，取回密码手机验证功能，使用此模块之前需要先去http://mob.com/ 注册获取appkey和appsecret，mob每天可以有10000条免费的短信，基本上可以算是免费的了


使用注意事项：
1、请在云端打包！请在云端打包！请在云端打包！（重要的事说三遍）
2、短信中的掌淘科技可以去除，具体请咨询mob官方
3、老给一个手机号发短信会导致失败率很高，这个是运营商为了防骚扰做的
4、测试包地址：http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=14430


#**regSms**<div id="a1"></div>

注册应用

regSms(params)

##params

appkey：

- 类型：字符串
- 描述：从mob网站获取的appkey，不能为空

appsecret：

- 类型：字符串
- 描述：从mob网站获取的appsecret，不能为空，注册保密

##示例代码

```js
//貌似是120秒内只能注册一次，不然会失败，注意下
//需要特别注意的事，这个函数没有回调！！我已经和官方沟通了，确实没有
sendsms = api.require('sendSms');
var param = {appkey:"6680ba14a50e",appsecret:"95b67202d004b9f4ab2a38f3eda2e82c"};
sendsms.regSms(param);
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**sendMessage**<div id="a2"></div>

发送手机验证码

sendMessage(params,callback(ret, err))

##params

phone：

- 类型：字符串
- 描述：欲验证的手机号，13800000000的形式，暂时不支持国外

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
  result:ok		//操作成功状态值，字符串类型
}

```

##示例代码

```js
sendsms = api.require('sendSms');
var param = {phone:13800000000};
sendsms.sendMessage(param,function(ret,err){
	if(ret.result == "ok"){
	        maxtime = 90;
			timer1 = setInterval("send_code_jishi();", 1000);
	        alert("短信发送成功");
	}else{
	        alert(ret.result);
	}
});
```

##补充说明

对方说是5秒内短信可以到达，实际上大部分时间都在这个范围内，但部分短信会有延迟，最好提示下用户（比如短信送达倒计时，倒计时结束才可以再发）

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**enterCode**<div id="a3"></div>

输入收到的验证码，验证手机号

enterCode(params,callback(ret, err))

##params

code：

- 类型：字符串
- 描述：收到的验证码，应该是4位数字

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    result:ok    		//操作成功状态值，字符串类型
}
```

##示例代码

```js
//mycode表示收到的验证码
sendsms = api.require('sendSms');
var param={code:mycode};
sendsms.enterCode(param,function(ret,err){
	if(ret.result == "ok"){
		alert("验证成功");
	}else{
		alert("验证失败");
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本