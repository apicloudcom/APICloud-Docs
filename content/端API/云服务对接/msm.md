/*
Title: msm
Description: msm
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[getAuthInfo](#1)

[certApply](#2)

[certVerify](#3)

[login](#4)
</div>

#**概述**

msm模块提供身份认证相关功能，开启认证以及认证方式可以在云端网站上面配置，此模块功能目前只对企业开放

#**getAuthInfo**

获取认证信息

getAuthInfo(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true,       			//操作成功状态值
	result:
    {
		msg:'success!',  		//说明
		authType:0,   			//认证方式（0无需认证、1手动认证、2自动认证）
		authStatus:0,    		//认证状态（0未认证、1已认证、2未申请、3黑名单）
		fields:
		{
			email:true,   		//邮箱是否必填
			name:true,     		//姓名是否必填
			group:true,     	//分组是否必填
			description:true,  	//申请说明是否必填
			photo:true,     	//证件照是否必填
		}
		groups:         		//分组数据，数组类型
    	[
			"group1","group2"
    	]
    }
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:''    //错误描述
}
```

##补充说明

获取认证信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**certApply**

证书申请

certApply({params}, callback(ret, err))

##params

email：

- 类型：字符串
- 默认值：无
- 描述：邮箱，不能为空

name：

- 类型：字符串
- 默认值：无
- 描述：姓名

group：

- 类型：字符串
- 默认值：无
- 描述：分组

description：

- 类型：字符串
- 默认值：无
- 描述：申请说明

photo：

- 类型：字符串
- 默认值：无
- 描述：证件照

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:''    //错误描述
}
```

##补充说明

证书申请

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**certVerify**

认证码验证

certVerify({params}, callback(ret, err))

##params

authCode：

- 类型：字符串
- 默认值：无
- 描述：认证码，不能为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:''    //错误描述
}
```

##补充说明

认证码验证

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**login**

登录

login({params}, callback(ret, err))

##params

userName：

- 类型：字符串
- 默认值：无
- 描述：用户名，不能为空

password：

- 类型：字符串
- 默认值：无
- 描述：密码，不能为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:''    //错误描述
}
```

##补充说明

登录

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
