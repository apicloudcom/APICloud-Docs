/*
Title: selectList
Description: selectList
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[reloadData](#3)

[setRefreshHeader](#4)

[setRefreshFooter](#5)

[hide](#6)

[show](#7)

[deleteItem](#8)

[refreshItem](#9)

[insertItem](#10)

[setSelected](#11)

[getSelected](#12)

[getIndex](#13)

[getData](#14)

[getSortedData](#15)
</div>

#**概述**

selectList封装了一个选择列表，开发者可自定义列表的选择图标、选择内容、以及右边字母导航索引的样式，亦可对单条数据进行增删该查操作。


#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：（可选项）列表视图的左上角点的坐标

y：

- 类型：数字
- 默认值：0
- 描述：（可选项）列表视图的左上角点的坐标

w：

- 类型：数字
- 默认值：当前屏幕宽度
- 描述：（可选项）列表视图的宽

h：

- 类型：数字
- 默认值：当前屏幕的高
- 描述：（可选项）列表视图的高

style：

- 类型：json对象
- 默认值：无
- 描述：列表数据源
- 内部字段：

```js
{
		bg:            //（可选项）列表背景设置，支持rgb、rgba、#、img，默认#FFFFFF
		borderColor:   //（可选项）每个cell之间分割线的颜色，支持rgb，rgba，#，默认#696969
		itemNormal:    //（可选项）item的常态下背景色，支持rgb，rgba，#，默认#ffffff
		itemHighlight: //（可选项）item的常态下背景色，支持rgb，rgba，#，默认#ffffff
		itemSelected:  //（可选项）item的选中后的背景色，支持rgb，rgba，#，默认#696969
		itemHeight     //（可选项）item的高度，数字类型，默认44
		normalImg      //（可选项）选择标识常态图标路径，支持widget、fs等本地路径协议，若不传则不显示
		selectedImg    //（可选项）选择标识选中后图标路径，支持widget、fs等本地路径协议，若不传则不显示
		selectImgSize  //（可选项）选择标识的大小，数字类型，默认20
		titleColor     //（可选项）标题字体的颜色值，默认#696969，支持rgb，rgba，#
		titleSize      //（可选项）标题字体的大小,默认18
		subTitleColor  //（可选项）子标题标题字体的颜色值，默认#696969，支持rgb，rgba，#
		subTitleSize   //（可选项）子标题字体的大小,默认18
		titleWidth     //（可选项）标题的宽度，数字类型，默认50
}
```

indicator:

- 类型：json对象
- 默认值：无
- 描述：（可选项）是否添加右边索引导航条
- 备注：若不传则不显示右边索引导航条
- 内部字段：

```js
{
	bgColor:       	//（可选项）背景色，字符串，默认透明，支持rgb，rgba，#
	color:          //（可选项）索引指器颜色,字符串类型，默认#A1A1A1,支持rgb，rgba，#
}
```

contents：

- 类型：数组
- 默认值：无
- 描述：选择列表内容（字符串）组成的数组，模块内会按照a-z排序显示
- 内部字段：

```js
[{
	 title:        //标题字符串，不传则不显示
	 subTitle:     //子标题字符串，不传则不显示
}]
```

fixedOn:

- 类型：字符串
- 默认值：当前主窗口名
- 描述：（可选项）将模块视图添加在某个窗口上的名字


##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    id：        //返回视图的id，数字类型
    contents:   //选中的item的数据内容的数组，内部字段如下： 
                 内部字段：[{
                     title:       //原数据源的标题
                     subTitle:    //原数据源的子标题
	                 index:       //数字类型；模块内排序后本条数据的新索引值
                 }]            
}
```

##示例代码

```js
var obj = api.require('selectList');
obj.open({
	contents:[{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"}]
},function(ret,err){
	 api.alert({msg:ret.section+"*"+ret.index});
});
```

##补充说明

打开列表视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭selectList

close(params)

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

##示例代码

	var obj = api.require('selectList');
	obj.close({id:1});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**reloadData**<div id="3"></div>

刷新列表数据

reloadData({params})

##params

contents：

- 类型：数组
- 默认值：无
- 描述：(可选项)选择列表内容（字符串）组成的数组，模块内会按照a-z排序显示，若不传则仅停止加载更多状态
- 内部字段：

```js
[{
	 title:        //标题字符串，不传则不显示
	 subTitle:     //子标题字符串，不传则不显示
}]
```

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

##示例代码

```js
var obj = api.require('selectList');
obj.reloadData({
    id:1,
	contents:[{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"},{title:"阿宝",subTitle:"131313131313"}]
},function(ret,err){
				api.alert({msg:ret.section+"*"+ret.index});
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setRefreshHeader**<div id="4"></div>

设置下拉刷新样式

setRefreshHeader({params} ,callback(ret,err))

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

loadingImg：

- 类型：字符串
- 默认值：无
- 描述：下拉刷新的小箭头本地图片的路径

bgColor:

- 类型：字符串
- 默认值：#f5f5f5
- 描述：（可选项）下拉刷新视图的背景色

textColor：

- 类型：字符串
- 默认值：#8e8e8e
- 描述：（可选项）提示文字颜色

textDown：

- 类型：字符串
- 默认值：下拉可以刷新…
- 描述：（可选项）提示文字

textUp：

- 类型：字符串
- 默认值：松开开始刷新…
- 描述：（可选项）提示文字

showTime：

- 类型：布尔值
- 默认值：true
- 描述：（可选项）是否显示刷新时间

##callback

返回触发刷新事件

##示例代码

```js
var loadingImgae = 'widget://res/selectList_arrow.png';		//刷新的小箭头，不可为空
var bgColor = '#F5F5F5';									//下拉刷新的背景颜色，有默认值，可为空
var textColor= '#8E8E8E';									//提示语颜色，有默认值，可为空
var textDown= '下拉可以刷新...';								//尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始刷新...';								//触发刷新事件的提示语，有默认值，可为空
var showTime= true;											//是否显示时间，有默认值，可为空

var obj = api.require('selectList');
obj.setRefreshHeader({
       id:1,
		loadingImg : loadingImgae,
		bgColor:bgColor,
		textColor:textColor,
		textDown:textDown,
		textUp:textUp,
		showTime : showTime
},function(ret,err){
	//触发加载事件
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRefreshFooter**<div id="5"></div>
 
设置上拉加载更多
 
setRefreshFooter({params}, callback(ret, err))
 
##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id
 
loadingImg：
 
- 类型：字符串
- 默认值：无
- 描述：上拉加载更多时显示的小箭头的本地图片路径
 
bgColor：
 
- 类型：字符串
- 默认值：#f5f5f5
- 描述：（可选项）上拉加载更多视图的背景色，支持rgb，rgba，#
 
textColor：
 
- 类型：字符串
- 默认值：#8e8e8e
- 描述：（可选项）提示文字颜色，支持rgb，rgba，#
 
textDown：
 
- 类型：字符串
- 默认值：上拉可以加载更多...
- 描述：（可选项）提示文字
 
textUp：
 
- 类型：字符串
- 默认值：松开开始加载...
- 描述：（可选项）提示文字
 
 
showTime：
 
- 类型：布尔值
- 默认值：true
- 描述：（可选项）是否显示刷新时间
 
 
##callback(ret, err)
 
返回触发加载更多的事件
 
##示例代码
 
```js
var loadingImgae = 'widget://res/listView_arrow.png';       //刷新的小箭头，不可为空
var bgColor = '#F5F5F5';                                    //下拉刷新的背景颜色 ，有默认值，可为空
var textColor= '#8E8E8E';                                   //提示语颜色，有默认值，可为空
var textDown= '下拉可加载更多...';                             //尚未触发刷新时间的提示语，有默认值，可为空
var textUp= '松开开始加载...';                                 //触发刷新事件的提示语，有默认值，可为空
var showTime= true;                                         //是否显示时间，有默认值，可为空        
var obj = api.require('selectList');
obj.setRefreshFooter({
    id:1,
    loadingImg:loadingImgae,
    bgColor:bgColor,
    textColor:textColor,
    textDown:textDown,
    textUp:textUp,
    showTime:showTime
},function(ret,err){
    //触发加载事件
});
 
```
 
##补充说明
 
加载更多的设置
 
##可用性
 
iOS系统，Android系统
 
可提供的1.0.0及更高版本

#**hide**<div id="6"></div>

隐藏selectList列表视图

hide({params})

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

##示例代码

	var obj = api.require('selectList');
	obj.hide({
	 id:1
	});

##补充说明

隐藏列表视图，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="7"></div>

显示列表视图

show({params})

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

##示例代码

	var obj = api.require('selectList');
	obj.show({id:1});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**deleteItem**<div id="8"></div>

删除指定索引的数据

deleteItem({params})

##params

index：

- 类型：数字
- 默认值：列表最后一条数据的索引
- 描述：（可选项）要删除的数据的索引

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

##示例代码

```js
var obj = api.require('selectList');
 obj.deleteItem({
      id:1,
      index:2
 });
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
#**refreshItem**<div id="9"></div>

刷新指定index条目的数据

refreshItem({params})

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要刷新数据的item索引下标

content：

- 类型：json
- 默认值：无
- 描述：(可选项)选择列表内容（字符串）组成的json对象
- 内部字段：

```js
{
	 title:        //标题字符串，不传则不显示
	 subTitle:     //子标题字符串，不传则不显示
}
```

##示例代码

```js
var obj = api.require('selectList');
obj.refreshItem({
      id:1,
      index:2,
      content:{title:"APICloud",subTitle:"000000000"}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
 
#**insertItem**<div id="10"></div>

插入指定索引的数据

insertItemItem({params})

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

index：

- 类型：数字
- 默认值：列表最后一条数据的索引
- 描述：（可选项）要插入的item索引下标

content：

- 类型：json
- 默认值：无
- 描述：(可选项)选择列表内容（字符串）组成的json对象
- 内部字段：

```js
{
	 title:        //标题字符串，不传则不显示
	 subTitle:     //子标题字符串，不传则不显示
}
```

##示例代码

```js
var obj = api.require('selectList');
 obj.insertItem({
    id:1,
    index:2,
    content:{title:"APICloud",subTitle:"000000000"}
 });
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setSelected**<div id="11"></div>

设置选中的条目

setSelected({params})

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要设置选中项的item索引

selected：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否设置为选中状态

##示例代码

```js
var obj = api.require('selectList');
obj.setSelected({
      id:1,
      index:2
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getSelected**<div id="12"></div>

获取当前选中的条目

getSelected({params},callBack(ret,err))

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

##callBack(ret,err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{            
    contents:   //选中的item的数据内容的数组，内部字段如下： 
                 内部字段：[{
                     title:       //原数据源的标题
                     subTitle:    //原数据源的子标题
	                  index:       //数字类型；模块内排序后本条数据的新索引值
                 }]  
}
```
##示例代码

```js
var obj = api.require('selectList');
obj.getSelected({id:1},fucntion(ret,err){
    api.alert({msg:ret.indexs[0]});
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getIndex**<div id="13"></div>

根据唯一标识查找该item在列表中的下标

getIndex({params },callBack(ret,err))

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

key：

- 类型：字符串
- 默认值：无
- 描述：唯一标识的key

value：

- 类型：字符串
- 默认值：无
- 描述：每条item数据的唯一标识

##callBack

ret：

- 类型：JSON对象
- 内部字段：

```js
	{
	    index:     //获取的item的索引
	}
```

##示例代码

	var obj = api.require('selectList');
	obj.getIndex({
	     key:"uid",
	     value:"0000001"
	},function(ret,err){
	     api.alert({msg:ret.index})
	});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getData**<div id="14"></div>

根据item的索引获取item的数据

getData({params },callBack(ret,err))

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）要获取数据的item的索引

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
	{
    content:   //选中的item的数据内容的数组，内部字段如下： 
                 内部字段：{
                     title:       //原数据源的标题
                     subTitle:    //原数据源的子标题
                 }
	}
```
##示例代码

	var obj = api.require('selectList');
	obj.getData({
	     index:0
	},function(ret,err){
	     api.alert({msg:ret.data});
	});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getSortedData**<div id="15"></div>

获取排序后的所有的数据

getSortedData({params },callBack(ret,err))

##params

id:

- 类型：数字
- 默认值：无
- 描述：要操作的模块视图id

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
	{
    contents:   //open时传入的数据源经过排序处理后的新数组，内部字段如下： 
                 内部字段：[{
                     title:       //原数据源的标题
                     subTitle:    //原数据源的子标题
                 }]
	}
```
##示例代码

	var obj = api.require('selectList');
	obj. getSortedData({
	     id:1
	},function(ret,err){
	     api.alert({msg:ret.data});
	});

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本