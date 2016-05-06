/*
Title: pingModule
Description: pingModule
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
	<li><a href="#const-content">常量</a></li>
</ul>
<div id="method-content">

<div class="outline">
[ping](#a1)

[pingTest](#a2)
</div>

#**概述**

pingModule1.0.0版本目前封装了ping的测试能力，使用此模块可轻松实现单个ping功能和ping测试功能。

#**ping**<div id="a1"></div>

获取ping某一个IP或者域名的结果，可以通过该方法判断是否可以和服务器交互. 

ping({params}, callback(ret, err))

##params

target：

- 类型：字符串
- 默认值：无
- 描述：目标主机IP或者域名，不能为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	 status: //操作成功状态值 true表示可以ping通，false表示无法ping通。
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
   	code:       //错误代码 参考错误代码
	msg:""		//错误描述
}
```

##示例代码

```js
var pingModule = api.require('pingModule');
var targethost = "www.baidu.com";
pingModule.ping({
		target:targethost
	},
	function(ret,err) {
		if(ret) {
			api.alert({msg: JSON.stringify(ret)});
			return;
		}
		if(err) {
			api.alert({msg: err.msg});
		}
	}
);
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

#**pingTest**<div id="a2"></div>

执行ping测试，默认执行5次ping测试,并返回每一个的执行结果

pingTest({params}, callback(ret, err))

##params

target：

- 类型：字符串
- 默认值：无
- 描述：目标主机IP或者域名，不能为空

size:

- 类型：字符串
- 默认值：64
- 描述：ping测试的字节数，默认为64B 

time:

- 类型：整型
- 默认值：5
- 描述：ping测试的次数，默认为5次

timeout:

- 类型：整型
- 默认值：5
- 描述：ping测试的超时时间，默认为5毫秒

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true		//操作成功状态值 布尔类型	
	time: 			//返回每次ping测试的延时结果 单位为ms
	sumtime：   		//返回ping测试的总延时结果 单位为ms
	avgtime：   		//返回ping测试的平均延时结果 单位为ms
	successtimes：  //ping命令执行成功次数
	failtimes:      //ping命令执行失败次数
	pingloss:		//ping命令执行丢失包百分比 数值为					  			  failtime/(successtimes + failtimes)
	ttl:            //TTL是IPv4包头的一个8 bit字段
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
   	code:       //错误代码 参考错误代码
	msg:""		//错误描述
}
```

##示例代码

```js
var pingModule = api.require('pingModule');
var targethost = "www.baidu.com";
var size = 64;
var time = 5;
var timeout = 5;
pingModule.pingTest({
		target:targethost,
		size:size,
		time:time,
		timeout:timeout
	},
	function(ret,err) {
		if(ret) {
			if(err) {
				api.alert({msg: "ret " + JSON.stringify(ret) + "err " + JSON.stringify(err)});
				return;
			} 
			api.alert({msg: JSON.stringify(ret)});
			return;
		}
		if(err) {
			api.alert({msg: err.msg});
		}
	}
);
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

</div>

<div id="const-content">

<div class="outline">
[错误码](#1)
</div>

#**错误码**<div id="1"></div>

####取值范围：
- 1		//请求超时
- 2		//未知主机地址
- 3		//错误:连接失败
- 4		//连接中断
- 5  	//无法读出数据
- 6  	//JS传递的主机参数为空
- 99	//其他错误 参考msg
