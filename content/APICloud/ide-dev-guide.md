/*
Title: 工具：APICloud Studio
Description: APICloud Studio使用说明
Sort: 4
*/
<style type="text/css">
    #studioDownload a{
        display: inline-block; 
        background-color: #609be3; 
        border: 1px solid #afcdf1; 
        color: #fff; border-radius: 0;
        padding: 10px 40px; font-size: 14px;
        margin-right: 20px;
        border-radius: 0;
    }
</style>

<h2 style="margin-top:30px;">APICloud Studio使用说明</h2>
[总体介绍](#a1)

[启动APICloud Studio](#a2)

[APICloud Studio功能介绍](#a3)

- [打开向导页面](#a4)
- [创建一个移动应用](#a5)
- [同步本地应用到云端资源库](#a6)
- [从云端资源库下载应用到本地](#a7)
- [使用云端svn同步功能](#a8)
- [真机同步测试](#a9)
- [使用自定义Loader](#a16)
- [本地打包](#a11)
- [云端编译](#a12)
- [输出手机调试日志](#a13)
- [在线文档](#a14)
- [APICloud 代码提示以及自动补全](#a15)

<div id="studioDownload">
    <a target="_blank" href="https://gitcafe.com/APICloud" class="btn btn-primary btn-lg last-url win">Windows版下载</a>
    <a target="_blank" href="https://gitcafe.com/APICloud" class="btn btn-primary btn-lg last-url mac">Mac版下载</a>
</div>

<div id="a1"></div>
#**总体介绍**

##概述

APICloud Studio是基于Eclipse和Aptana Studio3进行扩展，集成了包括：应用管理、模版框架、云端同步、代码管理、代码提示、本地打包、真机同步、AppLoader管理，编译自定义AppLoader等功能。企业和开发者也可以在此开源代码的基础上定制自己的APICloud开发工具。 开源地址：https://github.com/apicloudcom/APICloud-Studio

##名词解释 

* **APICloud Studio**：由APICloud提供的移动应用集成开发环境。

* **本地打包**：APICloud Studio把APICloud引擎和开发人员创建的APICloud移动应用结合在一起打成Android(apk)或者iOS(ipa)安装包。

* **真机同步**：APICloud Studio为开发者提供了Android和iOS平台的真机调试器，将本地开发的应用代码放入真机调试器的指定目录，即可实现真机模拟、调试，与最终完成的原生应用功能、体验保持统一。

* **自定义Loader**：添加了自定义模块或第三方模块的AppLoader，不需要云端编译即可用于真机同步调试。

<div id="a2"></div>
#**启动APICloud Studio**

APICloud Studio是绿色版，不用修改注册表。下载后解压缩，运行可执行文件即可。

![图片说明](/img/docImage/170.jpg)

<div id="a3"></div>
#**APICloud Studio功能介绍**

<div id="a4"></div>
##打开向导页面

操作流程

- 首先运行APICloud Studio。
- 在APICloud Studio中点击下图的功能按钮，便可以打开向导页面。

![图片说明](/img/docImage/171.jpg)
 
<div id="a5"></div>
##创建一个移动应用

**说明**

在APICloud中一套应用代码可以对应生成 Android 和 iOS 两个平台的应用。并且APICloud Studio中的操作都是以移动应用为单位进行的。

**操作流程**

创建一个应用有3个入口。

- 在向导页面中“创建app项目”中创建移动应用。如下图。

![图片说明](/img/docImage/173.png)
 
- 在我的app项目视图中，右键鼠标选择，新建—创建APICloud项目 如下图。

![图片说明](/img/docImage/176.jpg)
 
- 在文件菜单栏中选择，文件--新建—创建APICloud项目

![图片说明](/img/docImage/175.png)

在打开的向导中输入应用名称（必需）和应用说明（非必需），也可以选择需要的应用框架（或空白应用），然后点击完成。即可创建一个APICloud应用。

![图片说明](/img/docImage/177.jpg)

<div id="a6"></div>
##同步本地应用到云端资源库

**说明**

APICloud Studio开发工具提供了云端上传应用的功能。开发者创建的应用会和云端资源库建立连接。并且网站也通过云端资源库和APICloud Studio共享应用同步开发。

**操作流程**

- 首先选择一个需要同步到云端资源库的APICloud应用。
- 在APICloud应用上右键，选择云端同步—提交。
 
![图片说明](/img/docImage/178.png)

- 在打开的提交界面输入提交信息后点击完成。即可提交应用到云端资源库中。
 
![图片说明](/img/docImage/179.jpg)

<div id="a7"></div>
##从云端资源库下载应用到本地

**说明**

APICloud Studio开发工具提供了云端下载应用的功能。开发者通过同步功能将APICloud应用上传到云端资源库以后，其他开发人员可以通过云端资源库再把最新的应用下载到本地APICloud Studio中。

**操作说明**

- 首先选择云端资源库视图。

![图片说明](/img/docImage/180.png)
 
- 找到你要下载的应用（可以先从云平台找到该应用的应用ID），右键选择检出为。如下图。

![图片说明](/img/docImage/181.png)
 
- 在检出向导中点击完成按钮即可。

![图片说明](/img/docImage/182.jpg)
 
<div id="a8"></div>
##使用云端svn同步功能

**说明**

云端svn同步功能可以刷新云端资源库中的应用，开发者如果在网站上修改过应用可以通过这个功能同步到本地。

**操作流程**

- 在APICloud Studio 云端资源库视图下。

- 点击“同步SVN”按钮。即可发起同步远端资源库的功能刷新云端资源库。如下图所示。

![图片说明](/img/docImage/183.jpg)

<div id="a9"></div>
##真机同步测试

**说明**

真机同步测试功能是APICloud Studio为开发者提供的一个快速将应用运行在手机上的功能。这样可以方便开发人员测试，并且提高开发效率。（需要手机连接电脑，并且iPhone手机需要下载iTunes，Android手机需要下载豌豆荚、91等手机助手）

**操作说明**

真机同步测试有2个入口：

1， 首先在我的APP项目视图中选择一个需要真机测试的应用，然后在应用上右键选择一键真机同步测试。
![图片说明](/img/docImage/184.jpg)


2， 在APICloud Studio 中找到按钮 ，点击后在弹出的窗口中选择需要真机测试的应用。运行即可。


当应用同步到手机后， 点击完成关闭同步进度向导。

![图片说明](/img/docImage/185.jpg)

- 在手机中测试应用。

<div id="a16"></div>
##使用自定义Loader

* 编译自定义Loader

右键点击应用项目文件夹 -> 选择“编译自定义Loader” -> 等待编译完成，编译之前请确保云端已添加需要的模块，更详细可参考[自定义loader说明](/APICloud/技术专题/Custom_Loader)。

![图片说明](/img/docImage/compile-cust-loader.jpg)

![图片说明](/img/docImage/compiling-loader.jpg)

![图片说明](/img/docImage/compile-succ.jpg)

* 删除自定义Loader

右键点击应用项目文件夹 -> 选择“删除自定义Loader”，删除以后即可使用官方发布的 AppLoader。

![图片说明](/img/docImage/del-cust-loader.jpg)

* 真机同步测试

功能使用参考以上[真机同步测试](#a9)章节

<div id="a11"></div>
##本地打包

**说明**

本地打包是APICloud Studio把APICloud核心引擎和开发人员创建的APICloud移动应用结合在一起打成包。达到快速测试的效果。（IOS的测试包是不能在正版系统中安装的，只能安装在越狱手机中）如果需要打正式版本的安装包，请参考[云编译说明](#a12)

**操作流程**

本地打包有2个入口：

- 在我的APP项目视图中选择一个需要打包的应用，然后在应用上右键选择生成快速安装包。

![图片说明](/img/docImage/188.jpg)
 
- 或者在APICloud Studio 中找到按钮 ，点击后在弹出的窗口中选择需要打包的应用。点击运行。

- 在弹出的窗口中选择需要生成测试包的类型(ios/android)，然后点击完成即可生成对应的快速安装包。

![图片说明](/img/docImage/189.jpg)
 
- 生成测试安装包后，APICloud Studio会自动帮您打开安装包所在文件夹。

<div id="a12"></div>
##云端编译

**说明**

如果需要把应用打成正式版的安装包，需要在云端进行打包。

**操作说明**

- 在APICloud Studio 中找到按钮 ，点击后APICloud Studio会帮您连接到云端编译页面。

![图片说明](/img/docImage/190.png)
 
- 云端编译界面

![图片说明](/img/docImage/191.png)
 
<div id="a13"></div>
##输出手机调试日志

**说明**

APICloud Studio通过真机调试可以连接Android手机的日志，用户可以使用console.log输出日志以调试程序，而当js报错时，错误日志也会输出到APICloud Studio的控制台中，方便开发人员进行错误分析，bug调试。

**操作流程**

- 首先通过一键真机同步测试功能将要调试的应用同步到Android手机中的
- 开启APICloud Studio的日志输出功能按钮

![图片说明](/img/docImage/192.jpg)
 
- APICloud Studio控制台会提示开启监听…

![图片说明](/img/docImage/193.png)
 
- 如果开发人员自己输出了日志，或者js报错就会出现在APICloud Studio控制台中。（如何定义输出日志请参考文档）

<div id="a14"></div>
##在线文档

**说明**

APICloud提供了在线开发文档，通过阅读开发文档可以是开发人员更快上手开发应用。

**操作流程**

在APICloud Studio中点击按钮，即可进入APICloud 在线文档页面，也可以访问 http://docs.apicloud.com/ 获取。

![图片说明](/img/docImage/194.jpg)

<div id="a15"></div>
##APICloud 代码提示以及自动补全

**说明**

APICloud 中提供了自己定义的api对象以及大量的模块（如db、fs等）。通过这些api可以大大减少用户的开发，并且开发人员只需要掌握html5和js技术就可以发开出和iOS/Android相媲美的本地应用，同时，APICloud Studio也提供了这些api的代码提示功能。



**Api对象**

- 开发人员需要先熟悉APICloud提供的api文档。
- 在APICloud Studio的编辑器中，找到js编辑区域。
- 输入api对象后在输入一个”.”就会触发APICloud Studio的代码提示功能。
- 其中代码提示栏分为2部分：左侧是提示的属性或者方法名（属性：P，方法：F）右侧是该提示的内容，包括：描述、参数、回调函数、可用性等说明。

![图片说明](/img/docImage/195.jpg)
 
- 当选择一个提示后APICloud Studio会自动帮您补全代码。

![图片说明](/img/docImage/196.jpg)

**Api函数param参数**

- 选择一个api函数中的param区域。

![图片说明](/img/docImage/197.png)
 
- 使用组合键"Alt"+"/"，APICloud Studio会根据这个函数提示出相应的param参数。

![图片说明](/img/docImage/198.png)

- 选择一个参数后APICloud Studio会自动帮您补全。

![图片说明](/img/docImage/199.png)
 
**模块对象**

- APICloud 中模块是基于api调用的。
- 如果需要使用模块需要先利用api的require函数调用该模块。如下图操作

![图片说明](/img/docImage/200.jpg)
 
- 当选择了需要的函数后，APICloud Studio会自动帮您补全代码。
 
![图片说明](/img/docImage/201.png)