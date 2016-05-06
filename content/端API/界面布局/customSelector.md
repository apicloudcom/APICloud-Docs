/*
Title: customSelector
Description: customSelector
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[set](#2)

[close](#3)

[hide](#4)

[show](#5)

</div>

#**概述**

customSelector 是自定义分级选择器模块，开发者可自定义选择器的大小、位置、内容级别（Android 暂仅最大支持3级）和数据源及其显示样式，可设置指定选中项。本模块是由第三方模块开发者提供，使用此模块需在线云编译安装包。本模块已停止优化更新，建议使用[UISelector](http://docs.apicloud.com/端API/界面布局/UISelector)

![图片说明](/img/docImage/customSelector.jpg)

#**open**<div id="1"></div>

打开选择器

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：当前设备屏幕宽度除以4.0
- 描述：（可选项）选择器视图左上角点坐标

y：

- 类型：数字
- 默认值：0
- 描述：（可选项）选择器视图左上角点坐标

w：

- 类型：数字
- 默认值：当前设备屏幕的宽度除以2.0
- 描述：（可选项）选择器视图宽

h：

- 类型：数字
- 默认值：当前设备屏幕的高度减80
- 描述：（可选项）选择器视图高

bg：

- 类型：字符串
- 默认值：rgba(0,0,0,0)
- 描述：（可选项）视图背景设置，支持 rgb、rgba、#、img

style：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）设置选择器的样式
- 内部字段：

```js
{
	row：                        //数字类型，每列显示的行数，默认7，可为空
		text:{
			size:                //字体大小，数字类型，默认50，可为空
			selectedColor:       //选中色，字符串，支持 rgb,rgba,#,默认#ffffff，可为空
			color:               //常态文字颜色，字符串，支持 rgb,rgba,#,默认#218868，可为空
			}
		bg:{
			color:               //常态背景色，字符串，支持 rgb,rgba,#,默认#87ceeb,可为空
       		selectedColor:       //选中后的背景色,字符串,支持 rgb,rgba,#,默认,#218868可为空
			rect:                //背景视图在选择器单元格内的位置大小信息,json对象，可为空
	           {
                w:               //背景视图的宽，默认单元格宽-20，可为空
                h:               //背景视图的高，默认单元格高-20，可为空
            },
			zoomIn：             //选中后放大倍数，数字类型，默认1.2，可为空
    }
}
```

dataSource：

- 类型：数组对象/字符串
- 默认值：无
- 描述：选择器的数据源，若为字符串，则表示 JSON 文件的路径(支持widget,fs等协议)，文件格式同下文内部字段
- 内部字段：

```js
[{
      title:   		    //一级目录的标题，字符串，不可为空
      contents:		    //一级目录的内容组成的数组，可为字符串或json对象，不可为空        
      [{                //此内容若是字符串组成的数组，则表示该选择器为二级选择器，若本字段内容是json对象组成的数组，则表示该选择器为三级选择器，最高支持到三级，json对象的内部字段如下：
        	title：     //二级目录的标题列表，字符串，不可为空
        	contents：  //三级目录的内容组成的数组，数组类型，不可为空
	   }]
}]
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

indexs：

- 类型：数组
- 默认值：每列的第一条数据
- 描述：（可选项）设置的各列 item 的下标(不可超过本列 item 总数)组成的数组

bounce：

- 类型：布尔
- 默认值：true
- 描述：（可选项）列表滑动到头是否弹动

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status:             //布尔值，操作是否成功
	selects:            //从各级目录选取的内容组成的数组，若本选择器是自定义的二级选择器，则此数组包含两个元素，若本选择器是自定义的三级选择器，则此数组包含三个元素
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:               //错误信息，字符串类型
}
```

##示例代码

```js
var customSelector = api.require('customSelector');
customSelector.open({
    dataSource: [{
        title: 'A',
        contents: [{
            title: 'a',
            contents: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10']
        }]
    }, {
        title: 'B',
        contents: ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
    }, {
        title: 'C',
        contents: ['1a', '2b', '3c', '4d', '5e', '6f', '7g', '8h', '9i', '10j']
    }, {
        title: 'D',
        contents: ['1t', '2t', '3t', '4t', '5t', '6t', '7t', '8t', '9t', '10t']
    }, {
        title: 'E',
        contents: ['1a', '2a', '3a', '4a', '5a', '6a', '7a', '8a', '9a', '10a']
    }, {
        title: 'F',
        contents: ['1f', '2f', '3f', '4f', '5f', '6f', '7f', '8f', '9f', '10f']
    }, {
        title: 'G',
        contents: ['1!', '2!', '3!', '4!', '5!', '6!', '7!', '8!', '9!', '10!']
    }, {
        title: 'H',
        contents: ['1th', '2th', '3th', '4th', '5th', '6th', '7th', '8th', '9th', '10th']
    }, {
        title: 'I',
        contents: ['one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine', 'ten']
    }, {
        title: 'J',
        contents: ['壹', '貮', '叁', '肆', '伍', '陆', '柒', '捌', '玖', '拾']
    }, {
        title: 'K',
        contents: ['一', '二', '三', '四', '五', '六', '七', '八', '九', '十']
    }]
}, function(ret, err){     
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

初始化选择器，并打开

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**set**<div id="2"></div>

设置选择器选中的 items

set({params})

##params

indexs：

- 类型：数组
- 默认值：无
- 描述：设置的各列 item 的下标(不可超过本列 item 总数)组成的数组

##示例代码

```js
var customSelector = api.require('customSelector');
customSelector.set({
	indexs: [2,3,6]
});
```

##补充说明

设置选中状态

##可用性

IOS 系统

可提供的1.0.0及更高版本

#**close**<div id="3"></div>

关闭选择器

close()

##示例代码

```
var customSelector = api.require('customSelector');
customSelector.close();
```js

##补充说明

关闭时间选择器

##可用性

IOS 系统

可提供的1.0.0及更高版本


#**hide**<div id="4"></div>

隐藏选择器

hide()

##示例代码

```
var customSelector = api.require('customSelector');
customSelector.close();
```js

##补充说明

隐藏选择器，并没有从内存里清除

##可用性

IOS 系统

可提供的1.0.1及更高版本


#**show**<div id="5"></div>

显示选择器

show()

##示例代码

```
var customSelector = api.require('customSelector');
customSelector.show();
```js

##补充说明

显示已隐藏的选择器

##可用性

IOS 系统

可提供的1.0.1及更高版本


