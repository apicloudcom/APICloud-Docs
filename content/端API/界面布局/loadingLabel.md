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

[show](#5)

[hide](#6)
</div>

#**概述**

loadingLabel是一个加载标签，可开启暂停关闭，开发者可自定义其色值和位置

#**open**<div id="1"></div>

打开加载标签

open({params},callBack(ret,err))

##params

bgColor：

- 类型：字符串
- 默认值：#474747
- 描述：（可选项）非活跃色，支持rgb，rgba，#

lightColor：

- 类型：字符串
- 默认值：#7A8B8B
- 描述：（可选项）活跃色，支持rgb，rgba，#

centerX：

- 类型：数字
- 默认值：当前设备屏幕的中间
- 描述：（可选项）加载标签的中心点坐标

centerY：

- 类型：数字
- 默认值：100
- 描述：（可选项）加载标签的中心点坐标

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:
- 类型：布尔
- 默认值：true
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动

w：

- 类型：数字
- 默认值：60
- 描述：（可选项）加载标签视图的宽

h：

- 类型：数字
- 默认值：10
- 描述：（可选项）加载标签视图的高

gifPath：

- 类型：字符串
- 默认值：无
- 描述：（可选项）gif图片路径，暂仅支持本地协议路径：widget、fs等
- 备注：不传或传空时显示默认加载标签动画（三个点循环闪动），若本字段有有效值，则lightColor和bgColor两参数无意义

##callBack

ret：

- 类型：JSON对象

- 内部字段：

```js
{
	id:                  //打开模块视图的id
}
```

##示例代码

var loadingLabel = api.require('loadingLabel');
loadingLabel.open(function( ret, err ){
    if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});

##补充说明

打开加载标签

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stop**<div id="2"></div>

停止加载

stop({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id

##示例代码

```js
var loadingLabel = api.require("loadingLabel");
loadingLabel.stop({
    id: 1
});
```

##补充说明

停止加载，暂停加载标签的加载动画

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**start**<div id="3"></div>

开始加载

start({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id

##示例代码

```js
var loadingLabel = api.require('loadingLabel');
loadingLabel.start({
    id: 1
});
```

##补充说明

开始加载，开始加载标签的加载动画

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="4"></div>

关闭加载标签

close({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id

##示例代码

```js
var loadingLabel = api.require('loadingLabel');
loadingLabel.close({
    id:1
});
```

##补充说明

关闭加载标签，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="5"></div>

显示加载标签

show({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id

##示例代码

```js
var loadingLabel = api.require('loadingLabel');
loadingLabel.show({
    id:1
});
```

##补充说明

显示已隐藏的加载标签

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本




#**hide**<div id="6"></div>

隐藏加载标签

hide({params})

##params

id：

- 类型：数字
- 默认值：无
- 描述：操作的视图的id

##示例代码

```js
var loadingLabel = api.require('loadingLabel');
loadingLabel.hide({
    id: 1
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本