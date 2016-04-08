/*
Title: 微信开放平台接入
Description: 微信开放平台接入
Sort: 11
*/

开发者在使用APICloud提供的来自第三方开放平台-微信开放平台的相关模块时，需要开发者自行到微信开放平台申请相应的appId（urlScheme），并将该appId以feature的形式配置到您项目的config文件中。

该appId的申请与您应用的创建过程有关，具体流程请参考如下介绍。

##申请步骤

- 登录微信开放平台账号

访问微信开放平台，访问地址：https://open.weixin.qq.com

![图片说明](/img/docImage/50.jpg)

- 进入管理中心，若您未登录账号，微信开放平台将要求您登录：

![图片说明](/img/docImage/51.png) 

- 完成登录即可，进入管理中心：

![图片说明](/img/docImage/52.png) 

- 点击创建移动应用，进入应用基本信息填写界面：

![图片说明](/img/docImage/53.png)  

- 填写完毕后下一步：

![图片说明](/img/docImage/54.jpg) 

- 进入填写平台信息界面：

![图片说明](/img/docImage/55.png) 

- 勾选IOS应用：
 
![图片说明](/img/docImage/56.png) 

- 勾选Android应用：

![图片说明](/img/docImage/57.png)  

#**必填信息获取：**

**获取应用包名：**

Android平台的包名获取方式：

- 登录到[APICloud云端](http://www.apicloud.com/login)，如下图：
 
![图片说明](/img/docImage/58.jpg) 

- 登录成功后进入应用概览界面，如下图：
 
![图片说明](/img/docImage/59.png)  

- 获取包名。在应用概览区域点击应用简介下方的小箭头，在下拉的区域中即可查看到本应用的包名、appKey、申请百度apiKey所需的SHA1安全码码值（百度key）等信息。如下图红色圈区域：

![图片说明](/img/docImage/60.png) 

将该包名填入"勾选Android应用"一步中的应用包名即可

**获取应用签名：**

- 进入微信开放平台资源中心界面，并点击展开资源下载下拉菜单：

![图片说明](/img/docImage/61.jpg) 

- 选择Android资源下载：

![图片说明](/img/docImage/62.png) 

- 在右侧的展开预览界面中选择下载“签名生成工具”。您将会下载得到一个应用安装包（apk文件）：
 
![图片说明](/img/docImage/63.jpg) 

9.7、该应用将用于获取手机上已安装应用的签名。
将该apk安装至您的Android手机中。```同时请确认该手机上已经安装了您需要获取签名信息的应用。```
该apk安装后如图：
 
![图片说明](/img/docImage/64.png) 

- 在输入框中输入,查看包名中获取的应用包名，如图：

![图片说明](/img/docImage/65.jpg) 
 
- 点击Get Signature按钮即可，该工具将自动运算出此包名对应应用的签名，如下图中绿色字符：

![图片说明](/img/docImage/66.jpg) 

将该绿色字符串一次输入,勾选Android应用的应用签名框中即可。

- 如过输入的包名对应的应用在本设备上不存在，则会出现类似以下情况：

![图片说明](/img/docImage/67.jpg) 
 
所以请确保您的手机上一定安装了相应的应用。

- 输入完相关信息后，点击“提交审核”即可：
 
![图片说明](/img/docImage/68.png) 
 
![图片说明](/img/docImage/69.png) 

审核通过后即可在应用详情界面查看到你需要的appId。

