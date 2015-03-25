/*
Title: sms
Description: sms
*/
<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[startActivityForResult](#startActivityForResult)

</div>
# 概述 #

本模块是一款实现手机短信验证的模块,该模块自带一个界面。本模块封装了短信验证的相关接口。使用此模块之前需要先去[http://mob.com/sms](http://mob.com/sms)注册获取appkey和appsecret


## startActivityForResult<div id="startActivityForResult"></div>
初始化短信页面

startActivityForResult  (params, callback)

## params ##
appkey：

- 类型：字符串
- 默认值：“”
- 描述：从官方网站获取唯一标志

appsecret：

- 类型：字符串
- 默认值：“”
- 描述：从官方网站获取唯一标志

### 示例代码 ###

```js
var sms = api.require('sms');

sms.startActivityForResult({appkey:" ",appsecret:" "});
```	

### 可用性 ###

Android系统

可提供的 1.0.0 及更高版本