/*
Title: 百度开放平台接入
Description: 百度开放API配置指南
Sort: 11
*/

开发者在使用 APICloud 百度地图开放平台的相关模块时，如 baiduMap、baiduLocation、bMap 等，需要开发者自行到百度开放平台申请相应的 apiKey，并将该 apiKey 以feature 的形式配置到您项目的 config 文件中。同一个项目中如果使用了多个来自百度地图开放平台的模块，可以共用一个 apiKey

该 apiKey 的申请与您应用的创建过程有关，具体流程请参考如下介绍。

##申请步骤

- 登录百度地图开发者账号

访问百度地图 API 控制台页面，若您未登录百度账号，将会进入[百度地图开发者账号登录](https://passport.baidu.com/v2/?login&fr=old&u=http://lbsyun.baidu.com/)页面，如下图：

![图片说明](/img/docImage/bMapGuide/login.png) 
 
- 进入控制台

在百度地图开放平台首页点击申请密钥按钮进入控制台，如下图：

![图片说明](/img/docImage/bMapGuide/center.png) 

- 创建应用

百度开放平台的安全码获取需要区分移动平台，意味着如果你的同一个应用需要同时支持 iOS 和 Android 平台，那么，您必须为这两个平台单独申请 apiKey，即同一个应用申请两个 apiKey，并将这两个 apiKey 同时配置在 config 文件中。 

点击"创建应用"，系统将为您弹出创建 AK（APICloud平台上称之为apiKey） 页面，输入应用名称，将应用类型改为 iOS 或 android：
 
![图片说明](/img/docImage/bMapGuide/create.png)
 
![图片说明](/img/docImage/bMapGuide/select.png)

- 配置应用<div id="100"></div>

***Android平台：***

在应用类型选为 Android 后，需要配置应用的相应参数，如下图所示：

![图片说明](/img/docImage/bMapGuide/configAndroid.png) 

Android平台安全码的组成规则为：Android签名证书的sha1值 + “;” + packagename(即:数字签名 + 分号 + 包名)，例如：
BB:0D:AC:74:D3:21:E1:43:67:71:9B:62:91:AF:A1:66:6E:44:5D:75;com.apicloud.demo
Android平台的安全码及包名获取方式：

（1）、登陆 APICloud [开发者中心](https://www.apicloud.com/signin)，如下图：
 
![图片说明](/img/docImage/bMapGuide/apicloudLogin.png)

（2）、登录成功后进入应用概览界面，如下图：

![图片说明](/img/docImage/bMapGuide/overview.png)
 
（3）、获取包名以及SHA1码。在应用概览区域点击应用简介下方的小箭头，在下拉的区域中即可查看到本应用的包名、appKey、申请百度 apiKey 所需的 SHA1 安全码码值（百度key）等信息。如下图红色圈区域：
 
![图片说明](/img/docImage/bMapGuide/androidsha.png)

将该包名以及SHA1码拷出，输入百度地图创建应用界面中，点击提交，片刻即可完成应用的配置工作，您将会得到一个创建的 AK，将该 Key 拷贝并配置到 config 文件中 android_api_key 字段即可，如下图：

![图片说明](/img/docImage/bMapGruide/configak.png)

***iOS平台：***

iOS 平台的安全码只需要该应用的 Bundle Identifier（APICloud平台称之为包名） 即可，登录APICloud 控制台后，在应用概览界面即可获取。
然后重复[配置应用](#100)的步骤，即可配置成功，并生成 IOS 平台对应的 apiKey。
拷贝后配置 config 文件中 ios_api_key 字段即可：
 
![图片说明](/img/docImage/configak.png)

配置完毕后即可，APICloud应用会在您使用到该模块时，自动取得该apiKey，并在相应的模块中使用。
