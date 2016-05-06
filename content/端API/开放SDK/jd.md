/*
Title: jd
Description: jd
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
</div>
<div class="outline">
[login](#1)
</div>

#**概述**

jd模块封装了京东授权登录SDK，使用之前需要去[京东云网站](http://jos.jd.com)创建应用。

使用时可以通过login方法以参数的形式将appKey、appSecret等信息传进去，也可以在[config.xml](/APICloud/技术专题/app-config-manual)里面进行配置，模块会优先使用方法里面传进去的信息。

**[config.xml](/APICloud/技术专题/app-config-manual)配置示例如下：**

    <feature name="jd">
        <param name="appKey" value="F7E188290D59BD58FDA262E03A355542" />
        <param name="appSecret" value="a13d7611c4f4498ea79d95e861a5a554" />
        <param name="redirectUri" value="http://yunsmart.com" />
        <param name="naviColor" value="#f00" />
    </feature>

#**login**<div id="1"></div>

登陆授权

login({parmas},callback(ret, err))

##params

appKey：

- 类型：字符串
- 默认值：无
- 描述：（可选项）从京东云网站申请的app key

appSecret：

- 类型：字符串
- 默认值：无
- 描述：（可选项）从京东云网站申请的app secret

redirectUri：

- 类型：字符串
- 默认值：无
- 描述：（可选项）从京东云网站创建应用时填写的redirect uri

naviColor：

- 类型：字符串
- 默认值：#f00
- 描述：（可选项）导航栏背景颜色，支持#、rgb、rgba等格式

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	uid:				//用户ID，字符串类型
	nickname:			//昵称，字符串类型
	accessToken:		//授权Token，字符串类型
	refreshToken:		//刷新Token，字符串类型
	expires:			//失效时间，单位秒，数字类型
	time:				//在此时间内允许重置token，单位毫秒，数字类型
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

##示例代码

    var jd = api.require('jd');
    jd.login({
        appKey:'F7E188290D59BD58FDA262E03A355542',
        appSecret:'a13d7611c4f4498ea79d95e861a5a554',
        redirectUri:'http://yunsmart.com',
        naviColor:'#f00'
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
