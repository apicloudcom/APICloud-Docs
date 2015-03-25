/*
Title: 应用配置说明
Description: 应用配置说明
Sort: 1
*/


[Overview](#1)

- [概述](#2)
- [配置清单描述](#3)

[Preference](#4)

- [配置App全局背景](#5)
- [配置Window默认背景](#6)
- [配置Frame默认背景颜色](#7)
- [配置页面是否弹动](#7-0)
- [配置页面默认是否显示滚动条](#8)
- [配置启动页是否自动隐藏](#9)
- [配置IOS7状态栏和页面是否重合](#10)
- [配置应用是否全屏运行](#11)
- [配置应用是否自动检测更新](#12)
- [配置应用是否支持增量更新、云修复](#13)
- [配置应用开启/关闭调试模式](#14)
- [配置键盘弹出方式](#14-0)

[Feature](#15)

- [微信](#16)
- [新浪微博](#17)
- [百度定位](#18)
- [百度地图](#19)
- [支付宝支付](#20)
- [QQ登录/分享](#21)
- [极光推送](#21-0)
- [融云即时通信](#21-1)

[Permission](#22)

- [读取手机状态和身份](#23)
- [直接拨打电话](#24)
- [直接发送短信](#25)
- [使用拍照和视频](#26)
- [使用录音](#27)
- [访问地理位置信息](#28)
- [访问文件系统](#29)
- [完全的访问网络权限](#30)
- [开机启动](#31)
- [控制振动/闪光灯/屏幕休眠等硬件设备](#32)
- [访问设备通讯录](#33)

[Font](#34)

[Reference](#35)

#**Overview**
<div id="1"></div>

#**概述**
<div id="2"></div>

每一个Widget 包必须有一个名为 config.xml （大小写敏感）的配置文件，它位于Widget包的根目录下。该配置文件包含了关于该Widget的重要信息，如：名称、作者信息、描述、云端ID、偏好设置、权限配置、模块概览等等，并且该配置文件也是整个Widget的入口。

一个简单的config.xml文件配置清单如下：

```js
<widget id="A12345678901"  version="0.0.1">
    <name>API Example</name>
    <description>
        API Example App.
    </description>
    <author email="developer@apicloud.com" href="http://www.apicloud.com">
        APICloud.SIR
    </author>
    <content src="index.html" />
    <access origin="*" />
	<preference name="windowBackground" value="#FFF" />
    <permission name="call" />
    <feature name="weiXin">
		<param name="urlScheme" value="wx7779c7c063a9d4d9" />
	</feature>
</widget>
```

`注：该XML文件必须采用UTF-8编码。`

##配置清单描述
<div id="3"></div>

widget父元素描述了该Widget的基本属性，如表1所示。
<br>
- 表1. widget父元素的属性

<table>
    <tr>
        <th>属性名</th>
        <th width="70%">描述</th>
        <th>备注</th>
    </tr>
    <tr>
        <td>id</td>
        <td>应用ID，由云服务器自动分配。它是该Widget在云端的唯一标识。云服务器根据此ID对Widget进行管理并提供辅助服务，如：更新升级、统计分析、推送服务等。</td>
        <td>必选</td>
    </tr>
    <tr>
        <td>version</td>
        <td>Widget的版本号</td>
        <td>必选</td>
    </tr>
    <tr>
        <td>sandbox</td>
        <td>配置此属性后，APICloud应用在运行之初，将会在设备的SD卡上建立与此属性同名的文件夹根目录，并将该目录默认为本应用的沙箱根路径，此后应用运行过程中所有涉及的文件操作如：文件读写，拍照、下载等等，操作结果的文件都将存放在该路径下。该属性仅Android平台生效</td>
        <td>可选</td>
</table>

配置中的XML元素如表2所示。

- 表2. Widget配置元素

<table>
    <tr>
        <th>元素名</th>
        <th width="70%">描述</th>
        <th>备注</th>
    </tr>
    <tr>
        <td>name</td>
        <td>Widget的名称。如：QQ、新浪微博、微信等</td>
        <td>必选</td>
    </tr>
    <tr>
        <td>description</td>
        <td>Widget的简单描述信息</td>
        <td>可选</td>
    </tr>
    <tr>
        <td>author</td>
        <td>Widget的作者信息</td>
        <td>可选</td>
    </tr>
    <tr>
        <td>content</td>
        <td>Widget运行的起始页，支持相对/绝对路径</td>
        <td>必选</td>
    </tr>
    <tr>
        <td>access</td>
        <td>Widget允许访问的资源范围。一般配置“*”，代表允许访问所有</td>
        <td>可选</td>
    </tr>
    <tr>
        <td>preference</td>
        <td>偏好设置。配置Widget的一些运行时属性，如：页面是否支持弹动效果、窗口默认背景、页面是否显示滚动条等。该配置可在IDE的GUI界面中选择并使用。详细请参考<a href="#1">Preference Guide</a></td>
        <td>可选</td>
    </tr>
    <tr>
        <td>permission</td>
        <td>权限配置。通过此配置向系统声明Widget所用到的系统权限。如：直接拨打电话、直接发送短信、发起定位等。该配置可在IDE的GUI界面中选择并使用。详细请参考<a href="#2">Platform Permission</a></td>
        <td>必选</td>
    </tr>
    <tr>
        <td>feature</td>
        <td>功能配置。通过此配置，向系统声明需要使用哪些功能，以及需要传递给该功能的数据。如：使用新浪微博、使用微信分享等。该配置可在IDE的GUI界面中选择并使用。详细请参考<a href="#3">Feature Guide</a></td>
        <td>可选</td>
    </tr>
    <tr>
        <td>font</td>
        <td>字体配置。通过此配置，将自定义字体加入到应用中，使其可以在前端页面使用该字体</td>
        <td>可选</td>
    </tr>
</table>

#**Preference**<div id="4"></div>

Preference用于声明本应用的一些全局设置或者属性，该字段以键值对的形式存在。APICloud应用在启动及运行过程中会随时参考这些属性，以达到应用运行的最优状态。

##配置App全局背景<div id="5"></div>

字段名：appBackground

取值范围：	

- 颜色：#FFF，#FFFFFF，rgb(255,255,255)，rgba(255,255,255,1.0)；
- 图片：相对widget包路径的url地址，如image/xxx.png

默认值：rgba(0,0,0,0.0)

描述：配置App的背景颜色或图片，默认为透明色。配置此字段后，如果window的背景为透明色，则将透射出App背景。APICloud应用的UI层次结构见图1.

配置示例： ```<preference name="appBackground" value="color|imageUrl" />```

图1.APICloud应用UI层次结构图：

![图片说明](/img/docImage/48.png)
 
若WindowBackground为透明，那么Window将展示App的背景，同时如果FrameBackground也为透明，那么Frame将展示App的背景。

##配置Window默认背景<div id="6"></div>

字段名：windowBackground

取值范围：

- 颜色：#FFF，#FFFFFF，rgb(255,255,255)，rgba(255,255,255,1.0)；
- 图片：相对widget包路径的url地址，如image/xxx.png

默认值：rgba(0,0,0,0.0)

描述：配置Window的背景颜色或图片，默认为透明色。配置此字段后，所有open的Window都会使用该背景，可提高开发效率、节省系统资源、加速渲染速度。

配置示例：```<preference name="windowBackground" value="color|imageUrl" />```

##配置Frame默认背景<div id="7"></div>

字段名：frameBackgroundColor

取值范围：

- 颜色：#FFF，#FFFFFF，rgb(255,255,255)，rgba(255,255,255,1.0)；
- 图片：相对widget包路径的url地址，如image/xxx.png

默认值：rgba(0,0,0,0.0)

描述：配置Frame的背景颜色或图片，默认为透明色。此字段的配置效果等同于对网页的body标签设置background-color。

配置示例：```<preference name="frameBackgroundColor" value="color" />```

##配置页面是否弹动<div id="7-0"></div>

字段名：pageBounce

取值范围：true|false

默认值：window默认为false，frame默认为true

描述：配置页面是否可以弹动。若不配置，window默认不弹动，frame默认可以弹动；若配置，则window和frame是否可以弹动默认都以此配置的为准。

配置示例：```<preference name="pageBounce" value="false" />```


##配置页面默认是否显示滚动条<div id="8"></div>

字段名：hScrollBarEnabled | vScrollBarEnabled

取值范围：true|false

默认值：true

描述：配置在页面高度超出视图高度时，window|frame是否显示横|竖滚动条。默认显示。

配置示例：

```js
横向滚动条：
		<preference name="hScrollBarEnabled" value="true|false" />
竖直滚动条：
		<preference name="vScrollBarEnabled" value="true|false" />
```
##配置启动页是否自动隐藏<div id="9"></div>

字段名：autoLaunch

取值范围：true|false

默认值：true

描述：APICloud应用在启动时向用户展示一个启动界面，并控制该启动界面在适当的时候隐藏。如该字段置为false，则启动页需要开发者自行调相关接口关闭(api.removeLaunchView)。置为true，则引擎自动关闭。默认显示3秒后关闭，如3秒内网页未加载完毕则一直等待，直到网页加载完毕再关闭启动页。

配置示例：```<preference name="autoLaunch" value="true|false" />```

##配置IOS7状态栏和页面是否重合<div id="10"></div>

字段名：iOS7StatusBarAppearance

取值范围：true|false

默认值：true

描述：配置IOS7及以上系统中，页面是否和状态栏重合，表现效果为系统的状态栏将以半透的形式覆盖在当前应用上。仅IOS7以上系统起作用

配置示例：```<preference name="iOS7StatusBarAppearance" value="true|false" />```

##配置应用是否全屏运行<div id="11"></div>

字段名：fullScreen

取值范围：true|false

默认值：false	

描述：配置应用是否全屏运行。如果该字段为true，应用将以全屏的方式启动，并以全屏方式运行。运行过程中可随时通过APICloud开放的API（api.setFullScreen）控制退出全屏或重新进入全屏。

配置示例：```<preference name="fullScreen" value="true|false" />```

##配置应用是否自动检测更新<div id="12"></div>

字段名：autoUpdate

取值范围：true|false

默认值：true	

描述：配置应用是否自动检测更新。如果该字段为true，应用在启动时将自动与云端握手，并检查本应用是否有更新，是否被强制关闭，是否强制更新等（以上控制可在云端“应用服务”中随时设置）。应用运行过程中会根据这些设置进行相关操作，如：自动下载、强制关闭应用等。

配置示例：```<preference name="autoUpdate" value="true|false" />```

##配置应用是否支持增量更新、云修复<div id="13"></div>

字段名：smartUpdate

取值范围：true|false

默认值：false	

描述：配置应用是否支持增量更新以及云修复。如果该字段为true，应用在启动时将自动与云端握手，并检查本应用当前版本下是否有增量包更新，是否需要进行云修复。应用运行过程中会根据这些设置进行相关操作，如：提示更新下载、静默更新下载等。

配置示例：```<preference name="smartUpdate" value="false" />```

##配置应用开启/关闭调试模式<div id="14"></div>

字段名：debug

取值范围：true|false

默认值：false  
      
描述：配置应用是否处于调试模式。如果该字段为true，标识应用进入调试模式，应用运行过程中发生的因代码书写失误等原因导致的Js报错（引起执行中断）信息，将会以弹窗的方式覆盖在应用最上方，供开发者参考。目前仅Android平台有效。

配置示例：```<preference name="debug" value="false" />```

##配置键盘弹出方式<div id="14-0"></div>

字段名：softInputMode

取值范围：resize、pan、auto. iOS平台resize和auto等效

默认值：auto  
      
描述：
 - resize：弹出键盘时会把页面往上推移;
 - pan：弹出键盘时页面不会被往上推移
 - auto：由系统根据输入框位置决定是否页面往上推移

配置示例：```<preference name="softInputMode" value="resize"/>```


#**Feature**<div id="15"></div>

Feature用于声明本应用使用到的平台扩展模块功能、第三方SDK等接入规范、运行时组件，并声明该模块默认需要传入的参数及值（param），每个Feature对应一个或多个参数值。APICloud应用通过这些模块为用户提供特定的功能。

##微信<div id="16"></div>

名称：weiXin

参数：urlScheme

描述：配置微信专用的URL Scheme，使得本应用可以启动微信客户端，并与之交换数据，同时可以从微信客户端返回到本应用

配置示例：

```js
<feature name="weiXin">
	<param name="urlScheme" value="wx7779c7c063a9d4d9" />
    <param name="apiKey" value="wx7779c7c063a9d4d9" />
	<param name="apiSecret" value="a354f72aa1b4c2b8eaad137ac81434cd" />
</feature>
```

字段描述：

1. param-urlScheme：声明此字段为URL Scheme类型
1. param-value：对应urlScheme类型的值。通过微信开放平台申请。用于从当前应用跳到微信后能够回到当前应用。
1. param-apiKey：在微信开放平台申请的apiKey，使用微信的开放接口，必须申请该key。
1. param-value：在微信开放平台申请的apiKey的值。

##新浪微博<div id="17"></div>

名称：sinaWeiBo

参数：urlScheme

描述：配置新浪微博专用的URL Scheme，以及apiKey，使得本应用可以启动新浪微博客户端，并与之交换数据，同时可以从新浪微博客户端返回到本应用

配置示例：

```js
<feature name="sinaWeiBo">
	<param name="urlScheme" value="wb1464272715" />
    <param name="apiKey" value="1464272715" />
</feature>
```

字段描述：

1. param-urlScheme：声明此字段为URL Scheme类型
1. param-value：对应urlScheme类型的值。通过新浪微博开放平台申请apiKey，再加上‘wb’前缀构成
1. param-apiKey：在新浪微博开放平台申请的apiKey，使用新浪微博的开放接口，必须申请该key。
1. param-value：在新浪微博开放平台申请的apiKey的值。
1. param-apiSecret: 通过微信开放平台申请的应用秘钥1. param-value: 此参数用于微信登录授权获取登录的accessToken

##百度定位<div id="18"></div>

名称：baiduLocation

参数：apiKey

描述：配置百度定位功能必须的apiKey，该key需要在百度开放平台申请，申请细则请参考[百度开放平台](http://lbsyun.baidu.com/apiconsole/key?application=key)相关文档。

配置示例：

```js
<feature name="baiduLocation">
	<param name="apiKey" value="fef72715gshjelke" />
</feature>
```

字段描述：

1. param-apiKey：声明此字段为apiKey类型
1. param-value：对应apiKey类型的值。在百度开放平台申请的apiKey

##百度地图<div id="19"></div>

名称：baiduMap

参数：apiKey

描述：配置百度地图模块必须的apiKey，该key需要在百度开放平台申请，申请细则请参考[百度开放平台](http://lbsyun.baidu.com/apiconsole/key?application=key)相关文档。

配置示例：

```js
<feature name="baiduMap">
	<param name="android_api_key" value="fef72715gshjelke" />
	<param name="ios_api_key" value="fef72715gshjelke" />
</feature>
```

字段描述：

1. param-apiKey：声明此字段为apiKey类型
1. param-value：对应apiKey类型的值。在百度开放平台申请的apikey，ios和android需要分别申请，并同时配入config文件中。

##支付宝支付<div id="20"></div>

名称：aliPay

参数：urlScheme

描述：配置支付宝专用的URL Scheme，使得本应用可以启动支付宝客户端，并与之交换数据，同时可以从支付宝客户端返回到本应用

配置示例：

```js
<feature name="aliPay">
	<param name="urlScheme" value="AliPay + widgetId" />
</feature>
```

字段描述：

- param-urlScheme：声明此字段为URL Scheme类型
- param-value：固定值，由字符串‘AliPay’和本应用的widgetId拼接而成。


##QQ登录/分享<div id="21"></div>

名称：qq

参数：urlScheme

描述：配置支付宝专用的URL Scheme，以及apiKey，使得本应用可以启动QQ客户端，并与之交换数据，同时可以从QQ客户端返回到本应用

配置示例：
```js
<feature name="qq">
	<param name="urlScheme" value="tencent123345678" />
	<param name="apiKey" value="123345678" />
</feature>
```

字段描述：

1. param-urlScheme：声明此字段为URL Scheme类型
1. param-value：对应urlScheme类型的值。由腾讯开放平台申请的apiKey和tencent前缀构成：tencent + apiKey。
1. param-apiKey：在腾讯开放平台申请的apiKey，使用腾讯的开放接口，必须申请该apiKey。
1. param-value：在腾讯开放平台申请的apiKey的值。

##极光推送<div id="21-0"></div>

名称：ajpush

参数：channel、app_key

描述：配置使用极光推送所需的app_key以及统计用的渠道号，app_key需要在极光推送官网申请，channel用于极光官网统计分发渠道

配置示例：
```js
<feature name="ajpush">
	<param name="channel" value="developer-apicloud" />
	<param name="app_key" value="2878d6d8bc2556b577a53e05" />
</feature>
```

字段描述：

1. param-channel：渠道号
1. param-value：渠道号值，任意自定义的字符串，字母+数字。默认为：developer-apicloud
1. param-app_key：在极光推送官网申请的appKey。不可为空。
1. param-value：appKey值。

##融云即时通讯<div id="21-1"></div>

名称：rongCloud

参数：appKey

描述：配置融云开发者平台上申请的 App Key 值

配置示例：
```js
<feature name="rongCloud">
    <param name="appKey" value="此处填写App Key 值" />
</feature>
```

#**Permission**<div id="22"></div>

Permission用于声明本应用用到的所有系统权限。APPCloud开放的API接口以及提供的服务或者功能中，可能需要向操作系统申请某些权限，APPCloud将这些权限归类并抽象后提供给开发者，开发者通过简单的字段声明，APPCloud云端在编译应用时，将会判别permission字段并给应用安装包添加相应的系统权限（即应用安装时，系统向用户展示的权限列表）。

##读取手机状态和身份<div id="23"></div>

权限名称：readPhoneState

权限描述：允许该应用访问设备的电话功能。此权限可以让该应用确定本机号码和设备ID、是否处于通话状态以及拨打的号码

使用该权限的接口：api.ajax()、api.download()、api.getLocation()

是否敏感：否

配置示例：```<permission name="readPhoneState" />```

##直接拨打电话<div id="24"></div>

权限名称：call

权限描述：允许应用在用户未执行操作的情况下直接拨打电话号码。此权限可能会导致意外收费或呼叫。此权限不允许该应用拨打紧急电话号码。

使用该权限的接口：api.call()

是否敏感：是

配置示例：```<permission name="call" />```

	
##直接发送短信<div id="25"></div>

权限名称：sms

权限描述：允许该应用在用户不知情的情况下直接发送短信。此权限可能会导致意外收费。

使用该权限的接口：api.sms()

是否敏感：是

配置示例：```<permission name="sms" />```

##使用拍照和视频<div id="26"></div>

权限名称：camera

权限描述：允许该应用使用相机拍摄照片和视频。此权限可以让应用随时使用相机，而无需用户确认。

使用该权限的接口：api.getPicture()

是否敏感：否

配置示例：```<permission name="camera" />```

##使用录音<div id="27"></div>

权限名称：record

权限描述：允许该应用访问设备的麦克风，并进行录音。该权限可能导致用户隐私的泄露。

使用该权限的接口：api.startRecord()

是否敏感：否

配置示例：```<permission name="record" />```

##访问地理位置信息<div id="28"></div>

权限名称：location

权限描述：允许该应用访问位置提供程序根据GPS、基站和WLAN等网络源确定用户的的大概或者精确位置，当这些位置服务可用且处于启用状态时，此权限可让该应用确定用户的位置。使用该类服务时，用户的设备也会消耗更多的电量。

使用该权限的接口：api.startLocation()、api.getLocation()

是否敏感：是

配置示例：```<permission name="location" />```

##访问文件系统<div id="29"></div>

权限名称：fileSystem

权限描述：允许应用读取或写入内部存储及外部SD卡。

使用该权限的接口：api.readFile()、api.writeFile()、api.startRecord()、api.getPicture()

是否敏感：否

配置示例：```<permission name="fileSystem" />```

##完全的访问网络权限<div id="30"></div>

权限名称：internet

权限描述：允许应用创建网络套接字和使用自定义网络协议。查看网络连接的相关信息，查看WLAN状态、更改WLAN状态，更改网络设置，访问设备WIFI信息等。

使用该权限的接口：api.ajax()、api.download()、api.startLocation()、api.getLocation()

是否敏感：否

配置示例：```<permission name="internet" />```

##开机启动<div id="31"></div>

权限名称：bootCompleted

权限描述：允许该应用在系统启动完成后立即自动启动。这可能会导致延长手机的启动时间，并允许应用始终运行，从而导致手机总体运行速度减慢。

使用该权限的接口：基于推送的相关服务

是否敏感：否

配置示例：```<permission name="bootCompleted" />```

##控制振动/闪光灯/屏幕休眠等硬件设备<div id="32"></div>

权限名称：hardware

权限描述：允许应用控制闪光灯、振动器、防止手机休眠等。

使用该权限的接口：api.getPicture()、基于推送的相关服务

是否敏感：否

配置示例：```<permission name="hardware" />```

##访问设备通讯录<div id="33"></div>

权限名称：contact

权限描述：允许该应用访问和修改用户手机上存储的联系人的相关数据。

使用该权限的接口：api.openContacts()

是否敏感：是

配置示例：```<permission name="contact" />```

#**Font**<div id="34"></div>

Font用于配置字体文件，配置以后在前端页面里面就可以使用该字体。

字体文件需放在widget目录里面，可以同时配置多种字体。

目前只支持iOS。

配置示例：

```
<font name="widget/res/xingkai.ttf" />
<font name="widget/res/lishu.ttf" />
```


##Reference<div id="35"></div>

完整的config文件参考：

```js
<widget id="A12345678901"  version="0.0.1">
    <name>API Example</name>
    <description>
        API Example App.
    </description>
    <author email="developer@apicloud.com" href="http://www.apicloud.com">
        APICloud.SIR
    </author>
    <content src="index.html" />
    <access origin="*" />
    <preference name="pageBounce" value="false" />
    <preference name="appBackground" value="#000" />
    <preference name="windowBackground" value="rgba(0,0,0,0.0)" />
    <preference name="frameBackgroundColor" value="rgba(0,0,0,0.0)" />
    <preference name="hScrollBarEnabled" value="true" />
    <preference name="vScrollBarEnabled" value="true" />
    <preference name="autoLaunch" value="true" />
    <preference name="smartUpdate" value="false" />
    <preference name="fullScreen" value="false" />
    <preference name="iOS7StatusBarAppearance" value="true" />
    <preference name="autoUpdate" value="false" />
    <permission name="readPhoneState" />
    <permission name="call" />
	<permission name="sms" />
	<permission name="camera" />
	<permission name="record" />
	<permission name="location" />
	<permission name="fileSystem" />
	<permission name="internet" />
	<permission name="bootCompleted" />
	<permission name="hardware" />
	<permission name="contact" />
	<feature name="weiXin">
		<param name="urlScheme" value="wx7779c7c063a9d4d9" />
		<param name="apiKey" value="wx7779c7c063a9d4d9" />
	</feature>
    <feature name="sinaWeiBo">
        <param name="urlScheme" value="wb1062272715" />
        <param name="apiKey" value="1062272715" />
	</feature>
	<feature name="aliPay">
    	 <param name="urlScheme" value=" AliPayA00000000001" />
	</feature>
    <feature name="baiduLocation">
        <param name="apiKey" value="fef72715gshjelke" />
	</feature>
    <feature name="baiduMap">
        <param name="android_api_key" value="fef72715gshjelke" />
        <param name="ios_api_key" value="fef72715gshjelke" />
	</feature>
    <feature name="qq">
        <param name="urlScheme" value="tencent9c7c063a9d4d9" />
        <param name="apiKey" value="9c7c063a9d4d9" />
	</feature>
</widget>
```
