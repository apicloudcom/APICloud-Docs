/*
Title: 模块包结构说明
Description: 模块包结构说明
Sort: 3
*/


[模块包结构](#1)

[doc](#2)

[test](#3)

[target](#4)

[res_xxx](#5)

[module.json](#6)

#**模块包格式**<div id="1"></div>

模块包以模块的名称命名，这里以fs模块为例进行说明，里面包括doc、test、res_fs、target四个文件夹以及module.json文件。其结构如下图：

![图片说明](/img/docImage/14.png)
 
#**doc**<div id="2"></div>

doc文件夹用于存放模块api说明文档，如fsRef.pdf。

#**test**<div id="3"></div>

test文件夹用于存放模块测试case。

#**target**<div id="4"></div>

target文件夹用于存放静态库（.a、.so等）以及jar包。

iOS平台下，framework库也需要放在该文件夹下；若资源文件需要以Create groups for any added folders方式加入工程，则需要将资源文件也放在该目录下。

#**res_xxx**<div id="5"></div>

res_xxx文件夹用于存放本模块使用到的资源文件，如图片、音频、布局、动画文件等。命名方式为res_加上模块名称，如：res_baiduMap。
iOS平台下，该文件夹会以Create folders references for any added folders方式加入工程。详情请参考[模块开发指南(iOS)](/APICloud/技术专题/module-dev-guide-for-ios)文档。
Android平台下，该文件夹包含子目录res以及AndroidManifest.xml文件。res子目录结构同标准Android工程下的res目录结构相同，且只存放本模块使用到的资源文件，云服务器在打包时将把这些文件并入引擎工程中。详情请参考[模块开发指南(Android)](/APICloud/技术专题/module-dev-guide-for-android)文档。

#**module.json**<div id="6"></div>

module.json中声明了本模块入口类的路径、名称及其所映射的JS对象名称、方法等，如文件系统模块：

iOS：

```js
{
    "name":"fs",
    "class":"UZFileSystem",
    "methods":["open","close"],			//类中的实例方法，所有方法都带有一个参数
    "launchClassMethod":"launch"		//应用启动时执行的类方法，无参数，若配置，引擎会在应用启动时调用该类方法，模块可以在该方法中执行初始化操作
}
```

Android：

```js
{
    "name":"fs",
    "class":"com.uzmap.pkg.uzmodules.fs.UzFsUtils"
}
```