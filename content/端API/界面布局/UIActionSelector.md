/*
Title: UIActionSelector
Description: UIActionSelector
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[hide](#2)

[show](#3)

[close](#4)

[setActive](#5)

[getActive](#6)
</div>

#**概述**

UIActionSelector 是一个支持弹出动画的多级选择器。调用 open 接口，会从当前 window 底部弹出一个 action 选择器，该选择器在 iOS 平台上是立体滚轮效果的，在 android 平台上二维平面效果的。开发者可自定义该选择器的数据源，利用此模块做出一个城市地区选择器、公司部门选择器，菜单选择器等各种炫酷的选择器。
 
本模块选择器是分级联动选择器，最多支持三级目录，每级目录直接是相关联包含的。通过 open 接口内的 layout 参数可配置选择器的级数、显示行数、行间距等各种样式信息。getActive、setActive 接口可获取、设置当前选中项。详情参考模块接口参数。

**本模块可替代 citySelector 模块来自定义城市选择器**。

模块概览图如下：

![图片说明](/img/docImage/UIActionSelector.png)
 
#模块接口
 
#**open**<div id="1"></div>

打开选择器

open({params}, callback(ret, err))

##params

datas：

- 类型：JSON 数组类型 或 路径类型
- 描述：为选择器指定数据，可以是 JSON 数组 或是以 JSON 数组格式内容保存的文件的fs://、widget://路径
- 数据格式：

```js
[                                      //JSON 数组类型；第一级选择项数组
	{
		name: '北京市',                //字符串类型；第一级选择项的名称
		sub: [                         //JSON 数组类型；第二级选择项数组
			{
				name: '东城区'         //字符串类型；第二级选择项的名称
			},{
				name: '西城区'         //字符串类型；第二级选择项的名称
			}
		]
	}, {
		name: '河南省',                //字符串类型；第一级选择项的名称
		sub: [                         //JSON 数组类型；第二级选择项数组
			{
				name: '郑州市',        //字符串类型；第二级选择项的名称
				sub: [                 //JSON 数组类型；第三级选择项数组
					{
						name: '中原区' //字符串类型；第三级选择项的名称
					},{
						name: '金水区' //字符串类型；第三级选择项的名称
					}
				]
			},{
				name: '驻马店市',      //字符串类型；第二级选择项的名称
				sub: [                 //JSON 数组类型；第三级选择项数组
					{
						name: '西平县' //字符串类型；第三级选择项的名称
					},{
						name: '泌阳县' //字符串类型；第三级选择项的名称
					}
				]
			}
		]
	}
]
```

layout：

- 类型：JSON 类型
- 描述：选择器的布局设置
- 内部字段：

```js
{
	row: 5,                            //（可选项）数字类型；每屏显示的数据行数，超出的数据可以滑动查看，只能是奇数；默认：5
    col: 3,                            //（可选项）数字类型；数据源的数据级数，最多3级；默认：3
    height: 30,                        //（可选项）数字类型；每行选项的高度；默认：30
    size: 12,                          //（可选项）数字类型；普通选项的字体大小；默认：12
    sizeActive: 14,                    //（可选项）数字类型；当前选项的字体大小；默认：同 size
    rowSpacing: 5,                     //（可选项）数字类型；行与行之间的距离；默认：5
    colSpacing: 10,                    //（可选项）数字类型；列与列之间的距离；默认：10
    maskBg: 'rgba(0,0,0,0.2)',         //（可选项）字符串类型；遮罩层背景，点击该区域隐藏选择器，支持 rgb，rgba，#，img；默认：rgba(0,0,0,0.2)
    bg: '#fff',                        //（可选项）字符串类型；选择器有效区域背景，支持 rgb，rgba，#，img；默认：#fff
    color: '#888',                     //（可选项）字符串类型；选项的文字颜色，支持 rgb，rgba，#；默认：#848484
    colorSelected: '#f00'              //（可选项）字符串类型；已选项的文字颜色，支持 rgb，rgba，#；默认：同 colorActive
}
```

animation：

- 类型：布尔类型
- 描述：弹出和隐藏选择器时是否带弹出动画效果
- 默认：true

cancel：

- 类型：JSON 类型
- 描述：取消按钮设置，取消按钮显示在选择器左上角
- 内部字段：

```js
{                                      //（可选项）JSON 对象类型；取消按钮设置
	text: '取消',                      //（可选项）字符串类型；取消按钮的显示文字；默认：未设置时只显示背景
	size: 12,                          //（可选项）数字类型；取消按钮的显示文字大小；默认：12
    w: 90,                             //（可选项）数字类型；取消按钮的宽；默认：90
    h: 35,                             //（可选项）数字类型；取消按钮的高；默认：35
    bg: '#fff',                        //（可选项）字符串类型；取消按钮的背景，支持 rgb，rgba，#，img；默认：'#fff'
    bgActive: '#ccc',                  //（可选项）字符串类型；取消按钮的背景高亮，支持 rgb，rgba，#，img；默认：同 bg
    color: '#888',                     //（可选项）字符串类型；取消按钮的文字颜色，支持 rgb，rgba，#；默认：'#848484'
    colorActive: '#fff'                //（可选项）字符串类型；取消按钮的文字颜色高亮，支持 rgb，rgba，#；默认：同 color
}

```

ok：

- 类型：JSON 类型
- 描述：确定按钮设置，确定按钮显示在选择器右上角
- 内部字段：

```js
{                                      //（可选项）JSON 对象类型；确定按钮设置
	text: '确定',                      //（可选项）字符串类型；确定按钮的显示文字；默认：未设置时只显示背景
	size: 12,                          //（可选项）数字类型；确定按钮的显示文字大小；默认：12
    w: 90,                             //（可选项）数字类型；确定按钮的宽；默认：90
    h: 35,                             //（可选项）数字类型；确定按钮的高；默认：35
    bg: '#fff',                        //（可选项）字符串类型；确定按钮的背景，支持 rgb，rgba，#，img；默认：'#fff'
    bgActive: '#ccc',                  //（可选项）字符串类型；确定按钮的背景高亮，支持 rgb，rgba，#，img；默认：同 bg
    color: '#888',                     //（可选项）字符串类型；确定按钮的文字颜色，支持 rgb，rgba，#；默认：'#848484'
    colorActive: '#fff'                //（可选项）字符串类型；确定按钮的文字颜色高亮，支持 rgb，rgba，#；默认：同 color
}

```

title：

- 类型：JSON 类型
- 描述：选择器顶部标题栏设置
- 内部字段：

```js
{                                      //（可选项）JSON 对象类型；选择器顶部标题栏设置
	text: '请选择',                    //（可选项）字符串类型；选择器的标题内容；默认：请选择
	size: 12,                          //（可选项）数字类型；标题内容的文字大小；默认：12
    h: 44,                             //（可选项）数字类型；标题栏的高；默认：44
    bg: '#eee',                        //（可选项）字符串类型；标题栏的背景，支持 rgb，rgba，#，img；默认：'#eee'
    color: '#888'                      //（可选项）字符串类型；标题内容的文字颜色，支持 rgb，rgba，#；默认：'#848484'
}

```

actives：

- 类型：数组 
- 描述：打开模块时默认选项下标组成的数组，如：[0,0,0]
- 默认：各级选项的首项的索引组成的数组


fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	eventType: 'ok',                   //字符串类型；交互事件类型，取值范围如下：
                                       //ok（表示用户点击了确定按钮）
                                       //cancel（表示用户取消了选择器显示，包括点击取消按钮和遮罩层）
	level1: '河南省',                  //字符串类型；第一级选项的内容；只在 eventType 是 ok 时有效
	level2: '驻马店市',                //字符串类型；第二级选项的内容；只在 eventType 是 ok 时有效
	level3: '泌阳县'                   //字符串类型；第三级选项的内容；只在 eventType 是 ok 时有效
}
```

##示例代码

```js
var UIActionSelector = api.require('UIActionSelector');
UIActionSelector.open({
    datas: 'widget://res/city.json',   //JSON 数组类型 或 路径类型；为选择器指定数据，可以是 JSON 数组 或是以 JSON 数组格式内容保存的文件的fs://、widget://路径
    layout: {
        row: 5,                        //（可选项）数字类型；每屏显示的数据行数，超出的数据可以滑动查看，只能是奇数；默认：5
        col: 3,                        //（可选项）数字类型；数据源的数据级数，最多3级；默认：3
        height: 30,                    //（可选项）数字类型；每行选项的高度；默认：30
        size: 12,                      //（可选项）数字类型；普通选项的字体大小；默认：12
        sizeActive: 14,                //（可选项）数字类型；当前选项的字体大小；默认：同 size
        rowSpacing: 5,                 //（可选项）数字类型；行与行之间的距离；默认：5
        colSpacing: 10,                //（可选项）数字类型；列与列之间的距离；默认：10
        maskBg: 'rgba(0,0,0,0.2)',     //（可选项）字符串类型；遮罩层背景，支持 rgb，rgba，#，img；默认：rgba(0,0,0,0.2)
        bg: '#fff',                    //（可选项）字符串类型；选择器有效区域背景，支持 rgb，rgba，#，img；默认：#fff
        color: '#888',                 //（可选项）字符串类型；选项的文字颜色，支持 rgb，rgba，#；默认：#848484
        colorActive: '#f00',           //（可选项）字符串类型；选项的文字颜色高亮，支持 rgb，rgba，#；默认：同 color
        colorSelected: '#f00'          //（可选项）字符串类型；已选项的文字颜色，支持 rgb，rgba，#；默认：同 colorActive
    },
    animation: true,
    cancel: {                          //（可选项）JSON 对象类型；取消按钮设置
        text: '取消',                  //（可选项）字符串类型；取消按钮的显示文字；默认：未设置时只显示背景
        size: 12,                      //（可选项）数字类型；取消按钮的显示文字大小；默认：12
        w: 90,                         //（可选项）数字类型；取消按钮的宽；默认：90
        h: 35,                         //（可选项）数字类型；取消按钮的高；默认：35
        bg: '#fff',                    //（可选项）字符串类型；取消按钮的背景，支持 rgb，rgba，#，img；默认：'#fff'
        bgActive: '#ccc',              //（可选项）字符串类型；取消按钮的背景高亮，支持 rgb，rgba，#，img；默认：同 bg
        color: '#888',                 //（可选项）字符串类型；取消按钮的文字颜色，支持 rgb，rgba，#；默认：'#848484'
        colorActive: '#fff'            //（可选项）字符串类型；取消按钮的文字颜色高亮，支持 rgb，rgba，#；默认：同 color
    },
    ok: {                              //（可选项）JSON 对象类型；确定按钮设置
        text: '确定',                  //（可选项）字符串类型；确定按钮的显示文字；默认：未设置时只显示背景
        size: 12,                      //（可选项）数字类型；确定按钮的显示文字大小；默认：12
        w: 90,                         //（可选项）数字类型；确定按钮的宽；默认：90
        h: 35,                         //（可选项）数字类型；确定按钮的高；默认：35
        bg: '#fff',                    //（可选项）字符串类型；确定按钮的背景，支持 rgb，rgba，#，img；默认：'#fff'
        bgActive: '#ccc',              //（可选项）字符串类型；确定按钮的背景高亮，支持 rgb，rgba，#，img；默认：同 bg
        color: '#888',                 //（可选项）字符串类型；确定按钮的文字颜色，支持 rgb，rgba，#；默认：'#848484'
        colorActive: '#fff'            //（可选项）字符串类型；确定按钮的文字颜色高亮，支持 rgb，rgba，#；默认：同 color
    },
    title: {                           //（可选项）JSON 对象类型；选择器顶部标题栏设置
        text: '请选择',                //（可选项）字符串类型；选择器的标题内容；默认：请选择
        size: 12,                      //（可选项）数字类型；标题内容的文字大小；默认：12
        h: 44,                         //（可选项）数字类型；标题栏的高；默认：44
        bg: '#eee',                    //（可选项）字符串类型；标题栏的背景，支持 rgb，rgba，#，img；默认：'#eee'
        color: '#888'                  //（可选项）字符串类型；标题内容的文字颜色，支持 rgb，rgba，#；默认：'#848484'
    },
    fixedOn: api.frameName
}, function(ret, err) {
    if (ret) {
        alert(JSON.stringify(ret));
    } else {
        alert(JSON.stringify(err));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="2"></div>

隐藏选择器

hide()

##示例代码

```js
var UIActionSelector = api.require('UIActionSelector');
UIActionSelector.hide();
```

##补充说明

隐藏选择器，只是移除到屏幕之外，还在内存里没有清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**show**<div id="3"></div>

显示选择器

show()

##示例代码

```js
var UIActionSelector = api.require('UIActionSelector');
UIActionSelector.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="4"></div>

关闭选择器

close()

##示例代码

```js
var UIActionSelector = api.require('UIActionSelector');
UIActionSelector.close();
```

##补充说明

关闭选择器，意味着从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setActive**<div id="5"></div>

设置当前选中项

setActive({params})

##params

actives：

- 类型：数组 
- 描述：打开模块时默认选项下标组成的数组，如：[0,0,0]
- 默认：各级选项的首项的索引组成的数组

##示例代码

```js
var UIActionSelector = api.require('UIActionSelector');
UIActionSelector.setActive({
    actives: [1,0,0]
});
```


##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getActive**<div id="6"></div>

获取当前选中项

getActive(callback(ret, err))

##callback

ret:

- 类型：JSON 对象
- 内部字段：

```js
{
	    level1: '河南省',                  //字符串类型；第一级选项的内容
		level2: '驻马店市',                //字符串类型；第二级选项的内容
		level3: '泌阳县'                   //字符串类型；第三级选项的内容
}
```


##示例代码

```js
var UIActionSelector = api.require('UIActionSelector');
UIActionSelector.getActive(function(ret, err){        
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本