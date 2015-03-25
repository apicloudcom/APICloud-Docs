/*
Title: 模块开发指南_iOS
Description: 模块开发指南_iOS
Sort: 4
*/



[第一章	SDK简介](#1)

[第二章	阅读对象](#2)

[第三章 	SDK功能说明](#3)

[第四章	开发前准备](#4)

[第五章	使用SDK开发Native模块](#5)

[第六章	Native模块开发Demo解释](#6)

[第七章	SDK开放API说明](#7)

[第八章	Native模块包结构说明](#8)

#**第一章SDK简介**<div id="1"></div>

为满足广大开发者自定义扩展Native module的需求，APICloud推出模块扩展SDK（以下简称SDK），提供给有一定iOS基础的开发者，通过简单的接口实现，轻松接入APICloud平台，快速开发扩展模块，自行实现对APICloud引擎能力的增强，提升App的质量及用户体验。

#**第二章阅读对象**<div id="2"></div>

本文档面向所有使用该SDK的iOS开发人员、测试人员、合作伙伴以及对此感兴趣的其他用户。阅读该文档要求用户熟悉iOS应用开发，并且对Html、CSS、Javascript有一定了解。APICloud引擎强调传输数据的简洁和统一性，因此选择轻量级的JSON作为Javascript和Native语言之间通讯的数据载体，所以要求开发者同时要熟悉Objective-C和Javascript中JSON格式数据的操作。

#**第三章SDK功能说明**<div id="3"></div>

##i.  框架设计

APICloud引擎通过系统Webkit浏览器，实现了HTML+CSS+Javascript开发语言和Objective-C/Java/C/C++等Native开发语言之间的桥接，极大的丰富和增强了标准Javascript的能力。令前端开发者通过JS即可调用移动设备的底层功能，如：电话、短信、定位、多媒体、跨域http请求等，并能将如百度地图、支付宝等第三方厂商的SDK很容易的集成到自己的App中来。

本SDK开放桥接机制，方便具有一定iOS基础的开发者自由开发定义Native扩展模块，丰富JS的能力，提升App的用户体验。
APICloud引擎框架桥接层设计如图（1）：

![图片说明](/img/docImage/144.png) 

##ii. 主要功能

本SDK 主要提供以下功能和接口

1.	映射一个UZModule子类的函数至Javascript对象的函数
2.	module.json文件的声明
3.	向window注入并执行一段Javascript

#**第四章开发前准备**<div id="4"></div>

**开发环境**
- Xcode5或更高版本
- Mac os x 10.7以上

**开发帮助参考**
- Javascript规范及入门：http://www.w3school.com.cn
- JSON数据在线Viewer：http://www.bejson.com/go.html?u=http://www.bejson.com/jsonview2/

#**第五章使用SDK开发Native模块**<div id="5"></div>

##i、添加SDK工程到Xcode

解压ModulesDevProject_iOS.zip至任意目录，打开UZApp工程。

##ii、开发设计Native模块

**新建用于绑定映射至JS对象的类**

创建一个继承于UZModule的类（以下以UZModuleDemo类为例，映射的JS对象为moduleDemo），并重写相关函数。在module.json中定义的方法需在该类中实现，如showAlert:。

##iii、模块方法的添加

**获取JS传入的参数**

APICloud引擎要求前端JS开发者必须使用JSON格式数据作为JS与Native之间交换数据的传参，APICloud引擎会对JS传入的参数进行解析并封装。前端JS使用模块之前需要require模块对象。
例如Html页面这样写：

![图片说明](/img/docImage/145.png) 
 
那么在UZModuleDemo中则可以这样获取JS传入的msg值：

![图片说明](/img/docImage/146.png) 
 
**将操作结果回调至JS**

APICloud引擎采用JS与Native之间异步机制架构，Native做完相关操作后，应该将操作结果通知给JS页面，或者通知页面本次操作成功与否，错误提示等。该回调过程由UZModule下的方法sendResultEventWithCallbackId: dataDict: errDict: doDelete:完成。如下图的代码实现了对“showAlert”结果的回调：

![图片说明](/img/docImage/147.png) 
 
注意：

回调接口最后一个参数的传入，如果在本对象生命周期内需要多次回调此接口则此参数传NO，否则APICloud引擎会在第一次callBack后将此通讯通道删除。而后在模块类的dispose方法里将此通道删除，如：[self deleteCallback:cbId];

**模块声明文件module.json的编写**

Native模块必须在module.json文件中声明类名称及其所映射的JS对象名称，以及方法等。如下图所示：

![图片说明](/img/docImage/148.png) 

字段解释：
name：定义该扩展模块所对应的JS对象名，类似于标准JS中的window、document、Math等对象。

class：定义该扩展模块对应被JS映射的Objective-C类名称。

##iv、往界面添加视图

**UIView类视图**

可在指定view上添加自定义的view，如下图：

![图片说明](/img/docImage/149.png) 
 
getViewByName:方法返回指定的view，默认为当前的主窗口。

**controller类视图**

UZModule提供属性controller，可通过该控制器对目标控制器进行push或者present操作。

##v、调用第三方应用模块的开发

和第三方应用通讯的模块开发需要遵循以下步骤：

- 模块类引入 UZAppDelegate.h头文件
- 在Info.plist文件里面配置好urlScheme，如tencent11055322
- 以之前的urlScheme为key，将要接收应用回调信息的对象添加到引擎队列里，当引擎收到第三方应用回调消息时会将消息分发给注册对象，如下图：

![图片说明](/img/docImage/150.png)

- 在模块类的dispose方法里从引擎队列里移除对象，不然对象不会被释放，如下图：

![图片说明](/img/docImage/151.png)
 
- 引擎会检测是否对象实现了handleOpenURL:方法，实现该方法来接收应用回调消息

![图片说明](/img/docImage/152.png)
 
##vi、模块内资源的使用

**模块自身资源**

模块内使用到的资源文件要放在res_模块名的文件夹里，如res_moduleDemo。注意要将此文件以引用的形式导入工程，如下图所示：

![图片说明](/img/docImage/153.png)
 
模块内访问资源时添加res_moduleDemo/的绝对路径，如

![图片说明](/img/docImage/154.png)
 
**引擎资源**

引擎资源有其自身的协议规范，分别是widget://、fs://、file://。当前端页面传过来一个协议路径，native开发调用工具类getPathWithUZSchemeURL得到资源的绝对路径，如下图：

![图片说明](/img/docImage/155.png)
 
##vii、导出Native模块包
创建一个静态库工程，添加你的代码，引入UZEngine文件夹下的头文件，编译生成静态库，然后将资源文件和静态库，以及module.json文件按照模块包规范导出成zip包，并提交至APICloud云打包服务器上。

静态库生成注意事项：

- 静态库工程Edit scheme ->Run->Build Configuration设置为Release模式，如下图：

![图片说明](/img/docImage/156.png)
 
- 版本适配最低为iOS 5.0，设置如下图：

![图片说明](/img/docImage/157.png)
 
- 选择必要的头文件导入工程，如下图：
 
![图片说明](/img/docImage/158.png)

#**第六章Native模块开发Demo解释**<div id="6"></div>

本SDK默认展示一个扩展模块demo。该demo展示如何扩展一个名为moduleDemo的JS对象，并将该对象映射至Objective-C类（UZModuleDemo）的过程，同时展示如何在html页面中通过JS调用该模块。

##i、UZApp

UZApp工程包含了必须的uzEngine库和三个头文件，一个简单的module，还包含了widget网页包，以及module配置文件module.json等。注：如果开发者自己创建的工程，需要在工程配置文件里面的Other Linker Flags项添加-ObjC。

##ii、module.json

module.json的内容格式为JSON数组字符串，可以对多个module进行配置，其中的每一项相当于一个模块包中的module.json。

#**第七章SDK开放API说明**<div id="7"></div>

本章节提供APICloud引擎所有开放接口的说明。

##i、类
本SDK提供三个开放类，分别为：UZModule、UZAppDelegate、UZAppUtils。

<table>
    <thead>
    <tr>
        <th width="50%">类</th>
        <th>描述</th>
    </tr>
    </thead>
    <tr>
        <td>UZModule</td>
        <td>所有扩展Native模块的基类，子类通过继承该类并声明相应函数，实现子类绑定映射至JS对象</td>
    </tr>
    <tr>
        <td>UZAppDelegate</td>
        <td>应用程序入口，Native开发者自己创建应用时，其AppDelegate需继承于该类</td>
    </tr>
    <tr>
        <td>UZAppUtils</td>
        <td>工具类，提供一些基础API</td>
</table>

UZModule类是模块开发扩展的基类，其初始化，清空内存以及回调方法如下表：

<table style="table-layout:fixed;">
    <thead>
    <tr>
        <th width="50%">方法</th>
        <th>描述</th>
    </tr>
    </thead>
    <tr>
        <td>- (id)initWithUZWebView:(UIWebView *)webView</td>
        <td>初始化方法，做一些初始化工作，比如给在module.json里面定义的属性赋初值等</td>
    </tr>
    <tr>
        <td>- (void)dispose</td>
        <td>引擎主动回调函数，当window或者frame关闭以及当前页面发生url变化时，引擎会主动回调该接口，开发者应该在此接口中清理当前模块占用的资源，如网络资源，内存资源等</td>
    </tr>
    <tr>
        <td>- (void)sendResultEventWithCallbackId:(NSInteger)cbId dataDict:(NSDictionary *)dataDict errDict:(NSDictionary *)errDict doDelete:(BOOL)doDelete</td>
        <td>Native模块回调结果给前端JS</td>
</table>

UZAppDelegate对象方法说明：

<table>
    <thead>
    <tr>
        <th width="50">方法</th>
        <th>描述</th>
    </tr>
    </thead>
    <tr>
        <td>- (void)addAppHandle:(id <UIApplicationDelegate>)handle</td>
        <td>注册一个实现了UIApplicationDelegate协议的对象。注册后对象可以实现推送消息、处理第三方应用回调等功能</td>
    </tr>
</table>

#**第八章Native模块包结构说明**<div id="8"></div>
一个Native模块包根目录通常以该模块的JS对象名命名（以下以moduleDemo为例），模块包内包含res_moduleDemo、target、test、doc四个文件夹以及module.json。

目录解释：

- res_moduleDemo目录：放置资源文件等；
- target目录：存放编译生成的静态库文件；
- test目录：存放模块的测试网页；
- doc目录：存放模块的api文档；
- module.json文件：内容为JSON字符串，定义了模块的类名称、JS对象名称、方法等;

注意：此处的module.json不同于UZApp中的module.json文件，UZApp中的module.json是对工程中所有用到的模块配置文件的集合。
模块包列表如下图所示：
 
![图片说明](/img/docImage/159.png)
