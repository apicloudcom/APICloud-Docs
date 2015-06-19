/*
Title: baidu
Description: baidu
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[login](#1)
</div>

#**概述**

baidu模块封装了百度授权登录SDK等，使用之前需要到百度（http://developer.baidu.com/console#app/project）创建应用。

使用时可以通过login方法以参数的形式将apiKey传进去，也可以在config.xml里面进行配置，模块会优先使用方法里面传进去的信息。

**config.xml配置示例如下：**

    <feature name="baidu">
        <param name="apiKey" value="0trswTLaGB6hN820M30Brbhx" />
    </feature>

#**login**<div id="1"></div>

登陆授权

login({parmas},callback(ret, err))

##params

apiKey：

- 类型：字符串
- 默认值：无
- 描述：（可选项）从百度申请的apIkey

isForceLogin：

- 类型：布尔类型
- 默认值：true
- 描述：（可选项）是否强制登录（注销后再登录发生效果）

isConfirmLogin

- 类型：布尔类型
- 默认值：true
- 描述：（可选项）是否确认登录（注销后再登录发生效果）

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	uid:			//用户ID，字符串类型
	uname:			//昵称，字符串类型
	portrait:		//头像地址，字符串类型
	accessToken:	//accessToken
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''    //错误描述
}
```

##示例代码

    var baidu = api.require('baidu');
    baidu.login({
        apiKey:'0trswTLaGB6hN820M30Brbhx',
    },function(ret,err){
        if(ret){
            alert(JSON.stringify(ret));
        }else{
            alert(JSON.stringify(err));
        }
    });

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**logout**<div id="2"></div>

清除accessToken

logout()

##示例代码

    var baidu = api.require('baidu');
    baidu.logout();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getInfo**<div id="3"></div>

获取用户详细信息

getInfo({parmas},callback(ret, err))

##params

apiKey：

- 类型：字符串
- 默认值：无
- 描述：（可选项）从百度申请的apIkey

accessToken：

- 类型：字符串
- 默认值：无
- 描述：登录后获得的accessToken


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	userid			//当前登录用户的数字ID
	username		//当前登录用户的用户名，值可能为空
	realname		//用户真实姓名，可能为空。
	portrait		//当前登录用户的头像url
	userdetail		//自我简介，可能为空
	birthday		//生日，以yyyy-mm-dd格式显示
	marriage		//婚姻状况
	sex				//性别
	blood			//血型
	figure			//体型
	education		//学历
	trade			//当前职业
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''    //错误描述
}
```

##示例代码

    var baidu = api.require('baidu');
    baidu.getInfo({
      accessToken:'23.d066380144827c5411ee0bd78b9d38f6.2592000.1436063436.739729233-6094198',
    },function(ret,err){
        if(ret){
            alert(JSON.stringify(ret));
        }else{
            alert(JSON.stringify(err));
        }
    });

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
