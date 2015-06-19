/*
Title: 模块开发指南_Android
Description: 模块开发指南_Android
Sort: 5
*/


[第一章 SDK简介](#resoure2)

[第二章 阅读对象](#resoure3)

[第三章 SDK功能说明](#resoure4)
- [框架设计](#1)
- [主要功能](#2)

[第四章 开发前准备](#resoure5)
- [开发环境](#3)
- [开发帮助参考](#4)

[第五章 使用SDK开发Native模块](#resoure6)
- [导入SDK工程到Eclipse](#5)
- [开发设计Native模块](#6)

[第六章 Native模块开发Demo解释](#resoure7)

[第七章 SDK开放API说明](#resoure8)
- [类](#7)
- [重要API](#8)
- [常量说明](#9)

[第八章 Native模块包结构说明](#resoure9)

[第九章 其他](#resoure10)
- [模块资源文件命名规范](#10)
- [APICloud引擎固有资源说明](#11)
- [资源规范细则](#12)

#**第一章 SDK简介**<div id="resoure2"></div>
APICloud模块（Native Module）扩展SDK（以下简称SDK）是APICloud为满足广大开发者自定义扩展Native模块的热切需求，而推出的模块扩展开发SDK，提供给有一定Android基础的开发者，通过简单的接口实现，轻松接入APICloud平台，快速开发扩展模块，自行实现对APICloud引擎能力的增强，提升App的质量及用户体验。

一个完整的SDK包命名类似：ModulesDevProject_Android.zip。解压后是一个标准的Android工程目录，如图（1）所示：

![图片说明](/img/docImage/3.jpg)

备注：其中readme.txt是与版本描述相关的说明文件。

#**第二章 阅读对象**<div id="resoure3"></div>

本文档面向所有使用该SDK的Android开发人员、测试人员、合作伙伴以及对此感兴趣的其他用户。阅读该文档要求用户熟悉Android应用开发，并且对Html、CSS、Javascript有一定了解。APICloud引擎强调传输数据的简洁和统一性，因此选择轻量级的JSON作为Javascript和Native语言之间通讯的数据载体，所以要求开发者同时要熟悉Java和Javascript中JSON格式数据的操作。

<br/>

#**第三章 SDK功能说明**<div id="resoure4"></div>

Android SDK是开发者快速入门使用APICloud跨平台移动应用开发引擎，并熟练掌握扩展Native模块（Android平台）技巧及了解APICloud移动应用云平台的桥梁。

<br/>

##i.框架设计<div id="1"></div>

APICloud引擎以实现对操作系统底层能力的封装和扩展，通过系统Webkit浏览器引擎开放API给Javascript调用的形式，实现了HTML+CSS+Javascript开发语言和Object-C/Java/C/C++等Native开发语言之间的桥接，极大的丰富和增强了标准Javascript的能力。令前端开发者通过JS即可调用移动设备的底层功能，如：电话、短信、定位、多媒体、跨域http请求等，并能将如百度地图、支付宝等第三方厂商的SDK很容易的集成至App中来。

本SDK开放桥接机制，方便具有一定Android基础的开发者自由开发定义Native扩展模块，丰富JS的能力，提升App的用户体验。APICloud引擎框架桥接层设计如图（2）：

![图片说明](/img/docImage/4.png) 	


##ii.	主要功能<div id="2"></div>
		
本SDK 主要提供以下功能和接口：

* 映射一个Java类的函数和常量（统称为模块module）至Javascript对象的函数和常量，包括：

     -被映射Java类的函数、属性及常量书写规范

     -module.json文件的声明

* 往当前屏幕window中插入/移除一个或者多个自定义View，包括：

     -直接插入View至window

     -获取一个Activity的View并插入window

* 在module中启动另一个Activity或App并获取回调，包括：

     -直接启动Activity

     -启动Activity并获取返回值

* 启动widget、向window注入Javascript，包括：

	 -在module中调用引擎的widget管理能力启动widget

	 -向APP的某活动window注入并执行一段Javascript

* 扩展模块项目资源ID的管理,包括：

     -APICloud引擎及所有Native扩展模块（Module）中均不允许出现R文件的引用。

     -R文件对应的资源文件ID由引擎负责管理

<br/>

#**第四章 开发前准备**<div id="resoure5"></div>

##i.	开发环境：<div id="3"></div>

PC：Windows XP/Win7/8/Mac OS；

Eclipse3.7及以上；

ADT21及以上；

Android SDK 21（5.0）及以上；

JDK1.6或者1.7。尽量不要使用1.8，存在各种潜在问题；

其中Android环境推荐使用Google整合版的Eclipse：SDK ADT Bundle;

下载地址：http://developer.android.com/sdk/index.html#download

##ii.	开发帮助参考：<div id="4"></div>

Android在线API文档：http://developer.android.com/reference/packages.html

Javascript规范及入门：http://www.w3school.com.cn

JSON数据在线Viewer：http://www.bejson.com/go.html?u=http://www.bejson.com/jsonview2/

#**第五章 使用SDK开发Native模块**<div id="resoure6"></div>

##i.	导入SDK工程到Eclipse<div id="5"></div>

* 解压ModulesDevProject_Android.zip至任意目录

* 在Eclipse中导入该SDK，操作步骤：Eclipse ->File ->Import ->General ->Existing Project into Workspace ->Browser ->选择1中解压的目录 ->Finish即可

导入后的工程结构如图：
 
![图片说明](/img/docImage/5.jpg) 
	
##ii.	开发设计Native模块<div id="6"></div>

* 新建用于绑定映射至JS对象的类。在项目中新建Java类（以下以UZModuleDemo类为例，映射的JS对象为moduleDemo），继承自引擎Jar包中的APIModule或者UZModule类，并重写相关函数。如下图：

![图片说明](/img/docImage/7.jpg) 
 
* 定义并声明将被映射至JS类的Java函数。
若想将Java类中的某个函数映射至JS对象供JS调用，需要将该函数声明以“jsmethod_”开头，并且声明该函数为public，同时接收且仅能接受一个参数：UZModuleContext。

函数声明格式：```public void jsmethod_showAlert(final UZModuleContextmoduleContext){}```

APICloud引擎会在初始化的时候，根据Java函数是否包含“jsmethod_”的前缀，而将该函数映射至JS对象。例如声明“jsmethod_showAlert”，APICloud引擎会将“jsmethod_showAlert”函数映射至JS的“showAlert”函数，开发者在Html页面中即可使用moduleDemo.showAlert(argument)的方式直接调用至Java的jsmethod_showAlert函数，并进行相关操作。

如下图中的定义：

![图片说明](/img/docImage/6.jpg) 
 
实现了向JS对象映射：
- showAlert：弹出一个对话框；
- startActivity：启动一个Activity；
- startActivityForResult：启动一个Activity并要求返回值；
- vibrate：调用设备震动器震动；

这四个函数，在JS中使用：
- moduleDemo.showAlert(argument)；
- moduleDemo.startActivity(argument)；
- moduleDemo.startActivityForResult(argument)；
- moduleDemo.vibrate(argument)；
即可调用到对应的Java函数中；

注意：```以“jsmethod_”前缀声明的Java函数，APICloud终端引擎在操作该函数时，是在UI线程中进行的，所以请勿在该函数内部做耗时的操作，避免引起UI阻塞，抛出异常。```

* 获取JS传入的参数

APICloud引擎要求前端JS开发者必须使用JSON格式数据作为JS与Native之间交换数据的传参。APICloud引擎会对JS传入的参数进行解析并封装，通过包装成UZModuleContext类传递给声明“jsmethod_”前缀的函数。

UZModuleContext类是JS与Native之间通信的运行时上下文封装，既是JS提交给Native数据的载体，同时也是Native回调JS的执行者。UZModuleContext内部封装了JSON格式数据操作的所有方法，如optInt、optString等，UZModuleContext同时还封装了success、error等回调JS的方法。

例如Html页面这样写：	

![图片说明](/img/docImage/8.jpg)
 
那么在Java中则可以这样获取JS传入的msg值：

![图片说明](/img/docImage/9.jpg) 

* 将操作结果回调至JS

APICloud引擎采用JS与Native之间异步机制架构，Native做完相关操作后，应该将操作结果通知给JS页面，或者通知页面本次操作成功与否，错误提示等。该回调过程由UZModuleContext下的success、error等函数完成。如下图的代码实现了对“showAlert”结果的回调：

![图片说明](/img/docImage/10.png) 
		
* 模块声明文件module.json的编写

APICloud引擎要求Native模块扩展开发者必须在module.json文件中声明被映射Java类的class路径，以及其所映射的JS对象名称。APICloud引擎根据该文件寻找相应Java类，并在适当时候将其初始化。

module.json文件固定存放于assets下的uzmap目录中，不得更改。存储格式为JSON格式，包含modules、name、class等字段。声明标准如下：

```js
{
	modules:[
		{
		name:'moduleDemo',
		class:'com.uzmap.moduleDemo.UZModuleDemo'
		},
		{
		name:'xxxDemo',
		class:'com.xxx.Objxxx'
		},
		{
		name:'xxxDemo1',
		class:'com.xxx.Objxxx1'
		}
	]
}
```

字段解释：
- name：定义该扩展模块所对应的JS对象名，类似于标准JS中的window、document、Math等对象。
- class：定义该扩展模块对应被JS映射的Java类路径。


* 导出Native模块包

Native模块开发调试完毕后，需要将你的代码及资源按规范导出成模块包（zip格式），并提交至APICloud云打包服务器上。

* 模块包结构预览	

[见第八章Native模块包结构说明](#resoure9)

* 导出模块包操作步骤：

导出所有代码与你模块相关的代码文件到jar包里。操作步骤：

		（1）、导出所有代码与你模块相关的代码文件到jar包里。操作步骤：File -> Export ->JAR file ->选择你的代码，一路next即可。
		（2）、从工程res目录中分离出所有与你的模块相关的资源文件，且不改变其所在目录;
		（3）、从工程AndroidManifest文件中分离出你的模块所定义的任何Activity、Service以及权限等;
		（4）、将1、2、3步骤得到的文件对应拷入moduleDemo目录下对应目录中;
		（5）、将moduleDemo目录压缩成zip格式包;

#**第六章 Native模块开发Demo解释**<div id="resoure7"></div>

本SDK默认展示一个扩展模块demo。该demo展示如何扩展一个名为moduleDemo的JS对象，并将该对象映射至Java类（UZModuleDemo）的过程，同时展示如何在html页面中通过JS调用该模块。

UZModuleDemo类下每个API都有详细注释及使用实例，请开发者仔细阅读，同时请关注assets/widget目录下html页面的书写内容。

详细注释图：

![图片说明](/img/docImage/11.jpg)![图片说明](/img/docImage/12.jpg)

<br/>

#**第七章 SDK开放API说明**<div id="resoure8"></div>

本章节提供APICloud引擎所有开放接口的API说明。

##i.类<div id="7"></div>

本SDK提供四个重要的开放类，分别为：UZModule、UZCoreUtil、UZModuleContext、UZResourcesIDFinder，以及若干工具类API及常量，如：UZUtility、UZSslHttpManager等。

<table>
    <tr>
        <th>类</th>
        <th>描述</th>
    </tr>
    <tr>
        <td>UZModule</td>
        <td>所有扩展Native模块的基类，Java类通过继承该类并声明相应函数，实现Java类绑定映射至JS对象</td>
    </tr>
    <tr>
        <td>UZModuleContext</td>
        <td>JS函数映射至Native函数时所传递参数的载体，以及Native回调结果至JS的执行者。包含操作标准JSON的方法</td>
    </tr>
    <tr>
        <td>UZCoreUtil</td>
        <td>APICloud引擎工具类，提供CSS像素转设备像素，MD5，Cookie存取，Url转换等API</td>
    </tr>
    <tr>
        <td>UZResourcesIDFinder</td>
        <td>动态获取资源ID的工具类。在使用APICloud SDK的项目中不允许直接通过引用R文件来获取项目资源ID，必须通过该类下的接口动态获取资源ID</td>
    </tr>
	<tr>
        <td>UZOpenApi</td>
        <td>引擎对模块实现数据共享的类，该类下主要定义了诸多共享数据的关键key值</td>
    </tr>
	<tr>
        <td>UZUtility</td>
        <td>基础工具类，定义了许多实用函数，如获取外部存储路径，相对/绝对路径转换等</td>
    </tr>
	<tr>
        <td>UZSslHttpManager</td>
        <td>https（有证书或无证书）请求管理类</td>
    </tr>
	<tr>
        <td>UZHttpClient</td>
        <td>APICloud引擎内部封装的全局ajax（http、https）请求管理类，包括execute、cancel等接口。可直接调用，实现远程数据的获取，图片异步下载，资源缓存等</td>
</table>

##ii.重要API<div id="8"></div>
UZModule对象：
<table>
    <tr>
        <th>API</th>
        <th>描述</th>
    </tr>
    <tr>
        <td>runOnUiThread</td>
        <td>在UI线程中执行操作</td>
    </tr>
    <tr>
        <td>startActivityForResult</td>
        <td>启动一个Activity并要求返回值。所有使用APICloud SDK扩展的模块，在需要startActivityForResult时，都必须调用该接口，而不能直接调Activity的startActivityForResult</td>
    </tr>
    <tr>
        <td>finishApplication</td>
        <td>结束当前App</td>
    </tr>
    <tr>
        <td>insertViewToCurWindow</td>
        <td>插入一个自定义的View到当前window中</td>
    </tr>
	<tr>
        <td>removeViewFromCurWindow</td>
        <td>从当前window移除某个自定义View</td>
    </tr>
	<tr>
        <td>openWidgetWidthInfo</td>
        <td>打开一个widget</td>
    </tr>
	<tr>
        <td>closeWidgetWidthInfo</td>
        <td>关闭一个widget</td>
    </tr>
	<tr>
        <td>onActivityResult</td>
        <td>通过startActivityForResult时，回调结果可重写此接口获取</td>
	<tr>
        <td>getContext</td>
        <td>获取运行时上下文</td>
	<tr>
        <td>onClean</td>
        <td>APICloud引擎主动回调函数，当window或者frame关闭以及当前页面发生url变化时，引擎会主动回调该接口，开发者应该在此接口中清理当前模块占用的资源，如网络资源，内存资源等</td>
</table>

UZModuleContext对象：
<table>
    <tr>
        <th>API</th>
        <th>描述</th>
    </tr>
    <tr>
        <td>success</td>
        <td>Native模块正常回调结果给JS</td>
    </tr>
    <tr>
        <td>error</td>
        <td>当Native模块内部发生异常时，通过此接口回调结果给JS</td>
    </tr>
    <tr>
        <td>interrupt</td>
        <td>不处理回调。建议Native模块开发中，不想处理回调JS时，调用一下该函数</td>
    </tr>
    <tr>
        <td>opt*</td>
        <td>各种操作JSON数据的方法</td>
</table>

##iii.常量说明<div id="9"></div>
暂无

<br/>

#**第八章 Native模块包结构说明**<div id="resoure9"></div>

一个Native模块包根目录通常以该模块的JS对象名命名（以下以moduleDemo为例），二级子目录通常包含如下图目录结构：

![图片说明](/img/docImage/161.png)
	 
目录解释：

（1）、res_xxxx目录：xxx为您的扩展模块名。该目录与Android项目中的资源文件目录res目录相吻合，包含drawable、layout、values等子目录。在APICloud模块包中，该目录下只需对应存放你的模块中用到的资源文件即可。详情见[资源规范细则](#resoure10)。结构类似下图：

![图片说明](/img/docImage/222.png)

（2）、source目录：存放源代码的目录，如jar、java、c、cpp等文件。如下图：

![图片说明](/img/docImage/333.jpg)

（3）、target目录：用于存放本模块用到的so动态库文件。如下图：

![图片说明](/img/docImage/444.png)	 

（4）、AndroidManifest.xml文件：存放你的模块中用到的权限，定义的Activity，Service等。详情见[资源规范细则](#resoure10)。结构如下图所示：

![图片说明](/img/docImage/555.png)	 

（5）、module.json文件：即你的扩展模块描述文件。结构如下图：

![图片说明](/img/docImage/666.png)

<br/>

#**第九章 其他**<div id="resoure10"></div>
##i.模块资源文件命名规范<div id="10"></div>
APICloud建议开发者在开发过程中对资源文件的命名遵循如下规则：
mo + 模块名 + 功能或UI类型 + 资源类型。

	例如（以moduleDemo模块为例）：
	命名一个布局资源文件：
	mo_moduleDemo_demo_activity_layout.xml

	命名一个图片资源文件：
	mo_moduleDemo_backbtn_press_bg.png
	mo_moduleDemo_layout_bg.png

	命名一个字符资源文件：
	mo_moduleDemo_init_msg
	mo_moduleDemo_error_msg
		
##ii.APICloud引擎固有资源说明<div id="11"></div>

APICloud SDK工程目录下，凡是以“uz_”前缀打头命名的资源文件，请开发者不要随意改动，保持其原状，否则SDK可能在启动过程中报找不到引擎资源的警告而强制退出。
		
##iii.资源规范细则<div id="12"></div>	
暂定
