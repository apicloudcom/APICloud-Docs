/*
Title: bulkSMS
Description: bulkSMS
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	
</ul>
<div id="method-content">

<div class="outline">
[sends](#a1)

[stop](#a2)

</div>


#**概述**

bulkSMS模块封装了短信群发功能接口，使用此模块可轻松实现短信群发功能，在发送的消息内可在任意位置显示出你要显示的名字等信息。**暂仅支持 android 平台。**

#**sends**<div id="a1"></div>

短信群发

sends(params, callback(ret, err))

##params

users：

- 类型：JSON数组
- 描述：包含要发送短信的每个联系人的信息
- 内部字段：

```js
[{
	    "phoneNumber": "135xxxxxxxx",     //联系人电话号码
	    "disPlayName": "小王"             //姓名
}]
```

phoneNumber：

- 类型：字符串
- 描述：联系人电话号码

disPlayName：

- 类型：字符串
- 描述：联系人姓名

strcontents：

- 类型：JSON数组
- 描述：发送短信的内容，为多个时按照顺序分别发送给用户1 2 3...等接受用户超出信息内容数量时短信内容会从第一个重复。短信内容加入：#disPlayName# 的地方会显示disPlayName的值（联系人姓名），短信内容加入：#name# 的地方会显示name的值（比如发信人的姓名）。短信内容至少一条
- 内部字段：

```js
[
	 "祝#disPlayName#新年快乐#name#",    //短信内容 字符串类型，（注：disPlayName值是小王，name值是郭xx时）收信人会显示：祝小王新年快乐郭xx
	 "#name#祝#disPlayName#新年快乐",    //短信内容 字符串类型，（注：disPlayName值是小王，name值是郭xx时）收信人会显示：郭xx祝小王新年快乐
	 "祝新年快乐"                        //短信内容 字符串类型，收信人会显示：祝新年快乐
]
```

name：
- 类型：字符串
- 描述：（可选项）会替换短信内容中的 #name#


##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	results:0           //操作成功状态值0，失败1
	info:sendData       //返回的发送数据信息 数据类型JSON数组，失败时是错误描述
}
```


sendData：
- 类型：JSON数组
- 默认值：无
- 描述：群发成功后返回的发送数据信息

内部字段：
```js
[{
	    "phoneNumber": "135xxxxxxxx",                   //联系人电话号码
	    "strContents": "祝小张新年快乐郭xx"             //短信内容
}]
```

##示例代码1
```js
var bulksms = api.require('bulkSMS');
//小张会收到:祝小张新年快乐郭xx
//小王会收到:郭xx祝小王新年快乐
var params = {
            	users: [
	                {
	                    "phoneNumber": "135xxxxxxxx",
	                    "disPlayName": "小张"
	                },
	        		
	                {
	                    "phoneNumber": "134xxxxxxxx",
	                    "disPlayName": "小王"
	                }
	            ],
	            strcontents: [
	                "祝#disPlayName#新年快乐#name#",
	                "#name#祝#disPlayName#新年快乐",
	                "祝新年快乐"
	            ],
	            name: "郭xx"
        	};
			
bulksms.sends(params,function(ret,err){
	if(ret.results == "0"){
		//var time = setInterval("send();", 60*60*1000);
		alert("短信群发送成功");
	}else{
		alert(ret.info);
	}
});
```

##示例代码 2
```js
//利用contact模块获取到通讯录所有人信息
var contacts = null;
var contact = api.require('contact');
		
		contact.queryContact({
			
		},function(ret,err) {
		    if(ret.status) {
		        contacts =ret.contacts;      
		    } else{
		        api.alert({msg:'获取失败'});
		    }
		});
//给通讯录所有人发短信
var bulksms = api.require('bulkSMS');

var params = {
            	users: contacts,
	            strcontents: [
	                "祝#disPlayName#端午快乐#name#",
	                "#name#祝#disPlayName#端午快乐",
	                "祝端午快乐"
	            ],
	            name: "郭xx"
        	};
			
bulksms.sends(params,function(ret,err){
	if(ret.results == "0"){
		//var time = setInterval("send();", 60*60*1000);
		alert("短信群发送成功"+JSON.stringify(ret));
	}else{
		alert(ret.info);
	}
});
```



##补充说明
有些机型会有限制比如1小时内最多发送100条，需要设置手机具体的设置看使用的设备说明。也可以每次发送不超过限制规定时间后继续发送。
contacts内容具体详见：http://docs.apicloud.com/%E7%AB%AFAPI/%E8%AE%BE%E5%A4%87%E8%AE%BF%E9%97%AE/contact

##可用性

Android系统

可提供的1.0.0及更高版本


#**stop**<div id="a2"></div>

停止正在发送的短信

stop()

##示例代码

```js
//利用contact模块获取到通讯录所有人信息
var contacts = null;
var contact = api.require('contact');
		
		contact.queryContact({
			
		},function(ret,err) {
		    if(ret.status) {
		        contacts =ret.contacts;
		    } else{
		        api.alert({msg:'获取失败'});
		    }
		});
var bulksms = api.require('bulkSMS');
var params = {
            	users: contacts,
	            strcontents: [
	                "祝#disPlayName#新年快乐#name#",
	                "#name#祝#disPlayName#新年快乐",
	                "祝新年快乐"
	            ],
	            name: "郭xx"
        	};

bulksms.sends(params,function(ret,err){
	if(ret.results == "0"){
		//var time = setInterval("send();", 60*60*1000);
		alert("短信群发送成功");
	}else{
		alert(ret.info);
	}
});

bulksms.stop();
```

##补充说明

已发送成功的无法中断

##可用性

Android系统

可提供的1.0.0及更高版本