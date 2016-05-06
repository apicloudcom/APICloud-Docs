/*
Title: csOpenApi
Description: Domob APICloud 接口文档
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：上海合合信息科技发展有限公司</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[auth](#a1)
[getDownloadLink](#a2)
[getOpenApiVersion](#a3)
[isCamScannerAvailable](#a4)
[isCamScannerInstalled](#a5)
[scanImage](#a6)
</div>


#**概述**

csOpenApi模块封装了扫描全能王图片处理的Open API。

扫描全能王OpenAPI ( CamScanner Open API ) 是基于扫描全能王强大的图像处理能力，为第三方应用提供图像处理方案的公开接口。它可以提供给第三方的功能有：

+ 1）	智能找边
+ 2）	图像剪裁
+ 3）	5种图像美化模式
+ 4）	3种图像细节调整类型



#**auth**<div id="a1"></div>

授权, 调用scanImage处理图片之前必须先完成授权。

app_key可以访问https://dev.camscanner.com/进行申请

auth({params})

##params()

app_key：

- 类型：字符串
- 默认值：无
- 描述：从CamScanner处申请得到的app_key, 必须传入

user_id：

- 类型：字符串
- 默认值：无
- 描述：可选字段，从CamScanner处申请得到的user_id, 若没有该值，可不传


##示例代码

```js
var openapimodule = api.require('csOpenApi');
var param = {app_key:"123",user_id:"123"};
openapimodule.auth(param);
```

##补充说明

注册应用

##可用性

Android系统

可提供的1.0.0及更高版本


#**getDownloadLink**<div id="a2"></div>

获取 扫描全能王CamScanner 的下载链接。

getDownloadLink(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	result:http://xxx...		//CamScanner 下载链接
}
```

##示例代码

```js
var openapimodule = api.require('csOpenApi');
var resultCallback = function(ret){
	document.getElementById("download_link").innerHTML = JSON.stringify(ret);
};
openapimodule.getDownloadLink(resultCallback);
```

##补充说明

获取 扫描全能王CamScanner 的下载链接。

##可用性

Android系统

可提供的1.0.0及更高版本


#**getOpenApiVersion**<div id="a3"></div>

获取当前手机上安装的扫描全能王CamScanner支持的最低Open API版本号。

getOpenApiVersion(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	result:1.0		//当前CamScanner APP支持的最低OpenAPI版本号；若不支持，则返回-1
}
```

##示例代码

```js
var openapimodule = api.require('csOpenApi');
var resultCallback = function(ret){
	document.getElementById("version").innerHTML = JSON.stringify(ret);
};
openapimodule.getOpenApiVersion(resultCallback);
```

##补充说明

获取当前手机上安装的扫描全能王CamScanner支持的最低Open API版本号。

##可用性

Android系统

可提供的1.0.0及更高版本


#**isCamScannerAvailable**<div id="a4"></div>

判断当前手机上是否安装了支持Open API的CamScanner APP

isCamScannerAvailable(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	result:true		// true:手机上安装了可用的CamScanner,否则返回false
}
```

##示例代码

```js
var openapimodule = api.require('csOpenApi');
var resultCallback = function(ret){
	document.getElementById("cs_available").innerHTML = JSON.stringify(ret);
};
openapimodule.isCamScannerAvailable(resultCallback);
```

##补充说明

判断当前手机上是否安装了支持Open API的CamScanner APP

##可用性

Android系统

可提供的1.0.0及更高版本

#**isCamScannerInstalled**<div id="a5"></div>

判断当前手机上是否安装了CamScanner

isCamScannerInstalled(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	result:1		// >0 安装了CamScanner;; -1 = 没有安装Camscanner
}
```

##示例代码

```js
var openapimodule = api.require('csOpenApi');
var resultCallback = function(ret){
	document.getElementById("cs_install").innerHTML = JSON.stringify(ret);
};
openapimodule.isCamScannerInstalled(resultCallback);
```

##补充说明

判断当前手机上是否安装了CamScanner

##可用性

Android系统

可提供的1.0.0及更高版本

#**scanImage**<div id="a6"></div>

处理图片

scanImage({params}, callback(ret, err))

##params()

source_path：

- 类型：字符串
- 默认值：无
- 描述：待处理原图路径, 必须传入，需要保证图片是合法的jpg图片

result_img_path：

- 类型：字符串
- 默认值：无
- 描述：扫描全能王处理后生成的图片路径，必须传入

result_pdf_path：

- 类型：字符串
- 默认值：无
- 描述：扫描全能王处理后生成的pdf路径，必须传入

original_path：

- 类型：字符串
- 默认值：无
- 描述：扫描全能王返回的原图路径，可选字段

api_version：

- 类型：字符串
- 默认值：无
- 描述：请求所需最低的OPEN API版本号，可选字段

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	error_code:6001		//CamScanner处理后的返回码
	error_msg: OK		//CamScanner处理后返回的消息
}
```

##示例代码

```js
var openapimodule = api.require('csOpenApi');
var param = {source_path:"sdcard/CSOpenApiDemo/source.jpg",
	result_img_path:"sdcard/CSOpenApiDemo/result.jpg",
	result_pdf_path:"sdcard/CSOpenApiDemo/result.pdf",
	original_path:"sdcard/CSOpenApiDemo/ori.jpg",
	api_version:"1.0"};
var resultCallback = function(ret){
	document.getElementById("scan_image").innerHTML = JSON.stringify(ret);
};
openapimodule.scanImage(param, resultCallback);
```
</div>
<div id="const-content">
##补充说明

Return Code 返回码列表

- 6000: 返回结果正常
- 6001: 用户取消了操作
- 6002: 传入的参数不合法，可能由于source_path对应的图片不合法。
- 6003: 当前设备上没有安装有效的CamScanner应用
- 4002: 应用授权错误，请传入正确的APP_KEY。
- 4004: 应用包名错误。 请调用CamScanner OpenAPI by startActivityForResult()。
- 4006: 原图片错误，可能是源图不存在、损坏，或者不是JPG类型。
- 5003: 第三方应用授权时间过期。
- 5006: 第三方应用选择的美化模式不在授权范围内。
- 5007: 已到达第三方应用申请的请求次数上限。
- 5008: 访问的设备数超过限制。
- 5009: 应用请求的api_version高于当前CamScanner提供的版本
- 5010: 请求必须在登录状态下使用，但是用户没有选择登录
- 5011: 请求设备ID错误
- 7001: 无法保存扫描后的图片。可能是图片受损，或者本地没有足够的存储空间。 
- 7002: 无法保存扫描后生成的PDF。可能是PDF受损，或者本地没有足够的存储空间。 
- 7003: 无法保存原图。可能是PDF受损，或者本地没有足够的存储空间。 


##可用性

Android系统

可提供的1.0.0及更高版本
