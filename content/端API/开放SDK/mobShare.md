/*
Title: mobShare
Description: mobShare
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<div class="outline">
[share](#m1)

[shareTo](#m2)
</div>

<div id="m1"></div>
#**概述**

mobShare封装了 mob 开发者服务平台的 shareSDK，使用此模块可实现分享文字、图片、图文、音乐、视频、链接到微信、微博、Facebook、Twitter等多个平台。调用 share 接口，模块会弹出可分享平台列表（可通过 [config.xml](/APICloud/技术专题/app-config-manual) 和 key.xml 文件配置信息自定义数量）菜单供用户选择分享。使用本模块需要到 http://www.mob.com 申请 shareSDK 模块的开发者账号，并创建应用获取到 shareSDK 的 Appkey。申请教程参考[mob论坛技术贴](http://bbs.mob.com/forum.php?mod=viewthread&tid=8212&extra=page%3D1)。

**本模块封装了两套分享方案：**

方案一，通过调用 share 接口弹出分享平台列表菜单，供用户选择点击分享；

方案二，开发者自定义分享平台列表，通过调用 shareTo 接口，达到分享到某平台的目的。

**使用此模块之前需先配置  [config.xml](/APICloud/技术专题/app-config-manual)、key.xml 文件，key.xml 文件里配置了哪些平台，则弹出的分享菜单列表里就显示哪些平台。配置完毕，需通过云端编译生效。**

**[config.xml](/APICloud/技术专题/app-config-manual) 配置详解：**

- 名称：mobShare
- 参数：urlScheme、apiKey、apiSecret
- 配置示例:

```xml
  <feature name="mobShare">
    <param name="android_api_key" value="*******"/>
    <param name="android_api_secret" value="*******"/>
    <param name="ios_api_key" value="*******"/>
    <param name="ios_api_secret" value="*******"/>
    <param name="urlScheme" value="wxd0d84bbf23b4a0e4"/>
    <param name="urlScheme" value="tencent1105051647"/>
	<param name="urlScheme" value="QQ41DDBFFF"/>
    <param name="urlScheme" value="wb1132217156"/>
    <param name="urlScheme" value="fb*******"/>
    <param name="KAKAO_APP_KEY" value="48d3f524e4a636b08d81b3ceb50f1003"/>
    .
    .
    .
  </feature>
```

- 字段描述:
    
    **apiKey**：（必须配置）从 mob 平台选择社会化分享 shareSDK 创建应用后，申请的 app Key

    **apiSecret**：（必须配置）从 mob 平台选择社会化分享 shareSDK 创建应用后，申请的 app appSecret
    
    **urlScheme**：（必须配置）用于实现应用间跳转及数据交换，本应用可以启动第三方分享平台客户端，也可以从第三方分享平台客户端跳回本应用。urlScheme 的 value 值是从第三方分享平台获取。若同时支持多个平台，则要配置多个 urlScheme。以下是各个平台配置规范：
    - QQ：要填两个URL scheme: 一个是tencent + appId ; 一个是 QQ + （appId 转换成的十六进制）
    - 微信：是从微信开放平台获取的 appid，如：wxd0d84bbf23b4a0e4
    - 新浪微博：从新浪微博开放平台获取到的 App Key 拼接前缀 wb 而成的，如：wb1132217156
    - Facebook：设置格式为fb+AppID

   **KAKAO_APP_KEY**：（iOS可选配置）从kaKao平台申请的 app Key，若iOS平台需要使用kaKaoTalk、kaKaoStory平台进行分享，必须添加此字段

**key.xml 配置详解：**

`key.xml` 文件需要放在 `widget://res` 文件目录下，格式如下：

```js
	<?xml version="1.0" encoding="UTF-8" ?>
	<security>
	<item name="mobShare_sinaWb_apiKey" value="568898243"/>
	<item name="mobShare_sinaWb_apiSecret" value="38a4f8204cc784f81f9f0daaf31e02e3"/>
	<item name="mobShare_sinaWb_registUrl" value="http://www.apicloud.com"/>
	
	<item name="mobShare_wxSession_apiKey" value="wx4868b35061f87885"/>
	<item name="mobShare_wxSession_apiSecret" value="64020361b8ec4c99936c0e3999a9f249"/>

	<item name="mobShare_mail_apiKey" value="show"/>
	<item name="mobShare_sms_apiKey" value="show"/>
	<item name="其它服务需加密的参数配置" value="***"/>
	.
	.
	.
	</security> 
```

- 字段描述: 

    **mobShare_sinaWb_apiKey**：从新浪微博开放平台获取的 App Key
    **mobShare_sinaWb_apiSecret**：从新浪微博开放平台获取的 App  secret
    **mobShare_sinaWb_registUrl**：在新浪微博开放平台创建应用时（应用信息 -> 高级信息 -> 授权设置）自定义填写的回调 url 
    
    **mobShare_wxSession_apiKey**：从微信开放平台获取的 App Key
    **mobShare_wxSession_apiSecret**：从微信开放平台获取的 App secret
    
    **mobShare_mail_apiKey**：固定值为：show，若添加此此字段则分享平台列表菜单显示该按钮

    **mobShare_sms_apiKey**：固定值为：show，若添加此此字段则分享平台列表菜单显示该按钮
    
    以上字段实际分为三类：apiKey、apiSecret 和 registUrl，分别代表你注册申请当前平台时获取的 App Key、App Secret 和 RedirectURL。由于涉及平台众多，各个平台不一定都同时需要这三类字段，请开发者根据平台具体需要进行增加（如邮件、短信不需要这三类字段，只需在 apiKey 类字段使用上述给出的固定值 show 即可）。
   各个平台添加字段时只需替换上述name字段两个下划线之间的名称即可。以下是各个平台命名规范简写：

```js
        alipay: 支付宝好友
        douBan: 豆瓣
        flickr: Flickr
      facebook: Facebook
    googlePlus: Google+
     instagram: Instagram
        kaiXin: 开兴网
     kaKaoTalk: KaKao Talk
    kaKaoStory: KaKao Story
          line: Line
      linkedIn: LinkedIn
          mail: 邮件
     pinterest: Pinterest
        pocket: Pocket
            qq: QQ平台
         qZone: QQ空间
        renRen: 人人网
        sinaWb: 新浪微博
           sms: 短信
     tencentWb: 腾讯微博
        tumblr: Tumblr
       twitter: Twitter
      whatsApp: WhatsApp 
         wxFav: 微信收藏
     wxSession: 微信好友
    wxTimeline: 微信朋友圈
    youDaoNote: 有道云笔记
      yinXiang: 印象笔记
```
    
<div id="m1"></div>
#**share**

开始分享

share({params}, callback(ret, err))


##params

title:

- 类型：字符串
- 描述：（可选项）要分享的文本标题


titleUrl:
- 类型：字符串
- 描述：要分享的标题的url，**在 Android 平台上，如果是分享到 qq 或 qq空间，该参数不能缺省。IOS 忽略本参数**

text:

- 类型：字符串
- 描述：（可选项）要分享的文本信息

imgPaths：

- 类型：数组 （ android 不支持widget路径 ）
- 描述：（可选项）要分享的图片地址集合，传入参数可以为单张图片信息，也可以为多张图片信息，要求本地路径 (widget://、fs://、http://)，除腾讯微博外，其他平台只支持单张图片的分享，默认分享数组的第一张图片。**新浪微博分享网络图片需要申请高级权限**。

url:

- 类型：字符串
- 描述：（可选项）要分享网页路径/应用路径



##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:true   //布尔类型；操作成功状态值 true|false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code:       //数字类型；分享错误码，取值范围及其信息如下：
                //0: (分享失败)
                //1: (用户已取消)
}
```

##示例代码

```js
var mobShare = api.require('mobShare');
mobShare.share({
    title:'北京新鲜事',
    text: '这里是测试的内容',
    imgPaths:['widget://res/slide1.jpg', 'widget://res/slide2.jpg'],
    url: 'http://www.apicloud.com',
},function(ret,err){
    if (ret.status) {
		api.alert({msg:JSON.stringify(ret)});
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>
#**shareTo**

分享到指定平台

shareTo({params}, callback(ret, err))


##params

target:

- 类型：字符串
- 描述：（可选项）要分享到平台的名字，取值范围如下：
	- alipay: 支付宝好友
	- douBan: 豆瓣
	- flickr: Flickr
	- facebook: Facebook
	- googlePlus: Google+
	- instagram: Instagram
	- kaiXin: 开兴网
	- kaKaoTalk: KaKao Talk
	- kaKaoStory: KaKao Story
	- line: Line
	- linkedIn: LinkedIn
	- mail: 邮件
	- pinterest: Pinterest
	- pocket: Pocket
	- qq: QQ平台
	- qZone: QQ空间
	- renRen: 人人网
	- sinaWb: 新浪微博
	- sms: 短信
	- tencentWb: 腾讯微博
	- tumblr: Tumblr
	- twitter: Twitter
	- whatsApp: WhatsApp 
	- wxFav: 微信收藏
	- wxSession: 微信好友
	- wxTimeline: 微信朋友圈
	- youDaoNote: 有道云笔记
	- yinXiang: 印象笔记

title:

- 类型：字符串
- 描述：（可选项）要分享的文本标题

titleUrl:
- 类型：字符串
- 描述：要分享的标题的url，**在 Android 平台上，如果是分享到 qq 或 qq空间，该参数不能缺省。IOS 忽略本参数**

text:

- 类型：字符串
- 描述：（可选项）要分享的文本信息

imgPaths：

- 类型：数组 （ android 不支持widget路径 ）
- 描述：（可选项）要分享的图片地址集合，传入参数可以为单张图片信息，也可以为多张图片信息，要求本地路径（widget://、fs://、http://），除腾讯微博外，其他平台只支持单张图片的分享，默认分享数组的第一张图片。**新浪微博分享网络图片需要申请高级权限**。


url:

- 类型：字符串
- 描述：（可选项）要分享网页路径/应用路径



##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:true   //布尔类型；操作成功状态值 true|false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code:       //数字类型；分享错误码，取值范围及其信息如下：
                //0: (分享失败)
                //1: (用户已取消)
}
```

##示例代码

```js
var mobShare = api.require('mobShare');
mobShare.shareTo({
    target: 'qq',
    title:'北京新鲜事',
    text: '这里是测试的内容',
    imgPaths:['widget://res/slide1.jpg'],
    url: 'http://www.apicloud.com',
},function(ret,err){
    if (ret.status) {
		api.alert({msg:JSON.stringify(ret)});
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
