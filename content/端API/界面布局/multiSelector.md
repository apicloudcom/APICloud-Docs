/*
Title: multiSelector
Description: multiSelector
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[hide](#6)

[close](#2)

[show](#3)

[hidden](#4)

[hide](#5)
</div>

#**概述**

multiSelector封装了一个支持多选的选择器，开发者可自定义该选择器的样式及其数据源

![图片说明](/img/docImage/multiSelector.jpg)

#**open**<div id="1"></div>

打开选择器

open({params}, callback(ret, err))

##params

y：

- 类型：数字
- 默认值：屏幕高度-244
- 描述：（可选项）视图的起点y轴坐标

height：

- 类型：数字
- 默认值：244
- 描述：（可选项）视图的高度

cancelImg：

- 类型：字符串
- 默认值：默认图片
- 描述：（可选项）选择器左上角取消按钮的图片

enterImg：

- 类型：字符串
- 默认值：默认图片
- 描述：（可选项）选择器右上角确定按钮的图片

titleImg：

- 类型：字符串
- 默认值：默认图片
- 描述：（可选项）选择器工具栏的背景图片

bgImg：

- 类型：字符串
- 默认值：默认图片
- 描述：（可选项）选择的背景图片

fontColor：

- 类型：字符串
- 默认值：#828282
- 描述：（可选项）常态字体颜色，支持rgb，rgba，#

selectedColor：

- 类型：字符串
- 默认值：#79CDCD
- 描述：（可选项）选中字体颜色，支持rgb，rgba，#

<del>animation：</del>

- <del>类型：布尔值</del>
- <del>默认值：true</del>
- <del>描述：（可选项）打开关闭时是否添加动画</del>

anim：

- 类型：布尔值
- 默认值：true
- 描述：（可选项）打开关闭时是否添加动画

content：

- 类型：数组
- 默认值：无
- 描述：选择器的内容

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：（可选项）将此模块视图添加到指定窗口的名字

selectedItems：

- 类型：数组
- 默认值：无
- 描述：（可选项）默认选中的条目的下标组成的数组，下标从0开始，-1表示全选
- 备注：不传则open时未有选中项

selectIcon:

- 类型：json对象
- 默认值：见内部字段
- 描述：（可选项）表示选中、未选中的图标设置
- 内部字段：

```js
  {
       normal:    //（可选项）选中提示图标常态图片路径，支持fs、widget等本地路径协议，有默认图标
       selected:  //（可选项）选中后的图标路径，支持fs、widget等本地路径协议，有默认图片
  } 
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	selectAry:             //选中的字符串组成的数组 deprecate
	selectArray:           //选中的字符串组成的数组
}
```

##示例代码

```js
var arrayTitle = new Array();
arrayTitle[0]='第一条';
arrayTitle[1]='第二条';
arrayTitle[2]='第三条';
var obj = api.require('multiSelector');
obj.open({
         content:arrayTitle
     },function(ret,err){
         var selectObj=":";
         for (var index in ret.selectAry)
         {
             selectObj = selectObj + ret.selectAry[index];
         }
         api.alert({msg:'选择器选取的数据是'+ selectObj});
 });
```

##补充说明

打开选择器

##可用性

IOS系统 android系统

可提供的1.0.0及更高版本

#**setSelect**<div id="6"></div>

设置/取消选中条目

setSelect({params})

##params

indexs：

- 类型：数组
- 默认值：-1
- 描述：（可选项）设置要选中的条目的下标组成的数组（若该条目为已选中状态则会取消其选中状态），下标从0开始，-1表示全选



##示例代码

```js
 var obj = api.require('multiSelector'); obj.setSelect({      index:[-1] });
```

##补充说明

无

##可用性

IOS系统 android系统

可提供的1.0.1及更高版本


#**close**<div id="2"></div>

关闭选择器

close()

##示例代码

	var obj = api.require('multiSelector');
	obj.close();

##补充说明

关闭选择器

##可用性

IOS系统 android系统

可提供的1.0.1及更高版本



#**show**<div id="3"></div>

显示选择器

show()

##示例代码

	var obj = api.require('multiSelector');
	obj.show();

##补充说明

无

##可用性

IOS系统 android系统

可提供的1.0.1及更高版本


#**<del>hidden</del>**<div id="4"></div>

<del>隐藏选择器</del>

<del>hidden()</del>

##<del>示例代码</del>

	var obj = api.require('multiSelector');
	obj.hidden();

##<del>补充说明</del>

<del>无</del>

##<del>可用性</del>

<del>IOS系统 android系统</del>

<del>可提供的1.0.1及更高版本</del>

#**hide**<div id="5"></div>

隐藏选择器

hide()

##示例代码

	var obj = api.require('multiSelector');
	obj.hide();

##补充说明

无

##可用性

IOS系统 android系统

可提供的1.0.1及更高版本
