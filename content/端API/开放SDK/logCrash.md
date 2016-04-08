/*
Title: logCrash
Description: logCrash
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
</div>

<div class="outline">
[listenCrash](#a1)
</div>

#**概述**

logCrash封装了腾讯平台的监听log功能，使用此模块可轻松实现对已经发布APP的闪退的日志，方便开发者针对闪退日志与apicloud官方或者自己进行对已发布APP的维护
使用此模块之前必须先配置 config 文件，配置方法如下：

名称：BugId

参数：android_id、ios_id

备注：同一个 App 需要同时支持 iOS 和 Android 平台，必须单独申请各自的 apiKey，并同时配置在 config 文件中。

配置示例:

```
  <feature name="BugId">
    <param name="android_id" value="123456789" />
    <param name="ios_id" value="123456789" />
  </feature>
```

字段描述:

android_id：在腾讯平台申请的针对安卓应用监听的ID

ios_id：在腾讯平台申请的针对IOS应用监听的ID

ID申请地址http://bugly.qq.com/

如需帮助可以在论坛发帖，标题要以BUG开头，我会每天查看论坛帮大家解答，也可以发送疑问到邮箱zd_logbug@163.com。


#**listenCrash**<div id="a1"></div>

注册监听事件

listenCrash()


##示例代码

```js
var LogMoudle = api.require('logCrash');
LogMoudle.listenCrash();
```

##补充说明

当发布的APP出现闪退之后，开发者可以通过官方网站http://bugly.qq.com/，进入自己的管理界面，然后选择对应的app来查看具体的闪退原因，以及闪退对应的手机型号
以及其他手机的信息，方便开发者进行总结及修正。

如果在测试过程中没有在后台监听到闪退信息，那么就是由于申请的ID的填写不正确造成的，也正是这个原因，无法返回回调函数，希望大家谅解，使用方法，在需
要监听的界面oncreat方法里面调用模块即可。
监听应用闪退LOG日志,最常见的是空指针等日志，会将详细信息：闪退手机型号、闪退时的磁盘占用率、闪退手机的当前手机版本、SD卡的占用率、手机是否root过、
闪退时候的内存占用比例，以及出错代码的详细行数全部显示给模块使用者，方便开发者拿到日志之后和apicloud官方进行及时沟通并纠正错误，并及时发布修正版。


##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
