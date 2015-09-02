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
[logout](#2)
[getInfo](#3)
</div>

#**概述**

baidu模块封装了百度授权登录SDK，通过调用本模块可实现百度账号登陆授权的功能。使用之前需要到百度（http://developer.baidu.com/console#app/project）创建应用。可以通过login接口以参数的形式将apiKey传进去，也可以在config.xml里面配置，模块会优先使用接口里传入的apiKey。建议通过config.xml配置apiKey

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
- 描述：（可选项）从百度申请的apiKey
- 备注：若不传则从config.xml文件内读取改参数

force：

- 类型：布尔类型
- 默认值：true
- 描述：（可选项）是否强制登录（若本字段为false，则logout后再login时直接返回token、uid等信息；若为true则再次login时跳转到登陆页面）

confirm

- 类型：布尔类型
- 默认值：true
- 描述：（可选项）是否确认登录（logout后再login是否显示授权确认页面）
- 备注：login过程包括显示登陆页面和授权确认页面，若本参数为false则每次登陆都会显示上述两个页面，若本参数为true则再次login时只显示登陆页面不显示授权确认页面，**本参数仅android上适用，ios平台上忽略**

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   status:       //布尔类型；登陆是否成功
   userInfo:     //JSON对象；登陆成功后获取到的用户信息及其token
                   内部字段如下：{
                       uid:         //字符串类型；用户的ID
                       uname:       //字符串类型；用户的昵称，可能为空
                       portrait:    //字符串类型；用户的头像地址，可能为空
                       accessToken: //字符串类型；百度分配的登陆token值
                   }

}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	code:         //数字类型；错误码
	               取值范围如下：
	                  -1://未知错误
	                   0://登陆成功
	                   1://apiKey值非法
	                   2://账号或密码错误
	                   3://用户取消登陆
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

退出登录授权状态

logout()

##示例代码

```js
    var baidu = api.require('baidu');
    baidu.logout();
```

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
- 描述：（可选项）从百度申请的apIkey，若不传则从config.xml文件内读取该参数

accessToken：

- 类型：字符串
- 默认值：无
- 描述：登录后获得的accessToken


##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   status:        //布尔值，是否获取用户信息成功
   userInfo:      //JSON对象，获取到的用户信息，内部字段如下:{
                    userid:      //字符串类型；当前登录用户的ID
                    username:    //字符串类型；当前登录用户的用户名，可能为空
                    realname:    //字符串类型；当前登录用户的真实姓名，可能为空
                    portrait:    //字符串类型；当前登录用户的头像url，可能为空
                    userdetail:  //字符串类型；当前登录用户的自我简介，可能为空
                    birthday:    //字符串类型；当前登录用户的生日，以yyyy-mm-dd格式显示，可能为空
                    marriage:    //字符串类型；当前登录用户的婚姻状况，可能为空
                    sex	:        //字符串类型；当前登录用户的性别，可能为空
                    blood:       //字符串类型；当前登录用户的血型，可能为空
                    figure:      //字符串类型；当前登录用户的体型，可能为空
                    education:   //字符串类型；当前登录用户的学历，可能为空
                    trade:       //字符串类型；当前登录用户的当前职业，可能为空
                  }
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
		code:         //数字类型；错误码
	                   取值范围如下：
		                  -1://未知错误
		                   0://获取信息成功
		                   1://apiKey值非法
		                   2://accessToken值过期
		                   3://accessToken值非法
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
