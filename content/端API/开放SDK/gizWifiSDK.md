/*
Title: gizWifiSDK
Description: gizWifiSDK
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：机智云</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>

<div id="method-content">

**gizWifiSDK类**

<div class="outline">
[startWithAppID](#a1)
[getVersion](#a2)
[setLogLevel](#a3)
</div>
	

**设备配置入网**

<div class="outline">
[getPhoneSSID](#a4)
[setDeviceWifi](#a5)
[getSSIDList](#a6)
</div>


**设备搜索和绑定**

<div class="outline">
[updateDeviceFromServer](#a7)
[getBoundDevices](#a8)
[bindDevice](#a9)
[unbindDevice](#a10)
</div>

**用户登录注册相关**

<div class="outline">
[userLoginAnonymous](#a11)
[userLogin](#a12)
[userLoginWithThirdAccountType](#a13)
[requestSendVerifyCode](#a14)
[registerUser](#a15)
[registerUserByPhoneAndCode](#a16)
[registerUserByEmail](#a17)
[transAnonymousUserToNormalUser](#a18)
[transAnonymousUserToPhoneUser](#a19)
[changeUserPasswordByCode](#a20)
[changeUserPasswordByEmail](#a21)
[changeUserPassword](#a22)
[changeUserEmail](#a23)
[changeUserPhone](#a24)
</div>


**中控设备分组相关**

<div class="outline">
[getGroups](#a25)
[addGroup](#a26)
[removeGroup](#a27)
[editGroup](#a28)
</div>


**gizWifiDevice类**

**设备控制相关**

<div class="outline">
[login](#a29)
[write](#a30)
[registerNotifications](#a31)
[disconnect](#a32)
</div>


**设备基本信息相关**

<div class="outline">
[getHardwareInfo](#a33)
[getIsBind](#a34)
[getDeviceInfo](#a35)
</div>


**gizWifiCentralControlDevice类**

<div class="outline">
[registerNotifications](#a36)
[getSubDevices](#a37)
[addSubDevice](#a38)
[deleteSubDevice](#a39)
</div>

**gizWifiSubDevice类**

<div class="outline">
[write](#a40)
[registerNotifications](#a41)
[getDeviceInfo](#a42)
</div>

**gizWifiGroup类**

<div class="outline">
[getDevices](#a43)
[addDevice](#a44)
[removeDevice](#a45)
[getGroupInfo](#a46)
</div>

# 概述

机智云gizWifiSDK主要帮助开发者通过sdk接口调用的方式维护用户系统，用户与设备的绑定关系，设备的配置上线以及设备状态的获取和控制指令的发送。

# gizWifiSDK类接口

机智云 Wi-Fi SDK 的基础类。该类提供了SDK初始化、基本设置、用户管理、设备管理的基本接口。


#**startWithAppID**<div id="a1"></div>
 
初始化 SDK

startWithAppID({params}, callback(ret, err))

###params
appID:

* 类型： 字符串
* 默认值：无
* 描述：开发者在[机智云网站](http://site.gizwits.com)申请的应用标识。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0,					// 执行成功，数字类型
		msg: "GizWifiError_NONE"		//成功消息的描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}


###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.startWithAppID({"appID": "7ac10dec7dba436785ac23949536a6eb"}, function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getVersion**<div id="a2"></div>

获取SDK版本号

getVersion(callback(ret, err))

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		version:	// SDK版本号，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.getVersion(function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setLogLevel**<div id="a3"></div>

设置 SDK 日志。
setLogLevel({params})

###params
logLevel:

* 类型： 数字类型
* 默认值：3，详细日志输出
* 描述：SDK日志级别

writeSDCard:

* 类型： 布尔类型
* 默认值：false
* 描述：是否写SD卡。此参数只在Andorid平台生效（true = 写SD卡）

###示例代码
	var gizWifiSDK = api.require(‘gizWifiSDK');
	gizWifiSDK.setLogLevel({"logLevel": 3, "writeSDCard": true});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getPhoneSSID**<div id="a4"></div>

获取手机当前Wifi的SSID

getPhoneSSID(callback(ret, err))

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		SSID:	// 手机当前wifi的SSID，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}


###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.getPhoneSSID(function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setDeviceWifi**<div id="a5"></div>
 
配置设备路由。设备要能连接到WiFi网络，需要先把设备配置到WiFi路由器上。配置时，需要给设备发送要配置的路由SSID和密码。

设备配置支持两种方式：SoftAP方式、AirLink方式。在设备上按不同的按键，可以使设备进入对应的配置模式。详细的操作方式，请访问[机智云网站](http://site.gizwits.com/zh-cn/document/gokit/i_01_stared/)。

提醒：进行 SoftAP 配置时，手机当前必须连上 SoftAP 热点。

setDeviceWifi({params}, callback(ret, err))

###params

ssid:

* 类型： 字符串
* 默认值：无
* 描述：要配置的Wifi SSID

key:

* 类型： 字符串
* 默认值：无
* 描述：要配置的 Wifi 密码

mode:

* 类型： 数字类型
* 默认值：无
* 描述：设备配置方式（见 mode 枚举定义）

softAPSSIDPrefix:

* 类型： 字符串
* 默认值：无
* 描述：SoftAPMode 模式下SoftAP 的 SSID 全名。机智云的GoKit，默认前缀为”XPG-GAgent”或”XPG_GAgent”


timeout:

* 类型： 数字类型
* 默认值：30
* 描述：超时时间。超时时间建议设置为60秒

gagentTypes:

* 类型： 数值数组类型
* 默认值：0
* 描述：模组类型（见 GAgentType 枚举定义）


###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{			// 配置成功的设备，以下字段是设备信息：
       			"mac":		// 设备mac
       			"did":		// 设备did
       		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}


###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.setDeviceWifi({
	        "ssid": 'XXXXXXXXXX',
	        "key": 'XXXXXXXXXXX',
	        "mode":1,
	        "softAPSSIDPrefix": 'XXXXXXXXXXX',
	        "timeout": 60,
            "gagentTypes":[4]
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getSSIDList**<div id="a6"></div>

获取设备热点列表。设备 wifi 模组处于 SoftAP 热点模式时，可以获取设备搜索到的 WiFi 热点列表。此接口需要手机当前 Wifi 连上设备模组的 SoftAP 热点后才能工作。

getSSIDList(callback(ret, err))


###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		wifiSSIDs:[{   	// WiFi热点列表，以下字段是热点信息：
       			"ssid":		// WiFi的ssid
       			"rssi":		// WiFi的信号强弱
       		}]
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}


###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.getSSIDList(function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = "  JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**updateDeviceFromServer**<div id="a7"></div>

更新设备配置信息。SDK需要设备配置信息才能识别设备类型、设备操作指令以及设备的上报状态。SDK在获取到绑定设备列表时自动下载一次设备的配置文件。但如果设备的数据点有变化，APP 需要调用此接口先更新设备配置信息。

请在执行设备操作之前，确认设备的数据点定义是否有变化。如果数据点无变化，不需要调用此接口。


updateDeviceFromServer({params}, callback(ret, err))

###params

productKey:

* 类型： 字符串
* 默认值：无
* 描述：产品标识码。开发者在机智云网站创建硬件接入产品时会得到一个产品标识码，即 Product Key，可唯一标识设备类型。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		product:	// 配置信息更新成功的productKey，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}


###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.updateDeviceFromServer({"productKey": '6f3074fe43894547a4f1314bd7e3ae0b'}, function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getBoundDevices**<div id="a8"></div>
 
获取设备列表。用户登录后，可以获取指定产品类型的设备列表，包括从云端返回的和小循环搜索得到的设备。用户不登录时调用此接口，将只能获取小循环搜索得到的设备。
因为此接口会同时触发小循环设备发现和大循环获取绑定设备列表请求，设备搜索结果将根据当前搜索情况多次返回。

getBoundDevices({params}, callback(ret, err))

###params
uid:

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获取到的uid。uid 和 token 都不传时，将只会得到小循环设备

token:

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获取到的token。uid 和 token 都不传时，将只会得到小循环设备

specialProductKeys:

* 类型： 字符串数组
* 默认值：无
* 描述：指定过滤的产品类型识别码，可同时指定多个要过滤的 Product Key

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		devices:[{			// 设备数组（以下字段是设备对象信息），数组类型
			mac:			// 设备mac地址，字符串类型
			did:  			// 设备唯一标识，字符串类型
			ip:				// 设备IP地址，字符串类型
			passcode:		// 设备验证码（用于设备绑定和登录时验证身份），字符串类型
			productKey:		// 设备的产品识别码，字符串类型
			productName:	// 设备的产品名称，字符串类型
			type:			// 设备类型（0＝普通设备，1＝中控设备），数字类型
			isDisconnected:	// 设备是否已登录，布尔类型
			isOnline:  		// 设备是否在线，布尔类型
			isLAN:			// 设备是否是局域网内设备，布尔类型
			isDisabled:		// 设备是否已在云端注销，布尔类型
			remark:			// 设备的备注信息，字符串类型
		}]
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require(‘gizWifiSDK');
    	gizWifiSDK.getBoundDevices({
    		"uid": ‘xxx’,
    		"token": ‘xxx’,
    		"specialProductKeys": ['6f3074fe43894547a4f1314bd7e3ae0b']
     	}, function (ret1, err1) {
    		alert("ret1 = " + JSON.stringify(ret1) + "err1 = " + JSON.stringify(err1))
    	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**bindDevice**<div id="a9"></div>

绑定设备到云端。用户登录后，可以将局域网内搜索到的设备或虚拟设备绑定到云端自己的账户上。

bindDevice({params}, callback(ret, err))


###params

uid:

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获取到的uid。

token:

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获取到的token。

did:

* 类型： 字符串
* 默认值：无
* 描述：设备唯一标识 id。此 id 为设备向云端注册时，由云端分配。SDK 在设备搜索时可以给 APP 提供设备 did。

passcode:

* 类型： 字符串
* 默认值：无
* 描述：设备验证码。如果要绑定虚拟设备，可以在机智云网站的虚拟设备二维码中扫码得到passcode。如果要绑定实体设备，如果用户手中有passcode，可以填充，如果没有，可以不填充，SDK会自动向实体设备获取passcode。

remark:

* 类型： 字符串
* 默认值：无
* 描述：设备备注信息。绑定设备时，可以给设备备注个好记的名字。此参数不要求必填。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		did:  // 设备唯一标识，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require(‘gizWifiSDK');
    	gizWifiSDK.bindDevice({
		"uid": ‘xxxxxxxx’,
		"token": ‘xxxxxxxx’,
		“did”: ‘xxxxxx’	
    	}, function (ret1, err1) {
    		alert("ret1 = " + JSON.stringify(ret1) + "err1 = " + JSON.stringify(err1))
    	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**unbindDevice**<div id="a10"></div>

把设备从云端解绑。用户登录后，可以将已绑定的设备与云端自己的账户解绑。

unbindDevice({params}, callback(ret, err))

###params
uid:

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获取到的uid。

token:

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获取到的token。

did:

* 类型： 字符串
* 默认值：无
* 描述：设备唯一标识。

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		did:  // 设备唯一标识，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.unbindDevice({
		"uid": ‘xxxxxxxx’,
		"token": ‘xxxxxxxx’,
		“did”: ‘xxxxxx’	
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**userLoginAnonymous**<div id="a11"></div>

匿名用户登录，SDK会默认生成一个账号登录到云端，并返回对应的 uid 和 token。

userLoginAnonymous(callback(ret, err))


###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		uid:  	// 用户uid，字符串类型
		token:	// 登录会话token，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}


###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.userLoginAnonymous(function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});


###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**userLogin**<div id="a12"></div>
 
普通用户登录。用户名可以是手机号、邮箱和普通用户名。

userLogin({params}, callback(ret, err))

###params
userName:

* 类型： 字符串
* 默认值：无
* 描述：要登录的用户名。

password:

* 类型： 字符串
* 默认值：无
* 描述：要登录的密码。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		uid:  	// 用户uid，字符串类型
		token:	// 登录会话token，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.userLogin({
		"userName": 'XXXXXX',
	    	"password": 'XXXXXX'
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	})

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**userLoginWithThirdAccountType**<div id="a13"></div>

第三方账号登录。第三方账号支持百度、新浪、QQ，需要通过第三方的 shareSDK 工具或各自对应的SDK，获取到 uid 和 token 之后才可以使用此接口。

userLoginWithThirdAccountType({params}, callback(ret, err))

###params

uid: 登录第三方账号之后得到的uid

* 类型： 字符串
* 默认值：无
* 描述：要登录的用户id

token: 登录第三方账号之后得到的token

* 类型： 字符串
* 默认值：无
* 描述：要登录的密码

thirdAccountType:

* 类型： 数字类型
* 默认值：无
* 描述：第三方账号类型（0 = 百度账号, 1 = 新浪账号, 2 = QQ账号，见 thirdAccountType 枚举定义）

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		uid:  	// 登录机智云后得到的 uid，字符串类型
		token:	// 登录机智云后得到的 token，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.userLoginWithThirdAccountType({
	        "thirdAccountType": 0,
	        "uid": ‘xxxxxx’,
	        "token": ‘xxxxxx’
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});


###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**requestSendVerifyCode**<div id="a14"></div>

此接口已废弃，调用后将返回错误码为－47，含义是不支持的API。
请使用新的短信验证接口获取手机验证码：getCaptchaCode、requestSendPhoneSMSCode、verifyPhoneSMSCode。当注册新用户、匿名用户转换、找回密码、修改用户信息时，需要先调用这些接口。

requestSendVerifyCode({params}, callback(ret, err))

###params

phone: 

* 类型： 字符串
* 默认值：无
* 描述：要获取验证码的手机号码。

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 验证码获取成功，数字类型
		msg: "GizWifiError_SUCCESS"		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.requestSendVerifyCode({
	        "phone": ‘xxxxxx’
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**getCaptchaCode**<div id="a14"></div>

通过 App Secret 获取图片验证码。

getCaptchaCode({params}, callback(ret, err))

###params

appSecret: 

* 类型： 字符串
* 默认值：无
* 描述：应用的 secret 信息，是与 AppID 对应的应用签名字符串，从 site.gizwits.com 中可以看到

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		token: ‘xxxxxx’, 			// 图片验证码 token，字符串类型
		captchaId: ‘xxxxxx’		// 图片验证码 id，字符串类型
		captchaURL: ‘xxxxxx’		// 图片验证码 url，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.getCaptchaCode({
	        "appSecret": ‘xxxxxx’
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**requestSendPhoneSMSCode**<div id="a14"></div>

用图片验证码，请求发送手机短信验证码

requestSendPhoneSMSCode({params}, callback(ret, err))

###params

token: 

* 类型： 字符串
* 默认值：无
* 描述：验证码 token，通过 getCaptchaCode 获取

captchaId: 

* 类型： 字符串
* 默认值：无
* 描述：验证码 id，通过 getCaptchaCode 获取

captchaCode: 

* 类型： 字符串
* 默认值：无
* 描述：验证码，来自图片的验证内容

phone: 

* 类型： 字符串
* 默认值：无
* 描述：手机号

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 验证码获取成功，数字类型
		msg: "GizWifiError_SUCCESS"		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.requestSendPhoneSMSCode({
	        "token": ‘xxxxxx’
	        "captchaId": ‘xxxxxx’
	        "captchaCode": ‘xxxxxx’
	        "phone": ‘xxxxxx’
	}, function(ret, err) {
	    alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**verifyPhoneSMSCode**<div id="a14"></div>

验证收到的手机短信验证码

verifyPhoneSMSCode({params}, callback(ret, err))

###params

token: 

* 类型： 字符串
* 默认值：无
* 描述：验证码 token，通过 getCaptchaCode 获取

phoneCode: 

* 类型： 字符串
* 默认值：无
* 描述：手机短信中的验证码内容

phone: 

* 类型： 字符串
* 默认值：无
* 描述：手机号

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 验证码获取成功，数字类型
		msg: ‘GizWifiError_SUCCESS’		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.verifyPhoneSMSCode({
	        "token": 'xxxxxx'
	        "phoneCode": 'xxxxxx'
	        "phone": 'xxxxxx'
	}, function(ret, err) {
	    alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**registerUser**<div id="a15"></div>

注册普通用户。

registerUser({params}, callback(ret, err))

###params
userName: 

* 类型： 字符串
* 默认值：无
* 描述：用户名。

password: 

* 类型： 字符串
* 默认值：无
* 描述：密码。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		uid:  	// 注册成功后返回的uid，字符串类型
		token:	// 注册成功后返回的token，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.registerUser({
		"userName": 'xxxxxx',
		"password" :'xxxxxx'
	}, function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**registerUserByPhoneAndCode**<div id="a16"></div>

注册手机号用户

registerUserByPhoneAndCode({params}, callback(ret, err))

###params
phone: 

* 类型： 字符串
* 默认值：无
* 描述：手机号。

password: 

* 类型： 字符串
* 默认值：无
* 描述：密码。

code: 

* 类型： 字符串
* 默认值：无
* 描述：手机验证码。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		uid:  	// 注册成功后返回的uid，字符串类型
		token:	// 注册成功后返回的token，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.registerUserByPhoneAndCode({
	    "phone": 'xxxxxx',
	    "password": 'xxxxxx',
	    "code":'xxxxxx'
	}, function(ret, err) {
	    alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**registerUserByEmail**<div id="a17"></div>
 
注册邮箱用户

registerUserByEmail({params}, callback(ret, err))

###params

email: 

* 类型： 字符串
* 默认值：无
* 描述：手机号。

password: 

* 类型： 字符串
* 默认值：无
* 描述：密码。

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		uid:  	// 注册成功后返回的uid，字符串类型
		token:	// 注册成功后返回的token，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.registerUserByEmail({
		"email": 'xxxxxx',
		"password": 'xxxxxx'
	}, function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**transAnonymousUserToNormalUser**<div id="a18"></div>

匿名用户转普通用户。手机匿名登录后，可以转换为普通用户或邮箱用户。用户信息填充用户名和密码即可。转换后，匿名用户已经绑定的设备，会迁移到转换后的用户账号下。

transAnonymousUserToNormalUser({params}, callback(ret, err))

###params

token: 

* 类型： 字符串
* 默认值：无
* 描述：匿名登录后得到的token。

userName: 

* 类型： 字符串
* 默认值：无
* 描述：用户名。

password: 

* 类型： 字符串
* 默认值：无
* 描述：密码。

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 转换成功，数字类型
		msg: “GizWifiError_SUCCESS”		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.transAnonymousUserToNormalUser({
		"token": 'xxxxxx',
		"userName": 'xxxxxx',
		"password": 'xxxxxx'
	}, function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**transAnonymousUserToPhoneUser**<div id="a18"></div>

匿名用户转手机用户。手机匿名登录后，可以转换为手机用户，但需要先获取到手机验证码才可以转换。转换后，匿名用户已经绑定的设备，会迁移到转换后的用户账号下。

transAnonymousUserToPhoneUser({params}, callback(ret, err))

###params
token: 

* 类型： 字符串
* 默认值：无
* 描述：匿名登录后得到的token。

phone: 

* 类型： 字符串
* 默认值：无
* 描述：转换后的手机号。

password: 

* 类型： 字符串
* 默认值：无
* 描述：转换后的密码。

code: 

* 类型： 字符串
* 默认值：无
* 描述：手机验证码。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 转换成功，数字类型
		msg: "GizWifiError_SUCCESS"		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.transAnonymousUserToPhoneUser({
		"token": 'xxxxxx',
		"phone": 'xxxxxx',
		"password": 'xxxxxx',
		"code": 'xxxxxx'
	}, function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**changeUserPasswordByCode**<div id="a20"></div>

通过手机号重置密码。忘记密码时，可以通过手机号重设密码。但需要首先获取到手机验证码才可以重设。

changeUserPasswordByCode({params}, callback(ret, err))

###params
phone: 

* 类型： 字符串
* 默认值：无
* 描述：请求重置密码的手机号。

code: 

* 类型： 字符串
* 默认值：无
* 描述：手机验证码。

newPassword: 

* 类型： 字符串
* 默认值：无
* 描述：重置后的密码。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 重置成功，数字类型
		msg: "GizWifiError_SUCCESS"		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.changeUserPasswordByCode({
		"phone": ‘xxxxxx’,
		"code": ‘xxxxxx’,
		"newPassword": ‘xxxxxx’
	},function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**changeUserPasswordByEmail**<div id="a21"></div>

通过邮箱重置密码。忘记密码时，可以通过邮箱重置密码，机智云会向该邮箱发送一个重置密码的链接，用户登录邮箱后可以点击链接重置密码。

changeUserPasswordByEmail({params}, callback(ret, err))


###params

email: 

* 类型： 字符串
* 默认值：无
* 描述：请求重置密码的邮箱地址。

###callback(ret, er
r)
ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 请求发送成功，数字类型
		msg: "GizWifiError_SUCCESS"		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.changeUserPasswordByEmail({
		"email": 'xxxxxx'
	}, function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**changeUserPassword**<div id="a22"></div>

修改密码。用户登录后，可以修改密码。

changeUserPassword({params}, callback(ret, err))

###params

token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的token。

oldPassword: 

* 类型： 字符串
* 默认值：无
* 描述：旧密码。

newPassword: 

* 类型： 字符串
* 默认值：无
* 描述：新密码。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 修改成功，数字类型
		msg: "GizWifiError_SUCCESS"		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK')
	gizWifiSDK.changeUserPassword({
		"token": ‘xxxxxx’,
		"oldPassword": ‘xxxxxx’,
		"newPassword": ‘xxxxxx’
	},function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本


#**changeUserEmail**<div id="a23"></div>

修改用户邮箱。用户登录后，修改或补充邮箱地址。

changeUserEmail({params}, callback(ret, err))

###params
token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的token。

email: 

* 类型： 字符串
* 默认值：无
* 描述：邮箱。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 修改成功，数字类型
		msg: "GizWifiError_SUCCESS"		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.changeUserEmail({
		"token": ‘xxxxxx’,
		"email": ‘xxxxxx’
	},function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**changeUserPhone**<div id="a24"></div>
 
修改用户手机号。用户登录后，修改或补充手机号。注意，需要先获取手机验证码才能修改手机号。

changeUserPhone({params}, callback(ret, err))

###params

token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的token。

phone: 

* 类型： 字符串
* 默认值：无
* 描述：手机号。

code: 

* 类型： 字符串
* 默认值：无
* 描述：手机验证码。

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 修改成功，数字类型
		msg: "GizWifiError_SUCCESS"		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.changeUserPhone({
		"token": 'xxxxxx',
		"phone":'xxxxxx',
		"code": 'xxxxxx'
	},function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**changeUserAdditionalInfo**<div id="a24"></div>
 
补充用户个人信息。用户登录后，可以补充用户个人信息。

changeUserAdditionalInfo({params}, callback(ret, err))

###params

token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的token。

additionalInfo: 

* 类型： JSON对象
* 默认值：无
* 描述：用户附加信息。
* 内部字段

		{
			"name":		// 用户姓名，字符串类型
			"gender":	// 用户性别，见 UserGenderType 枚举类型
			"birthday":	// 生日，字符串类型
			"address":	// 家庭住址，字符串类型
			"remark":	// 备注，字符串类型
		}

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		errorCode: 0, 					// 修改成功，数字类型
		msg: "GizWifiError_SUCCESS"		// 消息描述，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.changeUserAdditionalInfo({
		"token": '',
	    	"additionalInfo": {
			"name”: ’xxx’,
			"gender”: 0,
			"birthday”: ’xxx’,
			"address”: ’xxx’,
			"remark": 'xxx’
	    	}
	},function(ret, err) {
	    	Ialert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**getUserInfo**<div id="a23"></div>

获取用户信息。用户登录后，可以获取用户的详细信息。

getUserInfo({params}, callback(ret, err))

###params
token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的 token

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		"uid": "xxx",					// 用户登录的uid，字符串类型
    		"username": "xxx",			// 用户名，字符串类型
    		"email": "xxx",				// email信息，字符串类型
    		"phone": "xxx",				// 电话号码，字符串类型
    		"isAnonymous": true/false,		// 是否为匿名用户，布尔类型
    		"name": "xxx",				// 昵称，字符串类型
    		"gender": "xxx",				// 性别，UserGenderType枚举类型
    		"birthday": "xxx",				// 生日，字符串类型
    		"address": "xxx",				// 住址，字符串类型
    		"remark": "xxx"				// 备注，字符串类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
	gizWifiSDK.getUserInfo({
		"token": ‘xxx’
	},function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});
###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getGroups**<div id="a25"></div>

获取用户账号下的设备分组列表。需要先完成用户登录，才能获取设备分组列表。设备分组是指把中控网关管理的子设备分成多个组，便于批量执行子设备操作。一个设备分组只能添加一种类型的设备。常见的应用场景，比如睡前把房间里所有的开关灯关掉，把床头的两个落地灯调暗，这时就可以把子设备分成两个组，一个是开关灯组，一个是落地灯组。

getGroups({params}, callback(ret, err))

###params
uid: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的uid。

token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的uid。

specialProductKeys: 

* 类型： 字符串
* 默认值：无
* 描述：设备分组的类型，即设备类型。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		groups:[{  	// 组对象（以下字段是组对象信息），数组类型
			"gid":	// 组ID，字符串类型
		}]
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require(‘gizWifiSDK');
	gizWifiSDK.getGroups({
        	"uid": ‘xxxxxx’,
        	"token": ‘xxxxxx’,
        	"specialProductKeys": []
    },function(ret, err) {
        	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
    });

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**addGroup**<div id="a26"></div>

添加设备分组。添加后返回当前的设备分组列表

addGroup({params}, callback(ret, err))


###params

uid: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的uid。

token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的uid。

productKey: 

* 类型： 字符串
* 默认值：无
* 描述：要添加的组类型标识，即要添加的设备的productKey。

groupName: 

* 类型： 字符串
* 默认值：无
* 描述：要添加的组名称。

specialDevices: 

* 类型： JSON对象
* 默认值：无
* 描述：要添加的设备对象数组。
* 内部字段

		{
			"mac":		// 子设备所属中控网关的mac地址，字符串类型
			"did": 		// 子设备所属中控网关的did，字符串类型
			"subDid":	// 子设备的did，字符串类型
		}


###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		groups:[{  	// 组对象（以下字段是组对象信息），数组类型
			"gid":	// 组ID，字符串类型
		}]
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require(‘gizWifiSDK');
	gizWifiSDK.addGroup({
            	"uid": ‘xxxxxx’,
            	"token": ‘xxxxxx’,
            	"productKey": ‘xxxxxx’,
            	"groupName": ‘xxxxxx’,
            	"specialDevices": []
        },function(ret, err) {
            	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err));
        });

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**removeGroup**<div id="a27"></div>

删除设备分组。删除后返回当前的设备分组列表

removeGroup({params}, callback(ret, err))

###params
uid: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的uid。

token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的uid。

gid: 

* 类型： 字符串
* 默认值：无
* 描述：要删除的设备分组的组ID。

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		groups:[{  	// 组对象（以下字段是组对象信息），数组类型
			“gid”:	// 组ID，字符串类型
		}]
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require(‘gizWifiSDK');
	gizWifiSDK.removeGroup({
		"uid": ‘xxxxxx’,
            	"token": ‘xxxxxx’,
	       "gid": ’xxxxxx’
	}, function (ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本


#**editGroup**<div id="a28"></div>
 
编辑设备分组。编辑分组后返回当前的设备分组列表

editGroup({params}, callback(ret, err))

###params
uid: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的uid。

token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的uid。

gid: 

* 类型： 字符串
* 默认值：无
* 描述：要编辑的设备分组的组ID。

groupName: 

* 类型： 字符串
* 默认值：无
* 描述：编辑后的组名称。

specialDevices: 

* 类型： JSON对象
* 默认值：无
* 描述：编辑后的设备对象数组。
* 内部字段

		{
			"mac":		// 子设备所属中控网关的mac地址，字符串类型
			"did": 		// 子设备所属中控网关的did，字符串类型
			"subDid":	// 子设备的did，字符串类型
		}

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		groups:[{  	// 组对象（以下字段是组对象信息），数组类型
			“gid”:	// 组ID，字符串类型
		}]
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
	}

###示例代码
	var gizWifiSDK = api.require('gizWifiSDK');
    	gizWifiSDK.editGroup({
		"uid": ’xxx’,
        	"token": ’xxx’,
        	"gid": ’xxx’,
        	"groupName": ’xxx’,
        	"specialDevices": []
    	}, function (ret, err) {
        	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
    	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本


# gizWifiDevice类接口
机智云 Wi-Fi 的设备类。该类提供了设备登录，控制、接收设备信息功能。

#**login**<div id="a29"></div>

设备登录。登录分为大循环登录和小循环登录（即远程和局域网环境）。如果设备既能大循环登录，也能小循环登录，SDK会优先进行小循环登录。当设备只能通过大循环访问时，才进行大循环登录。设备登录成功后，可以进行设备操作。

login({params}, callback(ret, err))

###params
uid: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的uid。

token: 

* 类型： 字符串
* 默认值：无
* 描述：用户登录后获得的token。

device: 

* 类型： JSON对象
* 默认值：无
* 描述：要登录的设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
		}

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 登录成功的设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 设备mac地址，字符串类型
			"did": 	// 设备did，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 请求登录的设备对象（以下字段是设备对象信息），对象类型
			“mac”:	// 设备mac地址，字符串类型
			“did”: 	// 设备did，字符串类型
		}
	}

###示例代码
	var gizWifiDevice = api.require('gizWifiDevice');
	gizWifiDevice.login({
		"uid": ’xxx’,
		"token": ’xxx’,
		"device": {
	    		"mac": ’xxx’,
	    		"did": ’xxx’
	  	}
	},function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**write**<div id="a30"></div>

设备控制。设备控制也分为大循环和小循环（即远程和局域网环境），SDK会优先进行小循环控制。当设备只能通过大循环访问时，才进行大循环控制。APP的设备控制指令到达设备端后，设备状态变化时会上报当前状态。APP通过回调函数可以得到状态数据，包括设备的运行状态、报警、故障、透传数据等。

硬件产品开发者根据产品功能来定义设备的操作命令集。在APP端，设备的操作命令以数据点形式格式化后发送到设备端。数据点可以定义布尔类型、字符串类型、数字类型、扩展类型的数据。如何定义数据点，请访问[机智云网站](http://site.gizwits.com/zh-cn/document/m2m/i_021_editdp/)。

如果开发者有需要透传的数据指令，可以通过定义扩展类型的数据点实现。如果要透传的是二进制数据，需要先用base64编码转换为字符串再写入write接口的data参数。同样，设备向APP透传的二进制数据，APP接收后，要先经过base64解码为二进制数据才能正确使用。请注意，一定要用base64编解码，否则二进制数据无法正确透传。

write({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：要发送操作指令的设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
		}

data: 

* 类型： JSON对象
* 默认值：无
* 描述：要发送的操作指令。
* 内部字段

		{
			"cmd":	// 命令action属性，数字类型
					// 1 = 设备控制（APP->设备）
					// 2 = 状态查询（APP->设备）
					// 3 = 查询应答（设备->APP）
					// 4 = 状态上报（设备->APP）
					
			"entity0": {				// 设备数据接入点名称（默认为entity0），对象类型
				……
				"attrName": "attrValue",	// 操作命令：操作名称、操作值
										// 操作名称是字符串类型，
										// 操作值的类型是在数据点中定义的
				……
			}		
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 操作命令执行成功的设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 设备mac地址，字符串类型
			"did": 	// 设备did，字符串类型
		}
		status:{   		// 设备上报的状态（以下字段是设备状态信息），对象类型
			"data": {		// 状态，字符串类型
				"entity0":{ 			// 设备接入点名称，对象类型
					"attrName": "attrValue",// 数据点名称: 操作值
					……
				}
			}
			"alerts":[					// 报警，数组类型
				"attrName": "attrValue"	// 数据点名称: 报警内容
			] 
			"faults":[				 	// 故障，数组类型
				"attrName":"attrValue"	// 数据点名称: 故障内容
			] 
			"binary": 	// 二进制透传数据，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 请求控制的设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 设备mac地址，字符串类型
			"did": 	// 设备did，字符串类型
		}
	}

###示例代码
	var gizWifiDevice = api.require('gizWifiDevice');
	gizWifiDevice.write({
		"device": {
	             "mac": ’xxx’,
	             "did": ’xxx’
		},
		"data": {
			"cmd": 1,
			"entity0": {
				"LED_G": 127,
	               	"LED_B":254,
	               	"LED_R":127,
	               	"LED_OnOff":true,
	               	"Motor_Speed":2,
	               	"Infrared":true
	         	}
	     	}
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**registerNotifications**<div id="a31"></div>

注册设备状态变化通知。只要得到设备的mac地址和did，就可以注册设备通知。注册后，设备后续的登录状态变化、运行状态变化都会实时上报给APP。设备解绑或断开连接后，就不会再上报数据了。

registerNotifications({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：要注册通知的设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 操作命令执行成功的设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 设备mac地址，字符串类型
			"did": 	// 设备did，字符串类型
		}
		isConnected: 	// 设备是否已登录，布尔类型
		isOnline:		// 设备是否在线，布尔类型
		status:{   		// 设备上报的状态（以下字段是设备状态信息），对象类型
			"data": {						// 设备状态，字符串类型
				"entity0":{ 				// 设备接入点名称，对象类型
					"attrName":"attrValue",// 数据点名称: 操作值
					……
				}
			}
			"alerts":[					// 报警，数组类型
				"attrName": "attrValue"	// 数据点名称: 报警内容
			] 
			"faults":[				 	// 故障，数组类型
				"attrName": "attrValue"	// 数据点名称: 故障内容
			] 
			"binary": 	// 二进制透传数据，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 请求注册的设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 设备mac地址，字符串类型
			"did": 	// 设备did，字符串类型
		}
	}

###示例代码
	var gizWifiDevice = api.require('gizWifiDevice');
	gizWifiDevice.registerNotifications({
		"device": {
	     		"mac": ’xxx’,
	     		"did": ’xxx’
	     	}
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});


###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**disconnect**<div id="a32"></div>

断开设备连接。

disconnect({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：要断开连接的设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			“mac”:		// 设备mac地址，字符串类型
			“did”: 		// 设备did，字符串类型
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 操作命令执行成功的设备对象（以下字段是设备对象信息），对象类型
			“mac”:	// 设备mac地址，字符串类型
			“did”: 	// 设备did，字符串类型
		}
		isConnected: 	// 设备是否已登录，布尔类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 请求注册的设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 设备mac地址，字符串类型
			"did": 	// 设备did，字符串类型
		}
	}

###示例代码
	var gizWifiDevice = api.require('gizWifiDevice');
	gizWifiDevice.disconnect({
	   	"device": {
	        	"mac": ’xxx’,
			"did": ’xxx’
	   	}
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getIsBind**<div id="a34"></div>

设备是否已绑定。

getIsBind({params}, callback(ret, err))

###params

device:  

* 类型： JSON对象
* 默认值：无
* 描述：要判断的设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
		}

uid: 

* 类型： 字符串对象
* 默认值：无
* 描述：要判断的是设备与哪个用户uid绑定关系。

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 操作命令执行成功的设备对象（以下字段是设备对象信息），对象类型
			“mac”:	// 设备mac地址，字符串类型
			“did”: 	// 设备did，字符串类型
		}
		isBind: 	// 设备是否已绑定，布尔类型
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 请求注册的设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 设备mac地址，字符串类型
			"did": 	// 设备did，字符串类型
		}
	}

###示例代码
	var gizWifiDevice = api.require('gizWifiDevice');
	gizWifiDevice.getIsBind({
		"device": {
	    		"mac": ’xxx’,
			"did": ’xxx’
	  	},
		"uid": ’xxx’
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getHardwareInfo**<div id="a33"></div>
 
获取设备硬件信息。只有在小循环时，设备登录后才能够获取到设备硬件信息。

getHardwareInfo({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device: {   	// 操作命令执行成功的设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 设备mac地址，字符串类型
			"did": 	// 设备did，字符串类型
		}
		hardwareInfo: {			// 硬件信息对象，对象类型
			"wifiHardVer":		// WiFi硬件版本号，字符串类型
			"wifiSoftVer":			// WiFi软件版本号，字符串类型
			"mcuHardVer":		// 设备硬件版本号，字符串类型
			"mcuSoftVer":		// 设备软件版本号，字符串类型
			"firmwareId":			// 固件fid，字符串类型
			"firmwareVer":		// 固件版本号，字符串类型
			"productKey":		// 产品类型识别码
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 请求注册的设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 设备mac地址，字符串类型
			"did": 	// 设备did，字符串类型
		}
	}

###示例代码
	var gizWifiDevice = api.require('gizWifiDevice');
	gizWifiDevice.getHardwareInfo({
	    	"device": {
	        	"mac": ’xxx’,
			"did": ’xxx’
	    	}
	},function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getDeviceInfo**<div id="a35"></div>
 
获取设备基本信息。

getDeviceInfo({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：设备对象，设备mac和did可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 中控设备mac地址，字符串类型
			"did": 		// 中控设备did，字符串类型
		}

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		device: {   	// 设备对象（以下字段是设备信息），对象类型
			mac:			// 设备mac地址，字符串类型
			did:  			// 设备唯一标识，字符串类型
			ip:				// 设备IP地址，字符串类型
			passcode:		// 设备验证码（用于设备绑定和登录时验证身份），字符串类型
			productKey:		// 设备的产品识别码，字符串类型
			productName:	// 设备的产品名称，字符串类型
			type:			// 设备类型（0＝普通设备，1＝中控设备），数字类型
			isConnected:	// 设备是否已登录，布尔类型
			isOnline:  		// 设备是否在线，布尔类型
			isLAN:			// 设备是否是局域网内设备，布尔类型
			isDisabled:		// 设备是否已在云端注销，布尔类型
			remark:			// 设备的备注信息，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device: {   	// 设备对象（以下字段是设备对象信息），对象类型
			“mac”:		// 设备mac地址，字符串类型
			“did”: 		// 设备did，字符串类型
		}
	}

###示例代码
	var gizWifiDevice = api.require('gizWifiDevice');
	gizWifiDevice.getDeviceInfo({
		"device": {
			"mac": ’xxx’,
			"did": ’xxx’
	        }
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


# gizWifiCentralControlDevice类接口

机智云 Wi-Fi 的中控设备类。该类提供了中控设备获取子设备列表、添加子设备、删除子设备功能。中控设备类继承自GizWifiDevice类，可以使用GizWifiDevice类的所有接口。

在获取到设备列表时，通过GizWifiDevice类的getType()接口，可以知道该设备是否为中控设备。中控设备登录后，就可以进行子设备添加、删除等操作了。

#**registerNotifications**<div id="a36"></div>
 
注册子设备列表变化通知。当中控设备处于子设备加网状态时，会主动上报当前已入网的子设备。APP注册通知后，SDK就会将子设备列表上报给APP。
registerNotifications({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：要注册通知的中控设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 中控设备mac地址，字符串类型
			"did": 		// 中控设备did，字符串类型
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 中控设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 中控设备mac地址，字符串类型
			"did": 	// 中控设备did，字符串类型
		}
		isConnected: 	// 中控设备是否已登录，布尔类型
		isOnline:		// 中控设备是否在线，布尔类型
		subDevices:{	// 中控设备上报的子设备列表（以下字段是子设备信息），对象数组类型
			"mac": 		// 中控设备mac，字符串类型
			"did":		// 中控设备did，字符串类型
			"subDid":		// 子设备did，字符串类型
			"isOnline":	// 子设备是否在线，布尔类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 中控设备对象（以下字段是中控设备对象信息），对象类型
			“mac”:	// 中控设备mac地址，字符串类型
			“did”: 	// 中控设备did，字符串类型
		}
	}

###示例代码
	var gizWifiCentralControlDevice = api.require('gizWifiCentralControlDevice');
	gizWifiCentralControlDevice.registerNotifications({
	        "device": {
	            	"mac": ’xxx’,
	            	"did": ’xxx’
	        }
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getSubDevices**<div id="a37"></div>

获取子设备列表。

getSubDevices({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：中控设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			“mac”:		// 中控设备mac地址，字符串类型
			“did”: 		// 中控设备did，字符串类型
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 中控设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 中控设备mac地址，字符串类型
			"did": 	// 中控设备did，字符串类型
		}
		subDevices:{	// 中控设备上报的子设备列表（以下字段是子设备信息），对象数组类型
			"mac": 		// 中控设备mac，字符串类型
			"did":		// 中控设备did，字符串类型
			"subDid": 				// 子设备did，字符串类型
			"subProductKey":			// 子设备类型标识，字符串类型
			"subProductName":		// 子设备产品名称，字符串类型
			"type”:					// 子设备类型，数字类型
			"isOnline":				// 子设备是否在线，布尔类型
			"productKey":				// 中控设备类型标识，字符串类型
			"productName":			// 中控设备产品名称，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 中控设备对象（以下字段是中控设备对象信息），对象类型
			“mac”:	// 中控设备mac地址，字符串类型
			“did”: 	// 中控设备did，字符串类型
		}
	}

###示例代码
	var gizWifiCentralControlDevice = api.require('gizWifiCentralControlDevice');
	gizWifiCentralControlDevice.getSubDevices({
	        "device": {
	            	"mac": ’xxx’,
			"did": ’xxx’
	        }
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**addSubDevice**<div id="a38"></div>

添加子设备。

addSubDevice({params}, callback(ret, err))


###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：中控设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 中控设备mac地址，字符串类型
			"did": 		// 中控设备did，字符串类型
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 中控设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 中控设备mac地址，字符串类型
			"did": 	// 中控设备did，字符串类型
		}
		subDevices:{	// 中控设备上报的子设备列表（以下字段是子设备信息），对象数组类型
			"mac": 		// 中控设备mac，字符串类型
			"did":		// 中控设备did，字符串类型
			"subDid": 				// 子设备did，字符串类型
			"subProductKey":			// 子设备类型标识，字符串类型
			"subProductName":		// 子设备产品名称，字符串类型
			"type”:					// 子设备类型，数字类型
			"isOnline":				// 子设备是否在线，布尔类型
			"productKey":			// 中控设备类型标识，字符串类型
			"productName":			// 中控设备产品名称，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 中控设备对象（以下字段是中控设备对象信息），对象类型
			“mac”:	// 中控设备mac地址，字符串类型
			“did”: 	// 中控设备did，字符串类型
		}
	}

###示例代码
	var gizWifiCentralControlDevice = api.require('gizWifiCentralControlDevice');
	gizWifiCentralControlDevice.addSubDevice({
	        "device": {
	            	"mac": ’xxx’,
			"did": ’xxx’
	        }
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**deleteSubDevice**<div id="a39"></div>

删除子设备。

deleteSubDevice({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：中控设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":	// 中控设备mac地址，字符串类型
			"did": 	// 中控设备did，字符串类型
		}

device: 

* 类型： JSON对象
* 默认值：无
* 描述：中控设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		subDid:		// 要删除的子设备did

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 中控设备对象（以下字段是设备对象信息），对象类型
			"mac":	// 中控设备mac地址，字符串类型
			"did": 	// 中控设备did，字符串类型
		}
		subDevices:{	// 中控设备上报的子设备列表（以下字段是子设备信息），对象数组类型
			"mac": 		// 中控设备mac，字符串类型
			"did":		// 中控设备did，字符串类型
			"subDid": 				// 子设备did，字符串类型
			"subProductKey":			// 子设备类型标识，字符串类型
			"subProductName":		// 子设备产品名称，字符串类型
			"type”:					// 子设备类型，数字类型
			"isOnline":				// 子设备是否在线，布尔类型
			"productKey":			// 中控设备类型标识，字符串类型
			"productName":			// 中控设备产品名称，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 中控设备对象（以下字段是中控设备对象信息），对象类型
			“mac”:	// 中控设备mac地址，字符串类型
			“did”: 	// 中控设备did，字符串类型
		}
	}

###示例代码
	var gizWifiCentralControlDevice = api.require('gizWifiCentralControlDevice');
	gizWifiCentralControlDevice.deleteSubDevice({
	        "device": {
	            	"mac": ’xxx’,
	            	"did": ’xxx’,
	            	"subDid": ’xxx’
	        }
	 }, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


# gizWifiSubDevice类接口

机智云 Wi-Fi 的中控子设备类。该类提供了子设备控制、子设备状态上报功能。中控子设备类继承自GizWifiDevice类，可以使用GizWifiDevice类的所有接口。

#**write**<div id="a40"></div>
 
子设备控制。同普通设备控制一样，请见2.2说明。

write({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：要发送操作指令的设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
			"subDid": 	// 子设备did，字符串类型
		}

data: 

* 类型： JSON对象
* 默认值：无
* 描述：要发送的操作指令，格式与普通设备相同（见2.2）。
* 内部字段

		{
			"cmd":	// 命令属性（见2.2），数字类型
			"entity0": {				// 设备数据接入点名称（默认为entity0），对象类型
				……
				"attrName": "attrValue",	// 操作命令：操作名称、操作值
										// 操作名称是字符串类型，
										// 操作值的类型是在数据点中定义的
				……
			}		
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 操作命令执行成功的设备对象（以下字段是设备对象信息），对象类型
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
			"subDid": 	// 子设备did，字符串类型
		}
		status:{   		// 设备上报的状态（以下字段是设备状态信息），对象类型
			"data": {		// 状态，字符串类型
				"entity0":{ 			// 设备接入点名称，对象类型
					"attrName": "attrValue",// 数据点名称: 操作值
					……
				}
			}
			"alerts":[					// 报警，数组类型
				"attrName": "attrValue"	// 数据点名称: 报警内容
			] 
			"faults":[				 	// 故障，数组类型
				"attrName": "attrValue"	// 数据点名称: 故障内容
			] 
			"binary": 	// 二进制透传数据，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 请求控制的设备对象（以下字段是设备对象信息），对象类型
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
			"subDid": 	// 子设备did，字符串类型
		}
	}

###示例代码
	var gizWifiSubDevice = api.require('gizWifiSubDevice');
	gizWifiSubDevice.write({
		"device": {
	        	"mac": ’xxx’,
			"did": ’xxx’,
			"subDid": ’xxx’
	    	},
	   	"data": {
			"cmd": 1,
	       		"entity0": {
				"LED_G": 127,
	             		"LED_B":254,
	             		"LED_R":127,
	             		"LED_OnOff":true,
	             		"Motor_Speed":2,
				"Infrared":true
	       		}
	   	}
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**registerNotifications**<div id="a41"></div>

注册子设备状态变化通知。

registerNotifications({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：要注册通知的设备对象，设备对象信息可以在获取设备列表时得到。
* 内部字段

		{
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
			"subDid": 	// 子设备did，字符串类型
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device:{   	// 操作命令执行成功的子设备对象（以下字段是子设备信息），对象类型
			"mac":		// 中控设备mac地址，字符串类型
			"did": 		// 中控设备did，字符串类型
			"subDid": 	// 子设备did，字符串类型
		}
		isOnline:		// 子设备是否在线，布尔类型
		status:{   		// 子设备上报的状态（以下字段是子设备状态信息），对象类型
			"data": {						// 运行状态，字符串类型
				"entity0":{ 				// 接入点名称，对象类型
					"attrName": "attrValue",// 数据点名称: 操作值
					……
				}
			}
			"alerts":[					// 报警，数组类型
				"attrName": "attrValue"	// 数据点名称: 报警内容
			] 
			"faults":[				 	// 故障，数组类型
				"attrName": "attrValue"	// 数据点名称: 故障内容
			] 
			"binary": 	// 二进制透传数据，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 请求注册的设备对象（以下字段是设备对象信息），对象类型
			“mac”:	// 设备mac地址，字符串类型
			“did”: 	// 设备did，字符串类型
			“subDid”: 	// 子设备did，字符串类型
		}
	}

###示例代码
	var gizWifiSubDevice = api.require('gizWifiSubDevice');
	gizWifiSubDevice.registerNotifications({
	        "device": {
			"mac": ’xxx’,
	            	"did": ’xxx’,
			"subDid": ’xxx’
	        }
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getDeviceInfo**<div id="a42"></div>

获取子设备基本信息。

getDeviceInfo({params}, callback(ret, err))

###params

device: 

* 类型： JSON对象
* 默认值：无
* 描述：子设备对象，设备mac和did可以在获取分组设备列表时得到。
* 内部字段

		{
			"mac":		// 中控设备mac地址，字符串类型
			"did": 		// 中控设备did，字符串类型
			"subDid": 	// 子设备did，字符串类型
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		device: {   	// 子设备对象（以下字段是子设备信息），对象类型
			"mac":					// 中控设备mac地址，字符串类型
			"did": 					// 中控设备did，字符串类型
			"subDid": 				// 子设备did，字符串类型
			"subProductKey":			// 子设备类型标识，字符串类型
			"subProductName":		// 子设备产品名称，字符串类型
			"type”:					// 子设备类型，数字类型
			"isOnline":				// 子设备是否在线，布尔类型
			"productKey":				// 中控设备类型标识，字符串类型
			"productName":			// 中控设备产品名称，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		device:{   	// 请求注册的设备对象（以下字段是设备对象信息），对象类型
			"mac":		// 设备mac地址，字符串类型
			"did": 		// 设备did，字符串类型
			"subDid": 	// 子设备did，字符串类型
		}
	}

###示例代码
	var gizWifiSubDevice = api.require('gizWifiSubDevice');
	gizWifiSubDevice.getDeviceInfo({
		"device": {
			"mac": ’xxx’,
			"did": ’xxx’,
			"subDid": ’xxx’
		}
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


# gizWifiGroup类接口

机智云 Wi-Fi 的设备分组类。该类提供了中控子设备分组功能。

#**getDevices**<div id="a43"></div>
 
获取分组设备列表。

getDevices({params}, callback(ret, err))

###params

group: 

* 类型： JSON对象
* 默认值：无
* 描述：组对象，组对象信息可以在获取分组列表时得到。
* 内部字段

		{
			"gid":		// 组ID，字符串类型
		}

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		group:{   	// 组对象（以下字段是组信息），对象类型
			"gid": 		// 组ID，字符串类型
		}
		devices:[{   		// 分组子设备列表，对象数组类型
			"mac": 		// 中控设备mac，字符串类型
			"did":		// 中控设备did，字符串类型
			"subDid":		// 子设备did，字符串类型
		}]
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		group:{   	// 请求注册的设备对象（以下字段是设备对象信息），对象类型
			"gid":	// 组ID，字符串类型
		}
	}

###示例代码
	var gizWifiGroup = api.require('gizWifiGroup');
	gizWifiGroup.getDevices({
		"group": {
	       		"gid": ’xxx’
		}
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**addDevice**<div id="a44"></div>

向组中添加设备。添加后，返回添加后的设备列表。

addDevice({params}, callback(ret, err))

###params
group: 

* 类型： JSON对象
* 默认值：无
* 描述：组对象，组对象信息可以在获取分组列表时得到。
* 内部字段

		{
			"gid":		// 组ID，字符串类型
		}

device: 

* 类型： JSON对象
* 默认值：无
* 描述：要添加的设备对象，设备对象信息可以在获取分组设备列表时得到。
* 内部字段

		{
			"mac":		// 中控设备mac地址，字符串类型
			"did": 		// 中控设备did，字符串类型
			"subDid": 	// 子设备did，字符串类型
		}

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		group:{   	// 组对象（以下字段是组信息），对象类型
			"gid": 		// 组ID，字符串类型
		}
		devices:[{   		// 分组子设备列表，对象数组类型
			"mac": 		// 中控设备mac，字符串类型
			"did":		// 中控设备did，字符串类型
			"subDid":		// 子设备did，字符串类型
		}]
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		group:{   	// 请求注册的设备对象（以下字段是设备对象信息），对象类型
			"gid":	// 组ID，字符串类型
		}
	}

###示例代码
	var gizWifiGroup = api.require('gizWifiGroup');
	gizWifiGroup.addDevice({
	        "group": {
	            "gid": ’xxx’
	        },
	       "device":{
			"did": ’xxx’,
			"mac": ’xxx’,
			"subDid": ’xxx’
	       }
	}, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

#**removeDevice**<div id="a45"></div>
 
删除分组内的设备。删除后，返回删除后的设备列表。

removeDevice({params}, callback(ret, err))

###params

group: 

* 类型： JSON对象
* 默认值：无
* 描述：组对象，组对象信息可以在获取分组列表时得到。
* 内部字段

		{
			"gid":		// 组ID，字符串类型
		}

device: 

* 类型： JSON对象
* 默认值：无
* 描述：要删除的设备对象，设备对象信息可以在获取分组设备列表时得到。
* 内部字段

		{
			"mac":		// 中控设备mac地址，字符串类型
			"did": 		// 中控设备did，字符串类型
			"subDid": 	// 子设备did，字符串类型
		}

###callback(ret, err)

ret

* 类型：JSON 对象
* 内部字段

	{
		group:{   	// 组对象（以下字段是组信息），对象类型
			"gid": 		// 组ID，字符串类型
		}
		devices:[{   		// 分组子设备列表，对象数组类型
			"mac": 		// 中控设备mac，字符串类型
			"did":		// 中控设备did，字符串类型
			"subDid":		// 子设备did，字符串类型
		}]
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		group:{   	// 请求注册的设备对象（以下字段是设备对象信息），对象类型
			“gid”:	// 组ID，字符串类型
		}
	}

###示例代码
	var gizWifiGroup = api.require('gizWifiGroup');
	gizWifiGroup.removeDevice({
	        "group": {
	            "gid": ’xxx’
	        },
	        "device":{
			"did": ’xxx’,
			"mac": ’xxx’,
			"subDid": ’xxx’
	        }
	 }, function(ret, err) {
	    	alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本


#**getGroupInfo**<div id="a46"></div>

获取分组设备列表。

getGroupInfo({params}, callback(ret, err))

###params
group: 

* 类型： JSON对象
* 默认值：无
* 描述：组对象，组对象信息可以在获取分组列表时得到。
* 内部字段

		{
			"gid":		// 组ID，字符串类型
		}

###callback(ret, err)
ret

* 类型：JSON 对象
* 内部字段

	{
		group:{   	// 组对象（以下字段是组信息），对象类型
			"gid": 			// 组ID，字符串类型
			"groupName": 	// 组名称，字符串类型
			"productKey": 	// 组类型标识，字符串类型
		}
	}

err

* 类型：JSON 对象
* 内部字段

	{
		errorCode:	// 错误代码，数字类型
		msg:		// 错误描述，字符串类型
		group:{   	// 设备对象（以下字段是设备对象信息），对象类型
			"gid":	// 组ID，字符串类型
		}
	}

###示例代码
	var gizWifiGroup = api.require('gizWifiGroup');
	gizWifiGroup.getGroupInfo({
		"group": {
	        	"gid": ’xxx’
		}
	}, function(ret, err) {
		alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err))
	});

###可用性
iOS系统，Android系统

可提供的1.0.0及更高版本

</div>


<div id="const-content">

#**常量定义**

Json字段名及常量说明：

mode  | 设备配置方式
---------- |   --------  |
softAP  | 软AP配置方式：1
airLink  | 一键配置方式：2

logLevel  | 日志级别
---------- |   --------  |
none  | 原生SDK无日志输出：0
error  | 错误日志输出：1
debug  | 警告日志输出：2
all  | 全部日志输出：3

type  | 设备分类
---------- |   --------  |
nomal  | 普通设备：0
centralControl  | 中控设备：1

thirdAccountType  | 第三方账号类型
---------- |   --------  |
BAIDU  | 百度账号：0
SINA  | 新浪账号：1
QQ  | 腾讯账号：2

UserGenderType  | 用户性别
---------- |   --------  |
Male  | 男：0
Female  | 女：1
Unknow  | 其他：2

GAgentType  | 模组类型
---------- |   --------  |
MXCHIP  | MXCHIP 1.x 模组（庆科3162）：0
HF  | HF 模组（汉枫）：1
RTK  | RTK 模组（RealTek）：2
WM  | WM 模组（联盛德）：3
ESP  | ESP 模组（乐鑫）：4
QCA  | QCA 模组（高通）：5
TI  | TI 模组（TI）：6



#**错误码描述**

errorCode |       msg  |
---------- |   --------  |
0  | GizWifiError_SUCCESS
-1  | GizWifiError_GENERAL
-2  | GizWifiError_NOT_IMPLEMENTED
-4  | GizWifiError_PACKET_DATALEN
-5  | GizWifiError_CONNECTION_ID
-7  | GizWifiError_CONNECTION_CLOSED
-8  | GizWifiError_PACKET_CHECKSUM
-9  | GizWifiError_LOGIN_VERIFY_FAILED
-10  | GizWifiError_NOT_LOGINED
-11  | GizWifiError_NOT_CONNECTED
-12  | GizWifiError_MQTT_FAIL
-13  | GizWifiError_DISCOVERY_MISMATCH
-14  | GizWifiError_SET_SOCK_OPT
-15  | GizWifiError_THREAD_CREATE
-17  | GizWifiError_CONNECTION_POOL_FULLED
-18  | GizWifiError_NULL_CLIENT_ID
-19  | GizWifiError_CONNECTION_ERROR
-20  | GizWifiError_INVALID_PARAM
-21  | GizWifiError_CONNECT_TIMEOUT
-22  | GizWifiError_INVALID_VERSION
-23  | GizWifiError_INSUFFIENT_MEM
-24  | GizWifiError_THREAD_BUSY
-25  | GizWifiError_HTTP_FAIL
-26  | GizWifiError_GET_PASSCODE_FAIL
-27  | GizWifiError_DNS_FAILED
-30  | GizWifiError_UDP_PORT_BIND_FAILED
-39  | GizWifiError_CONFIGURE_SSID_NOT_MATCHED
-40  | GizWifiError_CONFIGURE_TIMEOUT
-41  | GizWifiError_CONFIGURE_SENDFAILED
-42  | GizWifiError_NOT_IN_SOFTAPMODE
-43  | GizWifiError_UNRECOGNIZED_DATA
-44  | GizWifiError_CONNECTION_NO_GATEWAY
-45  | GizWifiError_CONNECTION_REFUSED
-46  | GizWifiError_IS_RUNNING
-47  | GizWifiError_UNSUPPORTED_API
-48  | GizWifiError_RAW_DATA_TRANSMIT
-60  | GizWifiError_SDK_INIT_FAILED
-61  | GizWifiError_DEVICE_IS_INVALID
-62  | GizWifiError_GROUP_IS_INVALID
9001|mac already registered!
9002|product_key invalid!
9003|appid invalid!
9004|token invalid!
9005|user does not exist!
9006|token expired!
9007|m2m_id invalid
9008|server error
9009|code expired
9010|code invalid
9011|sandbox scale quota exhausted!
9012|production scale quota exhausted!
9013|product has no request scale!
9014|device not found!
9015|form_invalid
9016|did or passcode invalid!
9017|device not bound!
9018|phone unavailable!
9019|username unavailable!
9020|username or password error!
9021|send command failed!
9022|email unavailable!
9023|device is disabled!
9024|fail to notify m2m!
9025|attr invalid!
9026|user invalid!
9027|firmware not found!
9028|JD product info not found!
9029|datapoint data not found!
9030|scheduler not found!
9031|qq oauth key invalid!
9999|reserved




