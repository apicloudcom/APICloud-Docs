/*
Title: ttsModule
Description: ttsModule
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[initTts](#a1)

[speakTts](#a2)

[closeTts](#a3)
</div>

#**概述**

ttsModule封装了android的本地TTS语音合成模块，使用此模块可轻松实现对文本转换为语音（UK/US）的功能


#**initTts**<div id="a1"></div>

初始化TTS

initTts({params}, callback(ret, err))

##params



language：

- 类型：数字
- 默认值：无
- 描述：不能为空，语言种类，可选填0(UK),1(US)

str：

- 类型：字符串
- 默认值：无
- 描述：不能为空，语音读取字符串

speechRate：

- 类型：数字
- 默认值：无
- 描述：不能为空，发音速度

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	state:		//该TTS是否可用
	
}
```

##示例代码

```js
var ttsModule = api.require('ttsModule');
ttsModule.initTts({
	language: 0,
	str: 'Hello ,welcome to Beijing!',
	speechRate: 0.8
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

#**speakTts**<div id="a2"></div>

读出文本


speakTts()




##示例代码

```js
var ttsModule = api.require('ttsModule');
ttsModule.speakTts();
```

##补充说明

无

##可用性

Android系统

可提供的1.0.

#**closeTts**<div id="a3"></div>

关闭TTS


closeTts()




##示例代码

```js
var ttsModule = api.require('ttsModule');
ttsModule.closeTts();
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


