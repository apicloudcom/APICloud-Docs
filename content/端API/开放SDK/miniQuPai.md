/*
Title: miniQuPai
Description: miniQuPai
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

#**微视频云接入**

开发者在使用miniQuPai模块时，需要开发者自行到趣拍的微视频云申请相应的AppKey和AppSecret。

该AppKey的申请与您应用的创建过程有关，具体流程请参考如下介绍。

##申请步骤
1、登录趣拍帐号

访问微视频云控制台页面，若您未登录账号，将会进入账号登录页面， 登录地址：http://vcs.qupai.me/dq.html#/login 如下图：

![描述](http://community.apicloud.com/bbs/data/attachment/forum/201602/27/170806tr7z33w0g37o667r.png)

2、登陆趣拍云控制台，具体如下图：
![描述](http://community.apicloud.com/bbs/data/attachment/forum/201602/27/170815jlllirypmrli4iyp.png)

3、创建应用
点击"创建应用"，系统将为您弹出需要填写应用的相关信息，具体如下图：
![描述](http://community.apicloud.com/bbs/data/attachment/forum/201602/27/170822txaaaoxhfhm0ylky.png)

4、获取AppKey和AppSecret

注册成功后，在应用管理里面“密钥”处查看AppKey和AppSecret，具体如下图：
![描述](http://community.apicloud.com/bbs/data/attachment/forum/201602/27/170828llke5ibyz20a050g.png)


5、IOS和Android平台的签名设置

IOS平台：使用官方的证书时如果是使用在线云编译，请填写BundleID为com.apicloud.testapp，如果是使用自定义loader请填写BundleID为com.apicloud.customloader。如果是自己证书定义的包名，请填写实际包名。

Android平台：通过apicloud官方的云平台获取Android包名，如果是自己定义的包名，请填写自己定义的包名，然后
通过下载使用趣拍平台提供的<a href="http://download.qupai.me/paas/home/app_signatures.apk">签名工具</a>输入包名生成"Android签名"内容，设置后的信息具体如下图：
![描述](http://community.apicloud.com/bbs/data/attachment/forum/201603/03/110044ualqm3x973a0z369.png)







<div class="outline">
[init](#a1)
[record](#a2)
[upload](#a3)
</div>
#**概述**

1、miniQuPai模块，实现了IOS、 Android 平台集成趣拍SDK极简版本模块。可以设置录制时长、视频码率、图片质量、拍摄布局高度、美颜参数等丰富了app视频录制相关功能   ;

2、远程视频地址通过拼接取得，格式为<a href="http://vcs.qupai.me/">http://{domain}/v/{remoteId}.mp4/?token={accessToken} </a>

2.1、{domain}通过开发控制台得到,获取地址具体如下图：
![描述](http://community.apicloud.com/bbs/data/attachment/forum/201603/07/162141p9c58059xgucxuqs.png)

2.2、{remoteId}通过上传接口remoteId : "",//上传成功中返回视频在服务端存储的remoteId

2.3、{accessToken}通过初始化鉴权成功之后返回的ACCESS-TOKEN





#**使用须知**
在<a href="http://vcs.qupai.me/">http://vcs.qupai.me/</a>上注册账号，申请App Key 和 App Secret。（注意：<font color=red>BundleID 、Android包名、Android签名</font>这三个参数，自定义和云编译等，app软件都要对应，否则初始化会失败。）

<div id="a1"></div>
#**init**

初始化sdk

init({params}, callback(ret, err))

##params

appKey：

- 类型：字符串
- 描述：申请的appKey。

appsecret：

- 类型：字符串
- 描述：申请的appsecret。

space：

- 类型：字符串
- 描述：存储视频文件夹名称。

##示例代码

```js
var demo = api.require('miniQuPai');
demo.init({appKey:'204955a834a7c36',appsecret:'55e409dc27c04a87be124a2939348b58',space:'uid'},
function(ret, err){
alert(JSON.stringify(ret));
});
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true,        //布尔型；true||false
	accessToken : ""     //字符串类型；鉴权成功之后返回的ACCESS-TOKEN
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg: ""            //字符串类型；错误信息
}
```


##可用性

IOS、Android系统

可提供的1.0.0及更高版本


<div id="a2"></div>
#**record**

录制视频

record({params}, callback(ret, err))

##params

minDuration：

- 类型：数字
- 描述：（可选项）允许拍摄的最小时长；
- 默认值：2

maxDuration：

- 类型：数字
- 描述：（可选项）允许拍摄的最大时长，时长越大，产生的视频文件越大；
- 默认值：8

bitRate：

- 类型：数字
- 描述：（可选项）视频码率，建议800*1000-5000*1000,码率越大，视频越清析，视频文件也会越大。参考：8秒的视频以2000*1000的码率压缩，文件大小1.5M-2M。请开发者根据自己的业务场景设置时长和码率；
- 默认值：800 * 1024

videoWidth：

- 类型：数字类型
- 描述：（可选项）输出视频的尺寸>宽；
- 默认值：480

videoHeight：

- 类型：数字类型
- 描述：（可选项）输出视频的尺寸>高；
- 默认值：480

captureHeight：

- 类型：数字类型
- 描述：（可选项）拍摄布局高度；
- 默认值：118

beautySkinViewOn：

- 类型：布尔型
- 描述：（可选项）美颜是否显示
- 默认值：false

beautySkinProgress：

- 类型：数字类型
- 描述：（可选项）美颜参数；
- 默认值：80


flashlightViewOn：

- 类型：布尔型
- 描述：（可选项）闪光灯是否显示
- 默认值：false

timelineIndicatorOn：

- 类型：布尔型
- 描述：（可选项）时间提示是否显示
- 默认值：false

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true,         //布尔型；true||false
	data : {
	   videoPath:"",      //字符串类型；视频存放路径 
	   thumbnailPath:"",  //字符串类型；缩略图路径
	   duration:1233      //字符串类型；视频时长(仅Android有)
	}
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg: ""              //字符串类型；错误信息
}
```

##示例代码

```js
var param = {
	minDuration:2,
	maxDuration:20,
	bitRate:2000000,
	videoWidth:320,
	videoHeight:480,
	captureHeight:120,
	beautySkinProgress:80,
	beautySkinViewOn:true,
	flashlightViewOn:true,
	timelineIndicatorOn:true
};
var demo = api.require('miniQuPai');
	demo.record(param, function(ret, err){
	alert(JSON.stringify(ret));
});
```

##可用性

IOS、Android系统

可提供的1.0.0及更高版本


<div id="a3"></div>
#**upload**

上传视频

upload({params}, callback(ret, err))

##params

videoPath：

- 类型：字符串类型
- 描述：录制视频的路径；

thumbnailPath：

- 类型：字符串类型
- 描述：录制视频的缩略图；

shareType：

- 类型：数类型
- 描述：（可选项）是否公开 0公开分享 1私有(default) 公开类视频不需要AccessToken授权；
- 默认值：1

description：

- 类型：字符串类型
- 描述：（可选项）描述信息；

tags：

- 类型：字符串类型
- 描述：（可选项）标签 多个标签用 "," 分隔符；

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true,   //布尔型；true||false
	remoteId : "",  //字符串类型；上传成功中返回视频在服务端存储的remoteId
	progress:0.2    //字符串类型；上传进度 (上传中ret只有这个属性传输上传进度值)
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
   msg: ""         //字符串类型；错误信息
}
```

##示例代码

```js
var demo = api.require('miniQuPai');
var param = {
	videoPath:$api.getStorage('videoPath'),
	thumbnailPath:$api.getStorage('thumbnailPath'),
	shareType:1,
	description:"测试视频",
	tags:"视频,录制"
};
demo.upload(param, function(ret, err){
if(ret.progress){
   api.toast({msg:JSON.stringify(ret)});//上传进度
}else if(ret.status){
   alert(JSON.stringify(ret));//上传成功
}else{
   alert(JSON.stringify(ret));//上传失败
}
});
```

##可用性

IOS、Android系统

可提供的1.0.0及更高版本