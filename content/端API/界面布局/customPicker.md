/*
Title: customPicker
Description: customPicker
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[hide](#3)

[show](#4)

</div>

#**概述**

customPicker是自定义选择器模块，支持多列，各列数据之间相互独立。本模块已停止更新，建议使用优化升级版模块[UICustomPicker](http://docs.apicloud.com/端API/界面布局/UICustomPicker)

#**open**<div id="1"></div>

打开选择器

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：（可选项）选择器视图左上角x坐标

y：

- 类型：数字
- 默认值：屏幕高度减去h
- 描述：（可选项）选择器视图左上角y坐标

w：

- 类型：数字
- 默认值：屏幕宽度
- 描述：（可选项）选择器视图宽

h：

- 类型：数字
- 默认值：264
- 描述：（可选项）选择器视图高

bg：

- 类型：字符串
- 默认值：#fff
- 描述：（可选项）选择器背景，支持颜色（#、rgb、rgba等格式）和图片（widget://、fs://等协议）

showHeader：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示选择器的header，若显示，那么只有点击完成按钮才会把选择的项回调给前端，若不显示，那么每选择一项就会马上回调给前端

header：

- 类型：json对象
- 默认值：见内部字段
- 描述：（可选项）设置选择器的header

内部字段：

```js
{
	h:							//（可选项）高度，默认44，数字类型
	bg:							//（可选项）背景，默认rgb(246,246,246)、支持颜色（#、rgb、rgba等格式）和图片（widget://、fs://等协议）
	title:						//（可选项）显示在header中间的标题，居中显示，默认无标题
	titleSize:					//（可选项）显示在header中间的标题文字大小，默认值：18
	titleColor:					//（可选项）显示在header中间的标题文字颜色，默认值：rgb(0,0,0)
	btnTitleSize:				//（可选项）按钮文字大小，默认值：15
	cancel:{					//（可选项）取消按钮，JSON对象
		leftMargin:				//（可选项）取消按钮距离左边的距离，默认值：10
		w:						//（可选项）取消按钮宽度，默认值：50
		h:						//（可选项）取消按钮高度，默认值：32
		title:					//（可选项）取消按钮标题，默认值：取消
		normalColor:			//（可选项）取消按钮正常状态标题颜色，默认值：rgb(0,0,0)
		highlightColor:			//（可选项）取消按钮高亮状态标题颜色，默认值：rgb(51,51,51)
		normalBgImg:			//（可选项）取消按钮正常状态背景图，不传则无背景图
		highlightBgImg:			//（可选项）取消按钮高亮状态背景图，不传则无背景图
	}
	done:{						//（可选项）完成按钮，JSON对象
		rightMargin:			//（可选项）完成按钮距离右边的距离，默认值：10
		w:						//（可选项）完成按钮宽度，默认值：50
		h:						//（可选项）完成按钮高度，默认值：32
		title:					//（可选项）完成按钮标题，默认值：取消
		normalColor:			//（可选项）完成按钮正常状态标题颜色，默认值：rgb(0,0,0)
		highlightColor:			//（可选项）完成按钮高亮状态标题颜色，默认值：rgb(51,51,51)
		normalBgImg:			//（可选项）完成按钮正常状态背景图，不传则无背景图
		highlightBgImg:			//（可选项）完成按钮高亮状态背景图，不传则无背景图
	}
}
```

rowHeight：

- 类型：数字
- 默认值：40
- 描述：（可选项）每一行高度，所有列的行高都一致

columnSeparateLineColor：

- 类型：字符串
- 默认值：rgba(0,0,0,0)
- 描述：（可选项）各列间分隔线颜色

dataSourceTitleKey：

- 类型：字符串
- 默认值：title
- 描述：（可选项）数据源里面标题对应的字段名

dataSource:

- 类型：JSON数组
- 默认值：无
- 描述：数据源，数组长度决定了列数。其里面的每一项需为数组，该项对应该列的数据源

内部字段：

```js
[
	[{
		title:					//标题
	}],
	[{
		title:					//标题
	}]
]
```

columnStyles:

- 类型：JSON数组
- 默认值：参加内部字段
- 描述：（可选项）配置每一列样式

内部字段：

```js
[{
	w:							//（可选项）列宽，默认为总宽度除以列数，数字类型
	commonTextSize:				//（可选项）普通行文字大小，默认值：15，数字类型
	commonTextColor:			//（可选项）普通行文字颜色，默认值：rgb(51,51,51)
	centreTextSize:				//（可选项）中间行文字大小，默认值：20，数字类型
	centreTextColor:			//（可选项）中间行文字颜色，默认值：rgb(0,0,0)
	centreBg:					//（可选项）中间行背景颜色，默认值：rgba(0,0,0,0)
	centreLineW:				//（可选项）中间行分隔线宽度，默认为w的值
	centreLineColor:			//（可选项）中间行分隔线颜色，默认值：rgb(0,0,0)
}]
```

selectedIndexs:

- 类型：数组
- 默认值：每列默认选中第一项
- 描述：（可选项）设置每列选中的项

内部字段：

```js
[0, 0, ...]
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否固定住不随页面滚动而移动

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	indexs:[0,1,...]			//每一列当前选中的项索引，数组长度依赖于列数
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:				//错误信息，字符串类型
}
```

##示例代码

```js
var first = [{title: '简体中文'},{title: '英语'},{title: '法语'}];
var dataSource = [];
dataSource[0] = first;
var obj = api.require('customPicker');
obj.open({
    dataSource: dataSource,
    header:{
        title:'选择语言'
    }
},function(ret, err){
    if(ret){
        var indexs = ret.indexs;
        var index = indexs[0];
        var msg = '您选择了'+first[index].title;
        api.alert({msg:msg});
    }
});
```

##补充说明

无

##可用性

iOS系统，android系统

可提供的1.0.0及更高版本

#**close**<div id="2"></div>

关闭选择器

close()

##示例代码

	var obj = api.require('customPicker');
	obj.close();

##补充说明

关闭选择器

##可用性

iOS系统

可提供的1.0.0及更高版本

#**hide**<div id="3"></div>

隐藏选择器

hide()

##示例代码

    var obj = api.require('customPicker');
    obj.hide();

##补充说明

隐藏选择器，并没有从内存清空

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**show**<div id="4"></div>

显示已隐藏选择器

show()

##示例代码

    var obj = api.require('customPicker');
    obj.show();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
