/*
Title: hintChatBox
Description: hintChatBox
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setHintButton](#2)

[setHintButtonListener](#3)

[setAddView](#4)

[setInputFieldListener](#5)

[close](#6)

[show](#7)

[hide](#8)

[becomeFirstResponder](#9)

[resignFirstResponder](#10)

[setMsg](#11)

[getMsg](#12)

[configMsg](#13)

[insertMsg](#14)

[setHintView](#15)

[setPlaceholder](#16)
</div>

#**概述**

hintChatBox是一个聊天输入框模块，集成了表情，从相册选取图片的功能。开发者可自定义表情集，只需简单配置即可实现自定义表情和添加点击事件。开发者可自定义快捷输入面板，用户可选择快捷输入

#**open**<div id="1"></div>

打开输入框

open({parmas},callback(ret, err))

params

bgColor:

- 类型：字符串
- 默认值：#f2f2f2
- 描述：（可选项）输入视图背景色设置，支持rgb，rgba，#，img

lineColor:

- 类型：字符串
- 默认值：#d9d9d9
- 描述：（可选项）输入框视图最上边的分割线色，支持rgb，rgba，#

borderColor:

- 类型：字符串
- 默认值：#B3B3B3
- 描述：（可选项）输入框边框色，支持rgb，rgba，#

fileBgColor:

- 类型：字符串
- 默认值：#FFFFFF
- 描述：（可选项）输入框背景色，支持rgb，rgba，#

switchButton:

- 类型：json对象
- 默认值：无
- 描述：表情键盘加号的按钮图片，可为空
- 内部字段：

```js
	{
		faceNormal:        //(可选项)表情按钮背景图片路径，支持widget、fs等本地路径协议,默认纯绿色面板
		faceHighlight:     //(可选项)表情按钮高亮图片路径，支持widget、fs等本地路径协议,
		addNormal:         //(可选项)添加按钮背景图片路径，支持widget、fs等本地路径协议,，默认纯绿色面板
		addHighlight:      //(可选项)添加按钮高亮图片路径，支持widget、fs等本地路径协议,
		keyboardNormal:    //(可选项)键盘按钮背景图片路径，支持widget、fs等本地路径协议,，默认纯绿色面板
		keyboardHighlight: //(可选项)键盘按钮高亮图片路径，支持widget、fs等本地路径协议,
	}
```

addButtons：

- 类型：数组
- 默认值：见内部字段
- 描述：(可选项)添加界面的按钮信息
- 内部字段：

```js
	[{
		normal:               //（可选项）常态按钮背景图片，支持widget、fs等本地路径协议，默认绿色面板
		highlight:            //（可选项）高亮按钮背景图片，支持widget、fs等本地路径协议，默认暗色
		title:                //（可选项）按钮标题，默认无
		titleSize:            //（可选项）标题大小，默认10
	}]
```

pageControl：

- 类型：json对象
- 默认值：见内部字段
- 描述：（可选项）表情和添加界面的页面控制器配置
- 备注：可不传，不传则没有控制器
- 内部字段：

```js
	{
	    normalColor:        //（可选项）常态色，字符串，默认#c4c4c4
	    highlightColor:     //（可选项）选中色，字符串，默认#9e9e9e
	}
```

sourcePath：

- 类型：字符串
- 默认值:无
- 描述：自定义表情源文件(.json的文件和图片表情集文件同名且在同一路径下)的路径，不可为空，json文件格式如下：[{name:’Expression_1’,text:’[微笑]’}]

placeholder：

- 类型：字符串
- 默认值：无
- 描述：（可选项）输入框的占位提示文字

maxLines：

- 类型：数字
- 默认值：4
- 描述：（可选项）输入框高度自适应输入的文字行数的最大限高值

leftButton：

- 类型：json对象
- 默认值：无
- 描述：（可选项）输入框左边按钮设置
- 备注：若不传则不显示左边按钮
- 内部字段：

```js
{
	hint：{              //快捷文字提示面板设置，不可为空
	   bg：              //（可选项）面板背景设置，支持rgb，rgba，#，img，默认白色
      	buttons：[{      //提示面板导航按钮组成的数组
	          normal:   //按钮常态下的背景图片
	          selected: //点击后背景图片
       }]
		hints：
		[{            //快捷提示文面板设置，数组对象，与buttons按序一一对应
		 	size：    //（可选项）快捷文字大小，数字类型，默认12
			color:   //（可选项）快捷文字颜色，默认黑色，支持rgb，rgba，#
			contents://快捷文字内容组成的数组，数组对象
			normal:  //快捷提示文字开头标注图标，支持widget，fs，等本地路径
			selected://快捷提示文字开头选中标注图标，支持widget，fs,等本地路径
	    }]
	    activeBtn:  //数字类型；leftBtn显示的当前活跃按钮的索引，小于buttons数组元素总数；默认值为0
}
   }
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
	{
	    eventType：       //回调事件类型，字符串，取值范围如下：
	                       show:    //模块视图打开成功
	                       send:    //用户点击发送按钮事件
                          addBtn：  //用户点击右边加号按钮事件的回调，如果open时传了addButtons参数才有次类型的回调
                          faceBtn： //用户点击表情按钮事件的回调
                          leftBtn： //用户点击左边按钮事件的回调
                          addBoard：//用户点击添加面板内按钮的事件的回调
        click:           //是否是点击事件的回调，布尔类型 deprecated
        index:           //若eventType为addBoard（或者click为true），则此参数为用户点击按钮的下标，否则undefined
	    msg:             //返回输入的文字
	    btnStatus:       //字符串类型；当eventType为leftBtn时，本字段表示按钮状态，取值范围如下：
	                       normal:  //未被选中的状态
	                       selected://选中后的状态
	}
```

##示例代码

```js
var addButtonAry = [];
    for (var i = 0; i < 3; i++) {
        addButtonAry[i]={
            normal:"widget://image/chatBox_album1.png",
            title:"相册"
        };
    }
var obj = api.require('hintChatBox');
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

#**setHintButton**<div id="2"></div>

设置设置指定提示按钮为活跃状态项

setHintButton({params})

##params

index：

- 类型：数字
- 默认值：0
- 描述：（可选项）指定的索引

##示例代码

	var obj = api.require('hintChatBox');
	obj.setHintButton ({index:2});

##补充说明

配合open接口使用，若open接口无leftButton参数，此接口无意义

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setHintButtonListener**<div id="3"></div>

设置提示面板上提示按钮的监听

setHintButtonListener(callBack())

##callBack(ret)

ret：

- 类型：JSON对象

内部字段：

	{
	    index：      //提示按钮在列表中的下标，数字类型
	    eventType：  //事件类型，取值范围如下：
                      open： //打开提示面板事件
                      close： //关闭提示面板事件
                      click： //点击提示面板内按钮事件
	}

##示例代码

	var obj = api.require('hintChatBox');
	obj.setHintButtonListener (function(ret,err){
		api.alert({msg:ret.index});
	});

##补充说明

配合open接口的leftButton参数使用

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setAddView**<div id="4"></div>

设置刷新添加按钮面板上的按钮

setAddView({params})

##params

addButtons：


- 类型：数组
- 默认值：无
- 描述：（可选项）添加界面的按钮信息
- 备注：不传则不刷新
- 内部字段：

```js
	[{
		normal:             //常态按钮背景图片，可为空，默认绿色面板
		highlight:           //高亮按钮背景图片，可为空，默认暗色
		title:               //按钮标题，可为空，默认无
		titleSize:            //标题大小，可为空，默认10
		titleColor:           //标题颜色，可为空，默认#a3a3a3
	}]
```

##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.setAddView();
```

##补充说明

配合open接口使用

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setInputFieldListener**<div id="5"></div>

设置输入框监听

setInputFieldListener(callBack())

##callBack(ret,err)

ret：

- 类型：JSON对象
- 内部字段：

```js
	{
		 eventType:    //输入框弹动事件，取值范围见输入框弹动事件类型
	     inputFieldH： //输入框的高度，数字类型
		 chatViewH：   //输入框下边缘距离屏幕底边的高度，数字类型
	}
```
##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.setInputFieldListener(function(ret,err){
		api.alert({msg:ret.eventType+'*'+ret.h});
	});
```

##补充说明

配合open接口使用

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="6"></div>

关闭聊天输入框

close()

##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.close();
```

##补充说明

关闭聊天输入框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="7"></div>

显示聊天输入框

show()

##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.show();
```

##补充说明

显示聊天输入框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="8"></div>

隐藏聊天输入框

hide()

##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.hide();
```

##补充说明

隐藏聊天输入框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**becomeFirstResponder**<div id="9"></div>

弹出键盘

becomeFirstResponder(callBack(ret,err))

##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.becomeFirstResponder(function(ret, err){

    });
```
ret：

- 类型：JSON对象
- 内部字段：

```js
	{
		status:           //操作状态码
	}
```
##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本


#**resignFirstResponder**<div id="10"></div>

隐藏键盘

resignFirstResponder(callBack(ret,err))

##示例代码

	var obj = api.require('hintChatBox');
	obj.resignFirstResponder(function(ret, err){

    });

ret：

- 类型：JSON对象
- 内部字段：

```js
	{
		status:           //操作状态码
	}
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**setMsg**<div id="11"></div>

设置输入框内的文字

setMsg({parmas},callback(ret, err))

#params

msg:

- 类型：字符串
- 默认值：空字符串
- 描述：(可选项)要设置的输入框内的文字内容

#callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
	{
		status:           //布尔类型，操作是否成功状态值
	}
```

##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.setMsg({
	msg:"设置的文字"
	 },function(ret,err){
	    if(ret.status){
	      api.alert({msg:"设置成功"});
	    }
	});
```

##补充说明

设置输入框内的文字

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**getMsg**<div id="12"></div>

获取当前输入框内的文字

getMsg(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
	{
		msg:           // 字符串类型，获取到的当前输入框内的文字
	}
```

##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.getMsg(function(ret,err){
	    if(ret.status){
	      api.alert({msg:ret.msg });
	    }
	});
```

##补充说明

获取当前输入框内的文字

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**configMsg**<div id="13"></div>

配置当前输入框内的文字

configMsg(params,callback(ret, err))

##params

msg:

- 类型：字符串
- 默认值：无
- 描述：(可选项)要设置的输入框内的文字内容

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
     status:           // 布尔类型，操作是否成功状态值
	 msg:              // 字符串类型，获取到的当前输入框内的文字
}
```

##示例代码

```js
var obj = api.require('hintChatBox');
obj.configMsg(function(ret,err){
    if(ret.status){
      api.alert({msg:ret.msg });
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**insertMsg**<div id="14"></div>

向当前输入框内指定位置插入字符串

insertMsg(params,callback(ret, err))

##params

index:

- 类型：数字
- 默认值：当前输入框内字符串的长度
- 描述：(可选项)插入当前输入框内字符串的位置

msg:

- 类型：字符串
- 默认值：空字符串
- 描述：(可选项)要插入到输入框内的文字内容

##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.insertMsg({
	   msg:'这里是插入的字符串'
	});
```

##补充说明

无

##可用性

iOS系统，Android系统
可提供的1.0.2及更高版本

#**setHintView**<div id="15"></div>

设置刷新提示语面板内容

setHintView({params})

##params

hint：

- 类型：json对象
- 默认值：无
- 描述：（可选项）输入框左边按钮刷新
- 备注：不传或传空则不刷新提示面板内容
- 内部字段：

```js
{               //（快捷文字提示面板设置
   bg：          //（可选项）面板背景设置，支持rgb，rgba，#，img，默认白色
   buttons：[{   //提示面板导航按钮组成的数组
     normal:    //（可选项）按钮常态下的背景图片
     selected:  //（可选项）点击后背景图片，
   }]
   hints：[{    //快捷提示文面板设置，数组对象，与buttons对应
      size：    //（可选项）快捷文字大小，默认12
      color:    //（可选项）快捷文字颜色，默认黑色，支持rgb，rgba，#
      contents: //快捷文字内容组成的数组，数组对象
      normal:   //快捷提示文字开头标注图标，支持widget，fs，等本地路径
      selected: //快捷提示文字开头选中标注图标，支持widget，fs,等本地路径
    }]
}
```

##示例代码

```js
	var obj = api.require('hintChatBox');
	obj.setHintView();
```

##补充说明

配合open接口使用

##可用性

iOS系统，Android系统
可提供的1.0.1及更高版本


#**setPlaceholder**<div id="16"></div>

设置占位提示文字

setPlaceholder({params})

##params

placeholder：

- 类型：字符串
- 默认值：空
- 描述：（可选项）占位提示文字
- 备注：若不传或传空则表示清空占位提示文字

##示例代码

```js
var obj = api.require('hintChatBox');
obj. setPlaceholder({
   placeholder:'我是占位提示文字'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

</div>

<div id="const-content">

<div class="outline">

[输入框弹动事件类型](#1)

</div>

#**输入框弹动事件类型**<div id="1"></div>

输入框弹动事件类型。字符串类型

##取值范围：

- move		    //输入框弹动事件
- change		//输入框高度改变事件


</div>