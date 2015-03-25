/*
Title: chatBox
Description: chatBox
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[show](#3)

[hide](#4)

[becomeFirstResponder](#5)

[resignFirstResponder](#6)

[setMsg](#7)

[getMsg](#8)

[configMsg](#9)

[insertMsg](#10)
</div>

#**概述**

chatBox是一个聊天输入框模块，集成了表情，从相册选取图片的功能。开发者可自定义表情集，只需简单配置即可实现自定义表情和添加点击事件

![图片说明](/img/docImage/chatBox.jpg)

#**open**<div id="1"></div>

打开输入框

open({parmas},callback(ret, err))

##params

bgColor:

- 类型：字符串
- 默认值：#f2f2f2
- 描述：输入视图背景色的十六进制值，可为可空

lineColor:

- 类型：字符串
- 默认值：#d9d9d9
- 描述：输入框视图最上边的分割线色的十六进制值，可为空

borderColor:

- 类型：字符串
- 默认值：#B3B3B3
- 描述：输入框边框色的十六进制值，可为空

fileBgColor:

- 类型：字符串
- 默认值：#FFFFFF
- 描述：输入框背景色的十六进制值，可为空

switchButton:

- 类型：json对象
- 默认值：无
- 描述：表情键盘加号的按钮图片，可为空

内部字段：

```js
{
	faceNormal:           	// 表情按钮背景图片路径，可为空，默认纯绿色
	faceHighlight:          //表情按钮高亮图片路径，可为空
	addNormal:           	//添加按钮背景图片路径，可为空，默认纯绿色
	addHighlight:          	//添加按钮高亮图片路径，可为空
	keyboardNormal:      	//键盘按钮背景图片路径，可为空，默认纯绿色
	keyboardHighlight:    	//键盘按钮高亮图片路径，可为空
}
```

sourcePath：

- 类型：字符串
- 默认值:无
- 描述：自定义表情源文件(.json的文件和图片表情集文件同名且在同一路径下)的路径，不可
为空，json文件格式如下：[{name:’Expression_1’,text:’[微笑]’}]

addButtons：

- 类型：数组
- 默认值：无
- 描述：添加界面的按钮信息，可为空

内部字段：

```js
[{
	normal:              //常态按钮背景图片，可为空，默认绿色面板
	highlight:           //高亮按钮背景图片，可为空，默认暗色
	title:               //按钮标题，可为空，默认无
	titleSize:           //标题大小，可为空，默认10
	titleColor:          //标题颜色，可为空，默认#a3a3a3
}]
```

pageControl：

- 类型：json对象
- 默认值：参见内部字段
- 描述：表情和添加界面的页面控制器配置，可为空，为空时不显示页面控制器

内部字段：

```js
{
        normalColor:        //常态色，字符串，默认#c4c4c4，可为空
        highlightColor:     //选中色，字符串，默认#9e9e9e，可为空
}
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：将此模块视图添加到指定窗口的名字，可为空

placeholder：

- 类型：字符串
- 默认值：无
- 描述：输入框的占位提示文字，可为空，若为空则不显示提示文字

maxLines：

- 类型：数字
- 默认值：4
- 描述：输入框高度自适应输入的文字行数的最大限高值，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    click:           //是否是点击事件的回调，布尔类型
    index：			 //若click为true，则此参数为用户点击按钮的下标，否则undefined
    msg:             //返回输入的文字
}
```
##示例代码

```js
var addButtonAry = new Array();
	for (var i = 0; i< 3; i++) {
		addButtonAry[i]={
			normal:"widget://image/chatBox_album1.png",
            title:"相册"
        };
    }
var obj = api.require('chatBox');
obj.open({
	switchButton:{
		faceNormal:"widget://image/chatBox_face1.png",
		addNormal: "widget://image/chatBox_add1.png",
		keyboardNormal: "widget://image/chatBox_key1.png"
	},
	sourcePath:"widget://image/emotion",
	addButtons:addButtonAry
},function(ret,err){
if(ret.click){
	api.alert({msg:"用户点击了第"+ret.index+"个按钮"});
}else{
	api.alert({
		title: '输入的内容是',
		msg: ret.msg,
		buttons: ['确定']
		});
	}
});
```

##补充说明

打开输入框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**close**<div id="2"></div>

关闭聊天输入框

close()

##示例代码

```js
	var obj = api.require('chatBox');
	obj.close();
```

##补充说明

关闭聊天输入框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="3"></div>

显示聊天输入框

show()

##示例代码

```js
	var obj = api.require('chatBox');
	obj.show();
```

##补充说明

显示聊天输入框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="4"></div>

隐藏聊天输入框

hide()

##示例代码

```js
	var obj = api.require('chatBox');
	obj.hide();
```

##补充说明

隐藏聊天输入框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**becomeFirstResponder**<div id="5"></div>

弹出键盘

becomeFirstResponder(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:           //操作状态码
}
```
##示例代码

	var obj = api.require('chatBox');
	obj.becomeFirstResponder();

##补充说明

弹出键盘

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**resignFirstResponder**<div id="6"></div>

隐藏键盘

resignFirstResponder(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:           //操作状态码
}
```
##示例代码

	var obj = api.require('chatBox');
	obj.resignFirstResponder();

##补充说明

弹出键盘

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**setMsg**<div id="7"></div>

设置输入框内的文字

setMsg({params},callback(ret, err))
##params

msg：

- 类型：字符串
- 默认值：空字符串
- 描述：要设置的输入框内的文字内容，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status:           //操作状态码
}
```
##示例代码

```js
   var obj = api.require('chatBox');   obj.setMsg({      msg:"设置的文字"   },function(ret,err){      if(ret.status){        api.alert({msg:"设置成功"});      }   });```

##补充说明

设置输入框内的文字

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**getMsg**<div id="8"></div>

获取当前输入框内的文字

setMsg(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    msg:           // 字符串类型，获取到的当前输入框内的文字
}
```
##示例代码

```js
var obj = api.require('chatBox');obj.getMsg(function(ret,err){    api.alert({msg:ret.msg });});```

##补充说明

获取当前输入框内的文字

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**configMsg**<div id="9"></div>

配置当前输入框内的文字

configMsg({params},callback(ret, err))

##params

msg：

- 类型：字符串
- 默认值：无
- 描述：要设置的输入框内的文字内容，可为可空，为空时callBack当前值

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
        status:           // 布尔类型，操作是否成功状态值        msg:              // 字符串类型，获取到的当前输入框内的文字
}
```
##示例代码

```js
var obj = api.require('chatBox');obj.configMsg(function(ret,err){    if(ret.status){      api.alert({msg:ret.msg });    }});```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**insertMsg**<div id="10"></div>

向当前输入框内指定位置插入字符串

insertMsg({params})

##params

index：

- 类型：数字
- 默认值：当前输入框内字符串的长度
- 描述：插入当前输入框内字符串的位置，可为空

msg：

- 类型：字符串
- 默认值：空字符串
- 描述：要设置的输入框内的文字内容，可为空

##示例代码

```js
var obj = api.require('chatBox');obj.insertMsg({   msg:'这里是插入的字符串'});```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本
