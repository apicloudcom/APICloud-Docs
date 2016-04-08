/*
Title: mdReader
Description: mdReader
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[open](#1)

[setPath](#2)

[show](#3)

[hide](#4)

[close](#5)
</div>

#**概述**

mdReader 封装了一个简单的 markdown 阅读器，可将 markdown 格式的文件读取显示出来，开发者可自定义显示区域及显示区域的背景。**本模块暂仅支持读取纯 markdown 文本，不能识别混合 html 标签的 markdown 文本**

#**open**<div id="1"></div>

打开一个 markdown 格式的文档

open({params})

##params

rect：

- 类型：JSON对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320, //（可选项）数字类型；模块的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 300  //（可选项）数字类型；模块的高度；默认：所属的 Window 或 Frame 的高度
}
```
styles：

- 类型：JSON对象
- 描述：（可选项）模块的样式
- 内部字段：

```js
{
    bg: 'rgba(0,0,0,0)'   //（可选项）字符串类型；日历整体背景，支持rgb、rgba、#、图片路径，要求本地路径（fs://，widget://）；默认：'rgba(0,0,0,0)'
}
```

path：

- 类型：字符串
- 描述：文档的路径，要求本地路径（fs://，widget://）

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed：

- 类型：布尔
- 描述：（可选项）模块是否随所属 Window 或 Frame 滚动
- 默认值：true（不随之滚动）

##示例代码

```js
var mdReader = api.require('mdReader');
mdReader.open({
    path: 'widget://res/test.md',
    rect: {
      x: 0,
      y: 0,
      w: api.winWidth,
      h: api.frameHeight
    },
    styles: {
       bg: '#eee'
    },
    fixedOn: api.frameName,
    fixed: false
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setPath**<div id="2"></div>

设置阅读器的文件路径

setPath({params})

##params


path：

- 类型：字符串
- 描述：文档的路径，要求本地路径（fs://，widget://）

##示例代码

```js
var mdReader = api.require('mdReader');
mdReader.setPath({
    path: 'widget://md.md'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="3"></div>

显示阅读器

show()

##示例代码

```js
var mdReader = api.require('mdReader');
mdReader.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**hide**<div id="4"></div>

隐藏阅读器

hide()

##示例代码

```js
var mdReader = api.require('mdReader');
mdReader.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="5"></div>

关闭阅读器

close()

##示例代码

```js
var mdReader= api.require('mdReader');
mdReader.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
