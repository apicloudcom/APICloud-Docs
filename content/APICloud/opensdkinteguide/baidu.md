/*
Title: 百度开放平台接入
Description: 百度开放API配置指南
Sort: 11
*/

开发者在使用APICloud提供的来自第三方开放平台-百度开放平台的相关模块时，如baiduMap、baiduLocation等，需要开发者自行到百度开放平台申请相应的apiKey，并将该apiKey以feature的形式配置到您项目的config文件中。同一个项目中如果使用了多个来自百度开放平台的模块，可以使用同一个apiKey

该apiKey的申请与您应用的创建过程有关，具体流程请参考如下介绍。

##申请步骤

- 登录百度账号

访问API控制台页面，若您未登录百度账号，将会进入百度账号登录页面，
登录地址：https://passport.baidu.com/v2/?login
如下图：

![图片说明](/img/docImage/94.png) 
 
- 登陆API控制台

登录会跳转到API控制台服务（http://lbsyun.baidu.com/apiconsole/key），
具体如下图：

![图片说明](/img/docImage/95.png) 

- 创建应用

点击"创建应用"，系统将为您弹出创建AK页面，输入应用名称，将应用类型改为：“for mobile”：
 
![图片说明](/img/docImage/96.png)
 
![图片说明](/img/docImage/97.png)

- 配置应用<div id="100"></div>

在应用类型选为“for mobile”后，需要配置应用的安全码，如下图所示：

![图片说明](/img/docImage/98.jpg) 

- 获取安全码

百度开放平台的安全码获取需要区分移动平台，意味着如果你的同一个应用需要同时支持IOS和Android平台，那么，您必须为这两个平台单独申请apiKey，即同一个应用申请两个apiKey，并将这两个apiKey同时配置在config文件中。 

##Android平台：

Android平台安全码的组成规则为：Android签名证书的sha1值 + “;” + packagename(即:数字签名 + 分号 + 包名)，例如：
BB:0D:AC:74:D3:21:E1:43:67:71:9B:62:91:AF:A1:66:6E:44:5D:75;com.apicloud.demo
Android平台的安全码及包名获取方式：

（1）、登录到APICloud云端（http://www.apicloud.com/login），如下图：
 
![图片说明](/img/docImage/99.png)

（2）、登录成功后进入应用概览界面，如下图：

![图片说明](/img/docImage/100.png)
 
（3）、获取包名以及SHA1码。在应用概览区域点击应用简介下方的小箭头，在下拉的区域中即可查看到本应用的包名、appKey、申请百度apiKey所需的SHA1安全码码值（百度key）等信息。如下图红色圈区域：
 
![图片说明](/img/docImage/101.png)

将该包名以及SHA1码拷出，组合后输入[配置应用](#100)界面中的安全码输入框中，点击确认，片刻即可完成应用的配置工作，您将会得到一个创建的Key，将该Key拷贝并配置到config文件中即可，如下图：
 
![图片说明](/img/docImage/102.png)

配置config文件中android_api_key字段：

![图片说明](/img/docImage/103.png)

##IOS平台：

IOS平台的安全码只需要该应用的Bundle Identifier，相当于Android平台的包名，登录APICloud 控制台后，在应用概览界面即可获取，获取包名。
然后重复[配置应用](#100)的步骤，即可配置成功，生成IOS平台对应的apiKey。
拷贝后配置config文件中ios_api_key字段即可：
 
![图片说明](/img/docImage/104.png)

配置完毕后即可，APICloud应用会在您使用到该模块时，自动取得该apiKey，并在相应的模块中使用。
