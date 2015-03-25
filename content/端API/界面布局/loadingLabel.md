/*
Title: loadingLabel
Description: loadingLabel
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[stop](#2)

[start](#3)

[close](#4)
</div>

#**概述**

loadingLabel是一个加载标签，可开启暂停关闭，开发者可自定义其色值和位置

#**open**<div id="1"></div>

打开加载标签

open({params})

##params

bgColor：

- 类型：字符串
- 默认值：#474747
- 描述：菜单背景色，可为空

lightColor：

- 类型：字符串
- 默认值：#7A8B8B
- 描述：菜单按钮点击色，可为空

centerX：

- 类型：数字
- 默认值：当前设备屏幕的中间
- 描述：加载标签的中心点坐标，可为空

centerY：

- 类型：数字
- 默认值：导航条的最下边
- 描述：加载标签的中心点坐标，可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##示例代码

	var obj = api.require('loadingLabel');
	obj.open();

##补充说明

打开加载标签

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stop**<div id="2"></div>

停止加载

stop()

##示例代码

	var obj = api.require(loadingLabel);
	obj.stop();

##补充说明

停止加载，暂停加载标签的加载动画

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**start**<div id="3"></div>

开始加载

start()

##示例代码

	var obj = api.require('loadingLabel');
	obj.start();

##补充说明

开始加载，开始加载标签的加载动画

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本




#**close**<div id="4"></div>

关闭加载标签

close()

##示例代码

	var obj = api.require('loadingLabel');
	obj.close();

##补充说明

关闭加载标签，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

