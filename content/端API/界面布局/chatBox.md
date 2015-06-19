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

[setRecordButtonListener](#11)

[setInputFieldListener](#12)

[close](#2)

[show](#3)

[hide](#4)

[becomeFirstResponder](#5)

[resignFirstResponder](#6)

[setMsg](#7)

[getMsg](#8)

[configMsg](#9)

[insertMsg](#10)

[setPlaceholder](#13)
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
- 描述：（可选项）输入视图背景色的十六进制值，支持rgb，rgba，#

lineColor:

- 类型：字符串
- 默认值：#d9d9d9
- 描述：（可选项）输入框视图最上边的分割线色的十六进制值，支持rgb，rgba，#

borderColor:

- 类型：字符串
- 默认值：#B3B3B3
- 描述：（可选项）输入框边框色的十六进制值，支持rgb，rgba，#

fileBgColor:

- 类型：字符串
- 默认值：#FFFFFF
- 描述：（可选项）输入框背景色的十六进制值，支持rgb，rgba，#

switchButton:

- 类型：json对象
- 默认值：无
- 描述：表情键盘加号的按钮图片
- 内部字段：

```js
{
	faceNormal:           	// 表情按钮背景图片路径，默认纯绿色
	faceHighlight:          //表情按钮高亮图片路径
	addNormal:           	//（可选项）添加按钮背景图片路径，若不传则不显示右边添加按钮
	addHighlight:          	//（可选项）添加按钮高亮图片路径，若不传则无高亮状态
	keyboardNormal:      	//键盘按钮背景图片路径，默认纯绿色
	keyboardHighlight:    	//键盘按钮高亮图片路径
}
```

sourcePath：

- 类型：字符串
- 默认值:无
- 描述：自定义表情源文件(.json的文件和图片表情集文件同名且在同一路径下)的路径，json文件格式如下：[{name:’Expression_1’,text:’[微笑]’}]

addButtons：

- 类型：数组
- 默认值：无
- 描述：（可选项）添加界面的按钮信息
- 备注：若switchButton内addNormal不传则此参数可不传且不显示右边添加按钮
- 内部字段：

```js
[{
	normal:              //（可选项）常态按钮背景图片，默认绿色面板
	highlight:           //（可选项）高亮按钮背景图片，默认暗色
	title:               //（可选项）按钮标题，默认无
	titleSize:           //（可选项）标题大小，默认10
	titleColor:          //（可选项）标题颜色，默认#a3a3a3
}]
```

pageControl：

- 类型：json对象
- 默认值：参见内部字段
- 描述：（可选项）表情和添加界面的页面控制器配置
- 备注：若不传则不显示页面控制器
- 内部字段：

```js
{
        normalColor:        //（可选项）常态色，字符串，默认#c4c4c4
        highlightColor:     //（可选项）选中色，字符串，默认#9e9e9e
}
```

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：（可选项）将此模块视图添加到指定窗口的名字

placeholder：

- 类型：字符串
- 默认值：无
- 描述：（可选项）输入框的占位提示文字
- 备注：不传则不显示提示文字

maxLines：

- 类型：数字
- 默认值：4
- 描述：（可选项）输入框高度自适应输入的文字行数的最大限高值

leftButton：

- 类型：json对象
- 默认值：无
- 描述：（可选项）输入框左边按钮设置
- 备注：不传则不显示左边按钮
- 内部字段：

```js
{
        normal:               //左边按钮背景图片,支持widget等本地协议
        selected:             //左边按钮选中后背景图片,支持widget等本地协议
        record:{              //录音按钮设置 
            normal:           //（可选项）按钮常态背景图片,支持rgb，rgba，#，img,默认#c4c4c4
            highlight:        //（可选项）钮按下时背景图片,支持rgb，rgba，#，img,默认#999999,若normal为颜色值则highlight不支持img，若normal为img则highlight不支持色值，normal和highlight应保持一致，若为颜色值则必须同为颜色值，若为img则同为img
            normalTitle：     //（可选项）按钮常态时的标题，默认'按住 说话'
            highlightTitle：  //（可选项）按钮按下时的标题，默认'松开 结束'
            titleColor：      //（可选项）按钮标题文字的颜色，支持rgb，rgba，#，默认#000000
            titleSize：       //（可选项）按钮标题文字的大小，数字类型，默认14
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
                          addBtn：  //用户点击右边加号按钮事件的回调，如果open时传了addButtons参数才有次类型的回调
                          faceBtn： //用户点击表情按钮事件的回调
                          leftBtn： //用户点击左边按钮事件的回调
                          addBoard：//用户点击添加面板内按钮的事件的回调
    click:           //是否是点击事件的回调，布尔类型 deprecated
    index:           //若eventType为addBoard（或者click为true），则此参数为用户点击按钮的下标，否则undefined
    msg:             //返回输入的文字
}
```
##示例代码

```js
var addButtonAry = [];
	for (var i = 0; i< 3; i++) {
		addButtonAry[i]={
			  normal:"widget://image/chatBox_album1.png",
            title:"相册"
        };
    }
var obj = api.require('chatBox');
obj.open({
	switchButton:{
        faceNormal : "widget://image/chatBox_face1.png",
        faceHighlight : "widget://image/chatBox_face1.png",
        addNormal : "widget://image/chatBox_add1.png",
        addHighlight : "widget://image/chatBox_add1.png",
        keyboardNormal : "widget://image/chatBox_key1.png",
        keyboardHighlight : "widget://image/chatBox_key1.png"
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

#**setRecordButtonListener**<div id="11"></div>

设置录音按钮监听

setRecordButtonListener(callBack(ret,err))

##callBack(ret,err)

ret：

- 类型：json对象
- 内部字段：

```js
{
 eventType:  //输入框左边按钮触发事件，取值范围如下：
                  touch_in		        //点击录音按钮下按事件
                  touch_cancel		    //点击录音按钮后松开事件
                  move_out		    //点击录音按钮后手指移出按钮的rect事件
                  move_out_cancel		//点击录音按钮后手指移出按钮的rect后松开事件
                  move_in             //move_out事件后手指重新移动进录音按钮的rect事件
}
```

##示例代码

```js
var obj = api.require('chatBox');
obj.setRecordButtonListener(function(ret,err){
    api.alert({msg:ret.eventType});
});

```

##补充说明

配合open接口内的leftButton参数使用，调用此接口必须在open内传leftButton参数，否则此接口无意义

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**setInputFieldListener**<div id="12"></div>

设置输入框监听

setInputFieldListener(callBack(ret,err))

##callBack(ret,err)

ret：
- 类型：json对象
- 内部字段：

```js
{
    inputFieldH：      //输入框的高度，数字类型
    chatViewH：       //输入框下边缘距离屏幕底边的高度，数字类型
    eventType:        //输入框弹动事件，取值范围如下：
                           move		    //输入框弹动事件
                           change		    //输入框高度改变事件
}
```

##示例代码

```js
var obj = api.require('chatBox');
obj.setInputFieldListener(function(ret,err){
   api.alert({msg:ret.eventType+'*'+ret.h});
});

```

##补充说明

配合open接口使用

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

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
- 内部字段：

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
- 描述：（可选项）要设置的输入框内的文字内容

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:           //操作状态码
}
```
##示例代码

```js
   var obj = api.require('chatBox');
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

#**getMsg**<div id="8"></div>

获取当前输入框内的文字

setMsg(callback(ret, err))

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
var obj = api.require('chatBox');
obj.getMsg(function(ret,err){
    api.alert({msg:ret.msg });
});
```

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
- 描述：（可选项）要设置的输入框内的文字内容
- 备注：若不传则callBack当前值

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
var obj = api.require('chatBox');
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

#**insertMsg**<div id="10"></div>

向当前输入框内指定位置插入字符串

insertMsg({params})

##params

index：

- 类型：数字
- 默认值：当前输入框内字符串的长度
- 描述：（可选项）插入当前输入框内字符串的位置

msg：

- 类型：字符串
- 默认值：空字符串
- 描述：（可选项）要设置的输入框内的文字内容

##示例代码

```js
var obj = api.require('chatBox');
obj.insertMsg({
   msg:'这里是插入的字符串'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**setPlaceholder**<div id="13"></div>

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