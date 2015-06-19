/*
Title: inputField
Description: inputField
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setInputFieldListener](#11)

[close](#2)

[show](#3)

[hide](#4)

[becomeFirstResponder](#5)

[resignFirstResponder](#6)

[setMsg](#7)

[getMsg](#8)

[configMsg](#9)

[insertMsg](#10)

[setPlaceholder](#11)
</div>

#**概述**

inputField是一个输入框，开发者可根据需求自定义其样式。该模块能巧妙的适配键盘高度，自定调整位置，始终紧贴软键盘

![图片说明](/img/docImage/inputField.jpg)

#**open**<div id="1"></div>

打开输入框

open({parmas},callback(ret, err))

##params

bgColor:

- 类型：字符串
- 默认值：灰色
- 描述：（可选项）输入视图背景色设置,支持rgba，rgb，#

lineColor:

- 类型：字符串
- 默认值：黑色
- 描述：（可选项）输入框视图最上边的分割线色设置,支持rgba，rgb，#

borderColor:

- 类型：字符串
- 默认值：红色
- 描述：（可选项）输入框边框色设置,支持rgba，rgb，#

fileBgColor:

- 类型：字符串
- 默认值：白色
- 描述：（可选项）输入框背景色设置，支持rgba，rgb，#

sendImg:

- 类型：字符串
- 默认值：无
- 描述：发送按钮的背景图片

sendImgHighlight：

- 类型：字符串
- 默认值：无
- 描述：（可选项）发送按钮的高亮背景图片

fixedOn：

- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：（可选项）将此模块视图添加到指定窗口的名字

maxLines：

- 类型：数字
- 默认值：无
- 描述：（可选项）输入框高度自适应输入的文字行数的最大限高值
- 备注：若不传空则高度不自适应

placeholder：

- 类型：字符串
- 默认值：无
- 描述：（可选项）输入框的提示文字
- 备注：若不传则不显示占位提示文字

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:           //返回输入的文字
}
```

##示例代码

```js
var obj = api.require('inputField');
obj.open({
	bgColor:'#708090',
	lineColor:'#C71585',
	fileBgColor:'#90EE90',
	borderColor:'#FFB6C1',
	sendImg:'widget://res/sendImg.png'
},function(ret,err) {
	api.alert({title: '输入的内容', msg: ret.msg});
});
```

##补充说明

打开输入框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setInputFieldListener**<div id="11"></div>

设置输入框监听

setInputFieldListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	 eventType:        //输入框弹动事件，取值范围如下：
                          move		    //输入框弹动事件
                          change	    //输入框高度改变事件
     inputFieldH：     //输入框的高度，数字类型
     chatViewH：       //输入框下边缘距离屏幕底边的高度，数字类型

}
```

##示例代码

```js
var inputField = api.require('inputField');

inputField.setInputFieldListener(function(ret,err){
    alert(JSON.stringify(ret) + JSON.stringify(err));
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**close**<div id="2"></div>

关闭输入框

close(callBack(ret,err));

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

    var obj = api.require('inputField');
    obj.close(function(ret,err){

    });

##补充说明

关闭输入框

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="4"></div>

隐藏输入框，并没有从内存里清除

hide(callBack(ret,err))

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

    var obj = api.require('inputField');
    obj.hide(function(ret,err){

    });

##补充说明

隐藏输入框

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**show**<div id="3"></div>

显示输入框

show(callBack(ret,err));

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

    var obj = api.require('inputField');
    obj.show(function(ret,err){

    });

##补充说明

显示已隐藏的输入框

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**becomeFirstResponder**<div id="5"></div>

弹出键盘

becomeFirstResponder(callBack(ret,err))

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

    var obj = api.require('inputField');
    obj.close(function(ret,err){

    });

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**resignFirstResponder**<div id="6"></div>

隐藏键盘

resignFirstResponder(callBack(ret,err))

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

    var obj = api.require('inputField');
    obj. resignFirstResponder ();

##补充说明

关闭输入框

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
   var obj = api.require('inputField');
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
var obj = api.require('inputField');
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
- 备注：若不传则此接口callBack当前值

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
var obj = api.require('inputField');
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
var obj = api.require('inputField');
obj.insertMsg({
   msg:'这里是插入的字符串'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本


#**setPlaceholder**<div id="11"></div>

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
var obj = api.require('inputField');
obj. setPlaceholder({
   placeholder:'我是占位提示文字'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本
