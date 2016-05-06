/*
Title: 创建第一个应用
Sort: 2
*/

[应用简介](#1)

[准备工作](#2)

[创建应用及代码管理](#3)

[应用包结构](#4)

[config.xml 配置文件](#5)

[前端开发框架](#6)

[端API调用](#7)

[真机同步调试](#8)

[本地打包](#10)

[云端编译](#11)

[Sample Code](#12)

#**应用简介**<div id="1"></div>
    
本文档会逐步引导您，快速开发一个简单应用。应用将包含简单的文件读写功能，所有步骤涉及APICloud Studio的使用、APICloud平台使用、端API调用等各方面知识介绍。

#**一、准备工作**<div id="2"></div>

[下载](http://apicloud.com/dev)并安装APICloud Studio开发环境，APICloud Studio当前支持Windows，Mac系统。

#**二、创建应用**<div id="3"></div>

APICloud提供了两种应用创建方式，方便开发者在云端和APICloud Studio中创建应用。

##云端创建应用：

1) 注册并登录APICloud系统：http://www.apicloud.com/console 点击左上角“创建应用”，
如图：选择“Native”，填写“名称”及“说明”，应用创建完成。

![图片说明](/img/docImage/120.jpg)

应用概览页 http://www.apicloud.com/appoverview 可以看到应用相关信息，留意一下应用ID，APICloud Studio会用到。

![图片说明](/img/docImage/121.png)

2) 用以上注册的APICloud账号登录APICloud Studio

![图片说明](/img/docImage/122.png) 

3) 登录后，左侧选择“云端资源库”，根据APICloud 创建的应用ID 选择SVN 项目。

![图片说明](/img/docImage/124.jpg) 

4) 选择项目，右键“检出为”

![图片说明](/img/docImage/125.png)  

5) 点击“完成”，应用创建完成。

![图片说明](/img/docImage/126.png)  

##APICloud Studio中创建应用：

1) 登录APICloud Studio，没有账号点击“注册账号”

![图片说明](/img/docImage/127.png)

2) 顶部菜单选择 “文件” → “新建” → “创建APICloud项目”。

![图片说明](/img/docImage/128.jpg)  

3) 填写“应用名称”，“应用说明”，点击完成，即完成创建。

![图片说明](/img/docImage/129.png)

4) 同步本地应用到云端资源库

开发者在APICloud Studio创建的应用会和云端资源库建立连接。项目代码改动后，可以使用APICloud Studio的代码提交功能提交代码到云端资源库。

**操作流程**

- 首先选择一个需要同步到云端资源库的项目。
- 在项目上右键，选择云端同步—提交。
 
![图片说明](/img/docImage/178.png)

- 在打开的提交界面输入提交信息后点击完成。即可提交项目代码到云端资源库中。

![图片说明](/img/docImage/179.jpg)

5）其他上传代码的方式

 第一种方式： 也可在网站控制台-端开发-代码界面上传整个项目的zip格式压缩包。（项目的根目录名要改为 widget。即压缩后为widget.zip。） 
 
![图片说明](/img/docImage/commitcode1.png)

 第二种方式： 使用TortoiseSVN（俗称“小乌龟”）等任何SVN工具提交代码。

 ![图片说明](/img/docImage/commitcode2.png)

  在电脑上新建一个文件夹，命名为您的项目名。在文件夹中右键，选择 SVN Checkout。出现如下界面：

  ![图片说明](/img/docImage/commitcode3.png)

 填入网站的项目地址，检出到的本地地址。点击ok即可。（前提是已经登录过APICloud Studio, 否则需要输入您在APICloud注册的用户名，及点击获取分支密码获得的密码。）




  
#**三、应用包结构**<div id="4"></div>

![图片说明](/img/docImage/130.png)

“config.xml”和 “index.html” 必须包含，其它均为可选。“config.xml”是配置文件，“index.html”是启动页面，“icon”为图标文件目录，“launch”为启动图片目录（更多介绍详见[Widget包结构说明](/APICloud/技术专题/widget-package-structure-manual)文档）。

#**四、config.xml 配置文件**<div id="5"></div>

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

- “id”: 必填，应用ID，由云服务器自动分配。它是该应用的唯一标识。
- “version”：必填，应用的版本号。
- “name”：必填，应用名称。
- “description”：可选，应用简单描述信息。
- “content”：必填，应用运行的起始页。
- “permission”：必填，权限配置。
（详细介绍见[应用配置指南](/APICloud/技术专题/app-config-manual)文档）

#**五、前端开发框架**<div id="6"></div>

我们提供了核心的api.css和api.js前端框架，可与第三方前端框架混用，也可不用我们的框架；api.css 处理不同平台浏览器的默认样式，api.js 提供最基础的 JavaScript 方法，所有方法在 window.$api 对象下。

（详细文档见[前端框架开发指南](/APICloud/技术专题/framework-dev-guide)文档）

#**六、端API调用**<div id="7"></div>
1. 核心模块在 window.api 对象下，默认提供该模块，不需要单独引用。
1. 扩展模块在相应的模块对象下（例如：文件系统模块在fs对象下），需要require引入（var fs = api.require('fs');）。API核心模块已经覆盖一般应用的绝大部分功能。
1. 模块中所有方法均遵循 api.functionName(params, callback)格式，params为JSON格式，callback是Function类型，callback返回两个参数，均为JSON格式：callback(ret, err)，ret处理成功信息，err处理错误信息。
1. apiready 方法在所有核心API模块准备完毕时执行。

（详细介绍见[api文档](http://docs.apicloud.com/%E7%AB%AFAPI/api)）

#**七、真机同步调试**<div id="8"></div>

打开APICloud Studio，用数据线连接移动设备，当前项目下，右键选择“一键真机同步测试”
 
![图片说明](/img/docImage/131.png)

![图片说明](/img/docImage/134.png)

等待同步完成，项目代码被拷贝到移动设备指定目录，移动设备上的apploader自动启动，即可实现真机同步调试。

点击顶部的“启动日志”按钮，当真机调试的应用有JavaScript错误时，APICloud Studio的控制台会有日志输出。
 
![图片说明](/img/docImage/135.jpg)

![图片说明](/img/docImage/136.png) 


#**八、本地打包**<div id="10"></div>

选择应用项目，右键选择“生成快速测试包”，填写“应用名称”，选择“生成平台”，点击“打包”，即可生成测试安装包。（更多详尽功能参见[APICloud Studio使用指南](/APICloud/ide-dev-guide)）

#**九、云端编译**<div id="11"></div>

登录APICloud 系统

- 端设置 http://www.apicloud.com/CADConfig
可以上传启动页面和应用图标

![图片说明](/img/docImage/138.png) 

- 证书 http://www.apicloud.com/certificate
正式版需要上传相应平台的证书，测试版不需要
 
![图片说明](/img/docImage/140.png) 

- 代码 http://www.apicloud.com/code
可以把应用代码上传至APICloud服务器
 
![图片说明](/img/docImage/139.png) 

- 模块 http://www.apicloud.com/module
选择应用需要的模块，添加进去

![图片说明](/img/docImage/141.png) 

- 云编译 http://www.apicloud.com/package
选择“云编译”菜单，选择相应平台（Android 或 iOS），选择编译类型（测试版或正式版），点击“云编译”按钮，耐心等待编译完成

![图片说明](/img/docImage/142.png)  

- 下载安装
扫描二维码可以下载安装应用至移动设备

![图片说明](/img/docImage/143.png)  

#**十、Sample Code**<div id="12"></div>

参照我们的[示例代码](http://resource.apicloud.com/samples/Samples.zip)快速上手开发第一个应用吧，Happy Coding!

