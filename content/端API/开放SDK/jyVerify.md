/*
Title: jyVerify
Description: jyVerify
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
</div>

<div class="outline">
[showPicVal](#a1)
</div>

#**概述**

jyVerify封装了极验验证平台的SDK，使用此模块可轻松实现图片拖动验证，并获取到用户验证的具体时间。暂仅支持Android。

使用此模块之前必须先配置 config 文件,配置方法如下:

名称:JYYZ

参数:android_id

配置示例:

```
 <feature name="JYYZ"> 
    <param name="android_id" value="8888888888888888888888"/> 
  </feature>
```

字段描述:

android_id: 在极验验证平台申请的ID

申请流程:
首先进入极验验证官网，然后进行注册登录，进入管理界面之后，点击左边的验证管理，然后点击添加验证，网站名，网站地址自己随意输入，终端类型选择
移动端，后台代码类型选择java，然后点击声称安装代码，生成之后在验证管理界面会出现刚刚注册的应用的信息，将ID复制下载填写进入config文件中即可。


#**showPicVal**<div id="a1"></div>

拖动图片验证信息

showPicVal(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:done,                 //操作成功状态值
	geetest_challenge:******, //用于向客户服务器提交之后的SDK二次验证信息
	geetest_validate:******,  //用于向客户服务器提交之后的SDK二次验证信息
	geetest_seccode:******    //用于向客户服务器提交之后的SDK二次验证信息
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code:0                   //用户点击返回按钮取消验证
}
```

##示例代码

```js
var JYskd = api.require('jyVerify');
JYskd.showPicVal(function(ret, err) {
	if (ret.msg == "done") {
		api.alert({
			msg : '' + ret.geetest_challenge + '-' + ret.geetest_validate + '-' + ret.geetest_seccode
		});
	} else {
		api.alert({
			msg : err.errmsg
		});
	}
});
```

##补充说明

拖动图片进行验证 并获取用户验证的详细时间以及是否成功。

##可用性

Android系统

可提供的1.0.0及更高版本

