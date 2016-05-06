/*
Title: seckenModule
Description: 洋葱SDK是帮助移动应用快速集成多维身份验证的开发工具集.
Version: v1.0.1
Date: 2015-11-24
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：洋葱</p>

<div class="outline">
[init](#a1)

[auth](#a3)

[qrcode](#a4)

[faceTrain](#a5)

[faceCompare](#a6)

[voiceTrain](#a7)

[voiceCompare](#a8)

[faceDelete](#a9)

[voiceDelete](#a10)

[unBind](#a11)

[hasFace](#a12)

[hasVoice](#a13)
</div>

#**概述**

洋葱SDK是帮助移动应用快速集成多维身份验证的开发工具集.

移动应用可通过集成洋葱SDK，快速实现二维码登录、指纹识别、声纹识别或人脸识别功能，更加有效的提高识别的安全性和真实性，还能利用位置和网络等信息作为安全识别的重要依据.

   在使用Secken SDK为您提供的各种功能之前，您需要先到洋葱的开发者中心注册移动应用，并获取APP_ID和APP_KEY。（注：洋葱官网的账号和开发者中心账号通用）

洋葱开发者中心地址：https://www.yangcong.com/signin

开发前请先认真阅读相关的洋葱开发文档。

	var seckenModule = null;
	apiready = function(){
	   seckenModule = api.require('seckenModule');
	}
    
<div id="a1"></div>

#**init**

初始化操作,在使用其它功能前,请先调用该方法进行初始化


##params

appKey：

- 类型：字符串
- 描述：分配给每个第三方应用的appKey，用于鉴权签名等功能。

app_id：

- 类型：字符串
- 描述：分配给每个第三方应用的app_id，用于识别应用的标示


##示例代码



	  var param={appKey:"********",app_id:"******"};
	  seckenModule.init(param);


##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本


<div id="a3"></div>

#**auth**

在Secken开发者平台申请应用的客户端情况下，使用sdk授权即可授权客户端，之后才能使用sdk的其他功能。


##params

username：

- 类型：字符串
- 描述：第三方APP用户的唯一标示，用于确定用户的唯一性



##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数


内部字段：

		{
    		status: true   //布尔型；true||false
			token:"";//仅作为本次授权身份验证token，用于SeckenSDK其他接口的调用。不作为用户唯			一id	使用。（有效期为一周，建议在token到期之前重新授权获取新的token）
		}


err：

- 类型：JSON 对象
- 描述：返回参数


内部字段：

		{
    		errorCode: //错误码
			errorMsg:  //错误信息
		}


##示例代码


		var param = {username:"ceshi123"};
		var resultCallback = function(ret, err){
	        if(ret.status){
	        	alert(JSON.stringify(ret));
			}else{
				alert(JSON.stringify(err));
			}
	    }
	    seckenModule.auth(param,resultCallback);


##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本

<div id="a4"></div>

#**qrcode**

调用SeckenSDK扫描功能，可实现客户端扫码，服务器端验证用户身份的功能。


##params

token：

- 类型：字符串
- 描述：仅作为本次授权身份验证token，用于SeckenSDK其他接口的调用。不作为用户唯一id使用。（有效期为一周，建议在token到期之前重新授权获取新的token）

username：

- 类型：字符串
- 描述：第三方APP用户的唯一标示，用于确定用户的唯一性


##示例代码


		var param = {token:"835735673Af",username:"ceshi123"};
		seckenModule.qrcode(param);

##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本

<div id="a5"></div>

#**faceTrain**

通过跳转SeckenSDK的人脸训练页面识别头像信息，成功识别三次则创建人脸信息成功，即可使用人脸验证功能；


##params

token：

- 类型：字符串
- 描述：仅作为本次授权身份验证token，用于SeckenSDK其他接口的调用。不作为用户唯一id使用。（有效期为一周，建议在token到期之前重新授权获取新的token）

username：

- 类型：字符串
- 描述：第三方APP用户的唯一标示，用于确定用户的唯一性

##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数

内部字段：


	{
    	status: true   //布尔型；true||false
		result: "训练成功";
	}

err：

- 类型：JSON 对象
- 描述：返回参数

内部字段：


	{
		result:  “训练失败”；
	}

##示例代码


	var param = {token:"835735673Af",username:"ceshi123"};
	var resultCallback = function(ret, err){
		if(ret.status){
	        alert(JSON.stringify(ret));
		}else{
			alert(JSON.stringify(err));
		}
	}
	seckenModule.faceTrain(param,resultCallback);


##可用性

Android系统  iOS系统

可提供的1.0.1及更高版本

<div id="a6"></div>

#**faceCompare**

通过跳转SeckenSDK的人脸验证页面，由服务器返回该头像信息是否为创建时候的人脸信息作为人脸是否验证成功的标志。


##params

token：

- 类型：字符串
- 描述：仅作为本次授权身份验证token，用于SeckenSDK其他接口的调用。不作为用户唯一id使用。（有效期为一周，建议在token到期之前重新授权获取新的token）

username：

- 类型：字符串
- 描述：第三方APP用户的唯一标示，用于确定用户的唯一性

##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    status: true   //布尔型；true||false
			result: "验证成功";
			auth_token:"";//集成SeckenSDK的app可将该字段提交至自己服务器，由自己服务器和洋葱			服务器进行二次确认，以确保洋葱SDK返回的验证结果未被篡改。(跟洋葱服务器进行二次确认接			口：https://api.sdk.yangcong.com/query_auth_token)
		}


err：

- 类型：JSON 对象
- 描述：返回参数

内部字段：


		{
			result:  “验证失败”；
		}

##示例代码


	var param = {token:"835735673Af",username:"ceshi123"};
	var resultCallback = function(ret, err){
		if(ret.status){
	        alert(JSON.stringify(ret));
		}else{
			alert(JSON.stringify(err));
		}
	}
	seckenModule.faceCompare(param,resultCallback);


##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本

<div id="a7"></div>

#**voiceTrain**

通过跳转SeckenSDK声音训练页面进行采集用户声音信息，采集三次成功则创建声音验证信息成功，即可使用声音验证功能；


##params

token：

- 类型：字符串
- 描述：仅作为本次授权身份验证token，用于SeckenSDK其他接口的调用。不作为用户唯一id使用。（有效期为一周，建议在token到期之前重新授权获取新的token）

username：

- 类型：字符串
- 描述：第三方APP用户的唯一标示，用于确定用户的唯一性

##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    status: true   //布尔型；true||false
			result: "训练成功";
		}

err：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
			result:  “训练失败”；
		}


##示例代码


		var param = {token:"835735673Af",username:"ceshi123"};
		var resultCallback = function(ret, err){
		    if(ret.status){
	        	alert(JSON.stringify(ret));
			}else{
				alert(JSON.stringify(err));
			}
	    }
		seckenModule.voiceTrain(param,resultCallback);


##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本

<div id="a8"></div>

#**voiceCompare**

通过跳转SeckenSDK的声音验证页面采集用户声音信息进行验证是否为创建声音的声音信息。


##params

token：

- 类型：字符串
- 描述：仅作为本次授权身份验证token，用于SeckenSDK其他接口的调用。不作为用户唯一id使用。（有效期为一周，建议在token到期之前重新授权获取新的token）

username：

- 类型：字符串
- 描述：第三方APP用户的唯一标示，用于确定用户的唯一性

##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
    		status: true   //布尔型；true||false
			result: "验证成功";
			auth_token:"";//集成SeckenSDK的app可将该字段提交至自己服务器，由自己服务器和洋葱			服务器进行二次确认，以确保洋葱SDK返回的验证结果未被篡改。(跟洋葱服务器进行二次确认接			口：https://api.sdk.yangcong.com/query_auth_token)
		}

err：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
			result:  “验证失败”；
		}

##示例代码


		var param = {token:"835735673Af",username:"ceshi123"};
		var resultCallback = function(ret, err){
		    if(ret.status){
	        	alert(JSON.stringify(ret));
			}else{
				alert(JSON.stringify(err));
			}
	    }
		seckenModule.voiceCompare(param,resultCallback);


##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本

<div id="a9"></div>

#**faceDelete**

删除人脸验证的一切相关信息。注：删除后用户将无法使用人脸验证


##params

token：

- 类型：字符串
- 描述：仅作为本次授权身份验证token，用于SeckenSDK其他接口的调用。不作为用户唯一id使用。（有效期为一周，建议在token到期之前重新授权获取新的token）

username：

- 类型：字符串
- 描述：第三方APP用户的唯一标示，用于确定用户的唯一性

##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    status: true   //布尔型；true||false
		}

err：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    errorCode: //错误码
			errorMsg:  //错误信息
		}


##示例代码


		var param = {token:"835735673Af",username:"ceshi123"};
		var resultCallback = function(ret, err){
	        if("fail" == ret.status){
				alert(ret.errorMsg);
			}else{
				alert(ret.status);
			}
	    }
		seckenModule.faceDelete(param,resultCallback);


##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本

<div id="a10"></div>

#**voiceDelete**

删除声音验证的一切相关信息。注：删除后用户将无法使用声音验证


##params

token：

- 类型：字符串
- 描述：仅作为本次授权身份验证token，用于SeckenSDK其他接口的调用。不作为用户唯一id使用。（有效期为一周，建议在token到期之前重新授权获取新的token）

username：

- 类型：字符串
- 描述：第三方APP用户的唯一标示，用于确定用户的唯一性

##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    status: true   //布尔型；true||false
		}


err：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    errorCode: //错误码
			errorMsg:  //错误信息
		}


##示例代码


		var param = {token:"835735673Af",username:"ceshi123"};
		var resultCallback = function(ret, err){
	        if(ret.status){
				alert(ret.errorMsg);
			}else{
				alert(ret.status);
			}
	    }
		seckenModule.voiceDelete(param,resultCallback);


##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本

<div id="a11"></div>

#**unBind**

取消用户的授权，客户端将不能使用SDK功能，但是不删除授权的声音和人脸信息，下次授权用户仍然可以使用之前训练的人脸和声音进行验证。


##params

token：

- 类型：字符串
- 描述：仅作为本次授权身份验证token，用于SeckenSDK其他接口的调用。不作为用户唯一id使用。（有效期为一周，建议在token到期之前重新授权获取新的token）

username：

- 类型：字符串
- 描述：第三方APP用户的唯一标示，用于确定用户的唯一性

##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    status: true   //布尔型；true||false
		}


err：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    errorCode: //错误码
			errorMsg:  //错误信息
		}


##示例代码


		var param = {token:"835735673Af",username:"ceshi123"};
		var resultCallback = function(ret, err){
			if(ret.status){
	        	alert(JSON.stringify(ret));
			}else{
				alert(JSON.stringify(err));
			}
	    }
		seckenModule.unBind(param,resultCallback);


##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本

<div id="a12"></div>

#**hasFace**

判断是否存在人脸信息。（注：需要授权之后才有效）

##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    status: true   //布尔型；true||false
			hasFace：true //true为有人脸信息,false为无人脸信息
		}


##示例代码


		var resultCallback = function(ret, err){
	        alert(ret.hasFace);
	    }
		seckenModule.hasFace(resultCallback);

##可用性

Android系统

可提供的1.0.1及更高版本

<div id="a13"></div>

#**hasVoice**

判断是否存在声音信息。（注：需要授权之后才有效）

##callback(ret, err)


ret：

- 类型：JSON 对象
- 描述：返回参数

内部字段：

		{
		    status: true   //布尔型；true||false
			hasVoice：true //true为有声音信息,false为无声音信息
		}


##示例代码


		var resultCallback = function(ret, err){
	        alert(ret.hasVoice);
	    }
		seckenModule.hasVoice(resultCallback); 

##可用性

Android系统 iOS系统

可提供的1.0.1及更高版本

