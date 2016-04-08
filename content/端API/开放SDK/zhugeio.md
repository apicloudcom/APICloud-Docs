/*
Title: zhugeio
Description: zhugeio
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">
[identify](#a1)

[track](#a2)
</div>

#**概述**

zhugeio封装了zhugeio精细化运营分析工具SDK，使用此模块可轻松实现精细化运营分析。  (请使用本模块升级版[zhuge](http://docs.apicloud.com/%E7%AB%AFAPI/%E5%BC%80%E6%94%BESDK/zhuge)，支持Android和IOS双平台。本模块已停止更新)

###**配置选项**<div id="a2"></div>
需在config.xml中配置:

```js
<feature name="zhugeio">
    <param name="zhugeio_APPKEY" value="apikey_001"/>
    <param name="zhugeio_CHANNEL" value="channel_001"/>
</feature>
```

zhugeio_APPKEY和zhugeio_CHANNEL为必填选项

#**identify**<div id="a1"></div>

用户身份识别 
为了把页面访问、自定义事件等记录的用户行为与每个用户关联起来，需要通过identify方法来识别用户信息，您可以通过该方法记录用户的自定义ID和详细信息，通常在登录后调用一次该方法即可。

identify({params})

##params

uid：

- 类型：字符串
- 默认值：无
- 描述：用户id，不能为空

预定义的属性：
name	    名称
gender	    性别(值:男,女)
birthday	生日(格式: yyyy/MM/dd)
avatar	    头像地址
email	    邮箱
mobile	    手机号
qq	        QQ账号
weixin	    微信账号
weibo	    微博账号
location	地域(如:北京)

##示例代码

```js
var zhugeio = api.require('zhugeio');
zhugeio.identify({
	uid: 'uid_001',
	qq:'3024149',
	email:'rlliang@37degree.com',
	mobile: '18210484266'
});
```

##补充说明
无

##可用性
Android系统
可提供的1.0.0及更高版本

#**track**<div id="a2"></div>

自定义的事件
自定义事件用于记录用户行为，例如购买道具、点击某个按钮等用户行为都可以通过一个事件来记录，还可以通过事件的属性来描述发生的场景或具体细节。

track({params})

##params

event_name：

- 类型：字符串
- 默认值：无
- 描述：事件名，不能为空

##示例代码

```js
var zhugeio = api.require('zhugeio');
zhugeio.track({
	event_name: '购买手机',
    手机: '小米4',
    价格: 1799,
    运营商: '移动'
});
```

##补充说明
无

##可用性
Android系统
可提供的1.0.0及更高版本


