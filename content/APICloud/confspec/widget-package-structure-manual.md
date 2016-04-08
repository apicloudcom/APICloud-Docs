/*
Title: Widget包结构说明
Description: Widget包结构说明
Sort: 2
*/


[widget包格式](#1)

[config.xml](#2)

[index.html](#3)

[error](#4)

[icon](#5)

[launch](#6)

[html](#7)

[css](#8)

[script](#9)

[image](#10)

[res](#11)

[wgt](#12)

#**widget包格式**<div id="1"></div>

![图片说明](/img/docImage/16.png)

#**config.xml**<div id="2"></div>

config文件为整个Widget的入口，它包含了关于该Widget的重要信息，如：名称、作者信息、描述、云端ID、偏好设置、权限配置、模块概览以及入口html（index.html）文件。详情见[应用配置说明](/APICloud/技术专题/app-config-manual)文档

#**index.html**<div id="3"></div>

在config文件中配置的默认第一个加载页面，详情见[应用配置说明](/APICloud/技术专题/app-config-manual)文档

#**error**<div id="4"></div>

页面加载出错时的提示页，页面名称必须为error.html

![图片说明](/img/docImage/17.png)
 
#**icon**<div id="5"></div>

应用图标，分辨率为150*150（仅供APICloud Studio本地测试版本使用，云端正式版本不需要在此设置，以减小应用包大小）

![图片说明](/img/docImage/18.png)
 
#**launch**<div id="6"></div>

启动图片，分辨率为1080*1920（仅供APICloud Studio本地测试版本使用，云端正式版本不需要在此设置，以减小应用包大小）

![图片说明](/img/docImage/19.png)
 
#**html**<div id="7"></div>

html网页文件

![图片说明](/img/docImage/20.png)
 
#**css**<div id="8"></div>

css样式

![图片说明](/img/docImage/21.png)
 
#**script**<div id="9"></div>

js脚本

![图片说明](/img/docImage/23.png)
 
#**image**<div id="10"></div>

图片资源

![图片说明](/img/docImage/24.png)

#**res**<div id="11"></div>

res文件夹下主要放置资源文件。

Apple Watch资源需要放到此目录下，编译Apple Watch应用时会从该目录读取资源，详情参考Apple Watch开发指南。

若要更改iOS中的Info.plist，可以将修改后的Info.plist放置在res目录下，编译时会将更改内容写入到工程中的Info.plist。详细请参考论坛帖子http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=20

#**wgt**<div id="12"></div>

子wgt目录，子widget根目录名称为widgetId
 
![图片说明](/img/docImage/25.png)
