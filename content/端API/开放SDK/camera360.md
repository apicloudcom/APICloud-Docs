/*
Title: camera360
Description: camera360
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">

[open](#1)

</div>

#**概述**

camera360模块封装了 Camera360 的开放 SDK，使用本模块可实现对图片的特效、虚化、裁剪、旋转、光影、边框等处理。 使用本模块需要到 http://sdk.camera360.com 申请 camera360 的开发者账号并创建应用并获取到key，由于Android camera360的开放sdk问题，在处理某些图片时可能会出现未知错误。

**使用此模块之前需先配置  config.xml 文件，配置完毕，需通过云端编译生效，配置方法如下：**

- 名称：camera360
- 参数：apiKey
- 配置示例:

```xml
  <feature name="camera360">
    <param name="android_api_key" value="hk5qVtkovqMu/jiSM+pHuVCwOkiDn5PppbAr7hb05Of9Jcd4+SXVsDetWTQUE9P1gt....."/>
    <param name="ios_api_key" value="hk5qVtkovqMu/jiSM+pHuVCwOkiDn5PppbAr7hb05Of9Jcd4+SXVsDetWTQUE9P1gt....."/>
  </feature>
```

- 字段描述:

   **apiKey**：（必须配置）在 camera360 开放平台创建应用后，该平台会为每个应用分配一个Key，在 IOS 平台上注意包名（应用概览里可以查看）和 Key 要对应。
    


#**open**<div id="1"></div>

打开 camera360 开始编辑图片

open({params}, callback(ret)) 

##params

path:

- 类型：字符串
- 描述：原始图片的路径，要求本地路径（fs://、widget://）**android不支持 widget 协议**

savePath:

- 类型： 字符串
- 描述： 处理完毕后，图片的保存路径，要求本地路径（fs://）,不支持 widget 协议**


##callback(ret)

ret:

- 类型：JSON对象
- 内部字段：
  
```js
{
   eventType:'finish',        //字符串类型；回调事件类型，取值范围如下：
                              //finish（图片处理完成）
                              //cancel（用户取消）
                              //fail（图片处理失败）
   thumbPath: '',             //字符串类型；处理完后图片的缩略图绝对路径
   path: ''                   //字符串类型；处理后的图片绝对路径
}
```


##示例代码

```js

	var obj = api.require('camera360');
	var msg = {

	  path:'fs://test.jpg',
	  savePath:'fs://processed_test.jpg'

	}
	obj.open(msg, function(ret){
		api.alert({msg:JSON.stringify(ret)});
	}); 
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

