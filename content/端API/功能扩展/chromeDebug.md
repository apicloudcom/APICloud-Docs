/*
Title: chromeDebug
Description: chromeDebug
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
    
</ul>
<div id="method-content">

<div class="outline">

[openDebug](#1)

[closeDebug](#2)

[错误码](#3)

</div>



##**概述**

在智能手机还未普及时，移动设备的调试处处是 alert 的，这估计是最常用的办法了。

移动互联网的浪潮，伴随着智能硬件的兴起与移动设备的普及，让前端工程师这个职业变得更为专业，这里主要说一下 Chrome DevTools 调试移动设备 Brower Page Tabs/WebViews。

准备工作

1. chrome 浏览器，最好 47+ 的版本

2. 一条 USB 数据线，连接电脑与移动设备，安装相应机型的 USB 驱动。如果电脑上安装有百度手机助手、360手机助手这类软件，一般连接后可以自动安装相应的USB驱动程序。[驱动程序下载地址](http://developer.android.com/tools/extras/oem-usb.html),

3. 手机系统为 Android 4.4+ 

##第一步：

首先在移动设备上开启 USB 调试模式

##第二步：

用 USB 数据线连接设备，驱动装好连接成功后，你可能会在设备上看到一个弹框请求允许使用这台计算机通过 USB 调试勾选后点击 "确定"

##第三步：

1. 在电脑上打开 Chrome 浏览器，在浏览器地址栏输入 chrome://inspect

2. 打开后 DevTools 后，确保打钩选中 Discover USB devices

3. 也许第一次需要翻墙加载一些插件，不过，你值得拥有

4. 如果还有问题，请看更详细的使用手册，[传送门](https://github.com/bringmehome/chromeDebug)



#**openDebug**<div id="1"></div>

打开 chrome 调试 HTML5 页面的开关

openDebug(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    result: 'success'      //是否成功
    code: 1000             //打开成功
}
```

##示例代码

```js
var chromeDebug = api.require('chromeDebug');
chromeDebug.openDebug(function(ret, err) {
    if (212 == ret.code) {
        alert(JSON.stringify(ret));
    } else {
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无   

##可用性

Android 系统

可提供的1.0.0及更高版本


#**closeDebug**<div id="2"></div>

关闭 chrome 调试 HTML5 页面的开关，虽然一般也用不到。

closeDebug(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    result: 'success'     //是否成功，布尔类型
    code: 1000            //打开成功
}
```

##示例代码

```js
var chromeDebug = api.require('chromeDebug');
chromeDebug.closeDebug(function( ret, err) {
    if (212 == ret.code) {
        alert(JSON.stringify(ret));
    } else {
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版

#**错误码**<div id="3"></div>

1. 1000 请求成功

2. 212 手机的 Android 版本低于4.4，不支持此功能