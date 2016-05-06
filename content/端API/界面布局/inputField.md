/*
Title: inputField
Description: inputField
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

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

inputField 是一个输入框，开发者可根据需求自定义其样式。该模块能巧妙的适配键盘高度，自定调整位置，始终紧贴软键盘

![图片说明](/img/docImage/inputField.jpg)

#**open**<div id="1"></div>

打开输入框

open({parmas}, callback(ret, err))

##params

bgColor:

- 类型：字符串
- 描述：（可选项）输入视图背景色设置，支持 rgba、rgb、#
- 默认值：#696969

lineColor:

- 类型：字符串
- 描述：（可选项）输入框视图最上边的分割线色设置，支持 rgba、rgb、#
- 默认值：#000

borderColor:

- 类型：字符串
- 描述：（可选项）输入框边框色设置，支持 rgba、rgb、#
- 默认值：#ff0000

fileBgColor:

- 类型：字符串
- 描述：（可选项）输入框背景色设置，支持 rgba、rgb、#
- 默认值：#fff

sendImg:

- 类型：字符串
- 描述：发送按钮的背景图片，**要求50-40大小的图片（宽-高）**

sendImgHighlight：

- 类型：字符串
- 描述：（可选项）发送按钮的高亮背景图片，**要求50-40大小的图片（宽-高）**

maxLines：

- 类型：数字
- 描述：（可选项）输入框高度自适应输入的文字行数的最大限高值
- 备注：若不传则高度不自适应

placeholder：

- 类型：字符串
- 描述：（可选项）输入框的提示文字
- 备注：若不传则不显示占位提示文字

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:           //字符串类型；返回输入的文字
}
```

##示例代码

```js
var inputField = api.require('inputField');
inputField.open({
	bgColor:'#708090',
	lineColor:'#C71585',
	fileBgColor:'#90EE90',
	borderColor:'#FFB6C1',
	sendImg:'widget://res/img/sendImg.png',
	fixedOn: api.frameName
}, function(ret, err){   
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setInputFieldListener**<div id="11"></div>

设置输入框监听

setInputFieldListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	 eventType:        //字符串类型；输入框弹动事件，取值范围如下：
                       //move：输入框弹动事件
                       //change	：输入框高度改变事件
     inputFieldH：     //数字类型；输入框的高度
     chatViewH：       //数字类型；输入框下边缘距离屏幕底边的高度

}
```

##示例代码

```js
var inputField = api.require('inputField');
inputField.setInputFieldListener(function(ret, err){    
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**close**<div id="2"></div>

关闭输入框

close(callback(ret, err));

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:           //布尔类型；操作状态码，true|false
}
```

##示例代码

```js
var inputField = api.require('inputField');
inputField.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="4"></div>

隐藏输入框，并没有从内存里清除

hide(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:          //布尔类型；操作状态码，true|false
}
```

##示例代码

```js
var inputField = api.require('inputField');
inputField.hide(function(ret, err){   
  if( ret ){
      alert( JSON.stringify( ret ) );
  }else{
      alert( JSON.stringify( err ) );
  }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**show**<div id="3"></div>

显示输入框

show(callback(ret, err));

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:           //布尔类型；操作状态码，true|false
}
```

##示例代码

```js
var inputField = api.require('inputField');
inputField.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**becomeFirstResponder**<div id="5"></div>

弹出键盘

becomeFirstResponder(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:          //布尔类型；操作状态码，true|false
}
```

##示例代码

```js
var inputField = api.require('inputField');
inputField.becomeFirstResponder(function(ret, err){   
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**resignFirstResponder**<div id="6"></div>

隐藏键盘

resignFirstResponder(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:         //布尔类型；操作状态码，true|false
}
```

##示例代码

```js
var inputField = api.require('inputField');
inputField.resignFirstResponder();
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**setMsg**<div id="7"></div>

设置输入框内的文字

setMsg({params},callback( ret, err))

##params

msg：

- 类型：字符串
- 描述：（可选项）要设置的输入框内的文字内容
- 默认值：空字符串

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status:          //布尔类型；操作状态码，true|false
}
```
##示例代码

```js
var inputField = api.require('inputField');
inputField.setMsg({
    msg:'设置的文字'
}, function(ret, err){   
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**getMsg**<div id="8"></div>

获取当前输入框内的文字

setMsg(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg:           // 字符串类型，获取到的当前输入框内的文字
}
```
##示例代码

```js
var inputField = api.require('inputField');
inputField.getMsg(function(ret, err){   
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**configMsg**<div id="9"></div>

配置当前输入框内的文字

configMsg({params}, callback(ret, err))

##params

msg：

- 类型：字符串
- 描述：（可选项）要设置的输入框内的文字内容
- 备注：若不传则此接口 callBack 当前值

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
        status:           // 布尔类型；操作是否成功状态值
        msg:              // 字符串类型；获取到的当前输入框内的文字
}
```
##示例代码

```js
var inputField = api.require('inputField');
inputField.configMsg(function(ret, err){    
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本

#**insertMsg**<div id="10"></div>

向当前输入框内指定位置插入字符串

insertMsg({params})

##params

index：

- 类型：数字
- 描述：（可选项）插入当前输入框内字符串的位置
- 默认值：当前输入框内字符串的长度

msg：

- 类型：字符串
- 描述：（可选项）要设置的输入框内的文字内容
- 默认值：空字符串

##示例代码

```js
var inputField = api.require('inputField');
inputField.insertMsg({
   msg:'这里是插入的字符串'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本


#**setPlaceholder**<div id="11"></div>

设置占位提示文字

setPlaceholder({params})

##params

placeholder：

- 类型：字符串
- 描述：（可选项）占位提示文字
- 备注：若不传或传空则表示清空占位提示文字

##示例代码

```js
var inputField = api.require('inputField');
inputField.setPlaceholder({
   placeholder:'我是占位提示文字'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.2及更高版本
