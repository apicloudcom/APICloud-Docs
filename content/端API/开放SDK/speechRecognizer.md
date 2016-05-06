/*
Title: speechRecognizer
Description: speechRecognizer
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[record](#1)

[stopRecord](#2)

[cancelRecord](#4)

[addRecordHUD](#5)

[showRecordHUD](#6)

[hideRecordHUD](#7)

[read](#8)

[stopRead](#9)

[pauseRead](#11)

[resumeRead](#13)
</div>

#**概述**

speechRecognizer模块封装了科大讯飞语音识别的sdk。开发者只需调用此模块即可实现语音识别、语音朗读的相关功能。省去了开发者去科大讯飞官网注册创建app的复杂流程

#**record**<div id="1"></div>

识别语音返回文字

record({params}, callback(ret, err))

##params

vadbos：

- 类型：数字
- 描述：（可选项）前断点时间（静音时间，即用户多长时间不说话做超时处理），范围是0-10000单位ms
- 默认值：5000

vadeos：

- 类型：数字
- 描述：（可选项）后断点时间（静音时间，即用户多长时间不说话做超时处理），单位ms，范围是0-10000
- 默认值：5000

rate：

- 类型：数字
- 描述：（可选项）采样率（支持16000，8000）
- 默认值：16000

asrptt：

- 类型：数字
- 描述：（可选项）返回的语句是否有标点符号，取值范围：0-无，1-有
- 默认值：1

audioPath：

- 类型：字符串
- 描述：（可选项）录制的音频文件保存路径（如fs://123.mp3,一定要加后缀名），不支持widget 协议
- 备注：若不传则不保存

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:true		//布尔类型；操作成功状态值，true|false
	wordStr：		//字符串类型；识别语音后的文字
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:           //字符串类型；返回的错误信息
}
```

##示例代码

```js
{
var speechRecognizer = api.require('speechRecognizer');
speechRecognizer.record({
  vadbos:5000,
  vadeos:5000,
  rate:16000,
  asrptt:1,
  audioPath:'fs://speechRecogniser/speech.mp3'
},function(ret,err){
	if(ret.status){
		api.alert({msg:ret.wordStr});
	} else {
		api.alert({msg:err.msg});
    }
});
}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopRecord**<div id="2"></div>

停止录音

stopRecord()

##示例代码

```js
{
    var speechRecognizer = api.require('speechRecognizer');
    speechRecognizer.stopRecord();
}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**cancelRecord**<div id="4"></div>

取消语音识别

cancelRecord()

##示例代码

 ```js
 {
   var speechRecognizer = api.require('speechRecognizer');
   speechRecognizer.cancelRecord();
 }
 ```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addRecordHUD**<div id="5"></div>

添加录音音量显示器

addRecordHUD({params}, callBack(ret, err))

##params

centerX：

- 类型：数字
- 描述：（可选项）录音音量标识的圆心坐标
- 默认值：当前设备屏幕的宽的一半

centerY：

- 类型：数字
- 描述：（可选项）录音音量标识的圆心坐标
- 默认值：100

radius：

- 类型：数字
- 描述：（可选项）录音音量标识的圆心半径
- 默认值：60

transparentR：

- 类型：数字
- 描述：（可选项）中间透明区域的半径
- 默认值：radius的1/2

bg：

- 类型：字符串
- 描述：（可选项）录音标识的背景色，支持 rgb，rgba，#
- 默认值：#AAAAAA

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    volume:		//数字类型；录音音量大小
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg:       //字符串类型；返回错误信息
}
```
##示例代码

```js
{
    var speechRecognizer = api.require('speechRecognizer');
    speechRecognizer.addRecordHUD({
		centerX: 160,
		centerY: 120,
		radius: 80,
		transparentR：40,
		bg: '#AAAAAA',
		fixedOn: api.frameName,
		fixed: false
    },function(ret,err){
        var volume = ret.volume;
    });
}
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**showRecordHUD**<div id="6"></div>

显示录音音量显示器

showRecordHUD()

##示例代码

```js
{
    var speechRecognizer = api.require('speechRecognizer');
    speechRecognizer.showRecordHUD();
}
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**hideRecordHUD**<div id="7"></div>

隐藏录音音量显示器

hideRecordHUD()

##示例代码

```js
{
    var speechRecognizer = api.require('speechRecognizer');
    speechRecognizer.hideRecordHUD();
}
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**read**<div id="8"></div>

用语音读取文字信息，**最大的字节数为1k**

read({params}, callback(ret, err))

##params

readStr：

- 类型：字符串
- 描述：要读取的文字信息

speed：

- 类型：数字
- 描述：（可选项）朗读的语速，范围是0-100
- 默认值：60

volume：

- 类型：数字
- 描述：（可选项）朗读的声音大小，范围是0-100
- 默认值：60

voice：

- 类型：数字
- 描述：（可选项）朗读人0-xiaoli；1-xiaoyu
- 默认值：0

rate：

- 类型：数字
- 描述：（可选项）采样率(支持16000，8000)
- 默认值：16000

audioPath：

- 类型：字符串
- 描述：（可选项）朗读的音频保存路径（如fs://123.mp3,一定要加后缀名），不支持widget 协议
- 备注：若不传则不保存

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:               //布尔类型；操作成功状态值，true|false
	speakProgress：       //数字类型；朗读的进度
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:                 //字符串类型；返回错误信息
}
```

##示例代码

```js
var speechRecognizer = api.require('speechRecognizer');
speechRecognizer.read({
	readStr: 'APICloud平台',
	speed: 60,
	volume: 60,
	voice: 1,
	rate: 16000,
	audioPath:'fs://speechRecogniser/read.mp3'
},function(ret,err) {
	if(ret.status) {
		ret.speakProgress
	} else {
		api.alert({msg:err.msg});
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopRead**<div id="9"></div>

停止朗读

stopReead()

##示例代码

```js
{
    var speechRecognizer = api.require('speechRecognizer');
    speechRecognizer.stopRead();
}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**pauseRead**<div id="11"></div>

暂停朗读（用 resumeRead 接口恢复朗读）

pauseRead()

##示例代码

```js
{
    var speechRecognizer = api.require('speechRecognizer');
    speechRecognizer.pauseRead();
}
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**resumeRead**<div id="13"></div>

恢复朗读

resumeRead()

##示例代码

```js
{
    var speechRecognizer = api.require('speechRecognizer');
    speechRecognizer.resumeRead();
}
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
