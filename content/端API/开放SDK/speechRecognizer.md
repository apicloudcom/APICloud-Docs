/*
Title: speechRecognizer
Description: speechRecognizer
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[record](#1)

[stopRecord](#2)

[cancel](#3)

[cancelRecord](#4)

[addRecordHUD](#5)

[showRecordHUD](#6)

[hideRecordHUD](#7)

[read](#8)

[stopRead](#9)

[pause](#10)

[pauseRead](#11)

[resume](#12)

[resumeRead](#13)
</div>

#**概述**

speechRecognizer模块封装了科大讯飞语音识别的sdk。开发者只需调用此模块即可实现语音识别，语音朗读的相关功能。省去了开发者去科大讯飞官网注册创建app的复杂流程

#**record**<div id="1"></div>

识别语音返回文字

record({params},callback(ret, err))

##params

vadbos：

- 类型：数字
- 默认值：5000
- 描述：前断点时间（静音时间，即用户多长时间不说话做超时处理），范围是0-10000单位ms，可为空

vadeos：

- 类型：数字
- 默认值：5000
- 描述：后断点时间（静音时间，即用户多长时间不说话做超时处理），单位ms，范围是0-10000，可为空

rate：

- 类型：数字
- 默认值：16000
- 描述：采样率（支持16000，8000），可为空

asrptt：

- 类型：数字
- 默认值：1
- 描述：返回的语句是否有标点符号，0-无，1-有，可为空

audioPath：

- 类型：字符串
- 默认值：无
- 描述：录制的音频文件保存路径（如fs://123.mp3,一定要价后缀名），若为空则不保存。可空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true		//操作成功状态值
	wordStr：		//识别语音后的文字
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:           //错误码
}
```

##示例代码

```js
var obj = api.require('speechRecognizer');
obj.record({
},function(ret,err){
	if(ret.status){
		ret.wordStr;
	}else{
		err.msg;
    }
});
```

##补充说明

语音识别

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopRecord**<div id="2"></div>

停止录音

stopRecord()

##示例代码

    var obj = api.require('speechRecognizer');
    obj.stopRecord();

##补充说明

停止录音

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<del>#**cancel**<div id="3"></div></del>

<del>取消语音识别</del>

<del>cancel()</del>

<del>##补充说明</del>

<del>取消语音识别</del>

<del>##可用性</del>

<del>iOS系统，Android系统</del>

<del>可提供的1.0.0及更高版本</del>


#**cancelRecord**<div id="4"></div>

取消语音识别

cancelRecord()

##示例代码

     var obj = api.require('speechRecognizer');
     obj.cancelRecord();

##补充说明

取消语音识别

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addRecordHUD**<div id="5"></div>

添加录音音量显示器

addRecordHUD(params,callBack(ret,err))

##params

centerX：

- 类型：数字
- 默认值：当前设备屏幕的宽的一半
- 描述：录音音量标识的圆心坐标，可为空

centerY：

- 类型：数字
- 默认值：100
- 描述：录音音量标识的圆心坐标，可为空

radius：

- 类型：数字
- 默认值：60
- 描述：录音音量标识的圆心半径，可为空

transparentR：

- 类型：数字
- 默认值：radius的1/2
- 描述：中间透明区域的半径，可为空

bg：

- 类型：字符串
- 默认值：#AAAAAA
- 描述：录音标识的背景色，支持rgb，rgba，#，可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口
- 描述：录音标识视图固定到指定窗口的名字，可为空

fixed:
- 类型：布尔
- 默认值：true
- 描述：是否将模块视图固定到窗口上，不跟随窗口上下滚动，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    volume:		//录音音量大小，数字类型
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:           //错误码
}
```
##示例代码

    var obj = api.require('speechRecognizer');
    obj.addRecordHUD(function(ret,err){
        var volume = ret.volume;
    });


##补充说明

录音音量识别标识

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**showRecordHUD**<div id="6"></div>

显示录音音量显示器

showRecordHUD()

##示例代码

    var obj = api.require('speechRecognizer');
    obj.showRecordHUD();

##补充说明

显示录音音量识别标识

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**hideRecordHUD**<div id="7"></div>

隐藏录音音量显示器

hideRecordHUD()

##示例代码

    var obj = api.require('speechRecognizer');
    obj.hideRecordHUD();

##补充说明

隐藏录音音量识别标识

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


#**read**<div id="8"></div>

用语音读取文字信息

read({params}, callback(ret, err))

##params

readStr：

- 类型：字符串
- 默认值：无
- 描述：要读取的文字信息，不能为空

speed：

- 类型：数字
- 默认值：60
- 描述：朗读的语速，范围是0-100，可为空

volume：

- 类型：数字
- 默认值：60
- 描述：朗读的声音大小，范围是0-100，可为空

voice：

- 类型：数字
- 默认值：0
- 描述：朗读人0-xiaoli；1-xiaoyu，可为空

rate：

- 类型：数字
- 默认值：16000
- 描述：采样率(支持16000，8000)，可为空

audioPath：

- 类型：字符串
- 默认值：无
- 描述：朗读的音频保存路径（如fs://123.mp3,一定要加后缀名），若为空则不保存

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:               //操作成功状态值
	speakProgress：       //朗读的进度
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:           //错误码
}
```

##示例代码

```js
var obj = api.require('speechRecognizer');
obj.read({
	readStr:'hello，北京'
},function(ret,err) {
	if(ret.status) {
		ret.speakProgress
	}else{
		err.msg
	}
});
```

##补充说明

语音读文字

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopRead**<div id="9"></div>

停止朗读

stopReead()

##示例代码

    var obj = api.require('speechRecognizer');
    obj.stopRead();

##补充说明

停止朗读

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<del>#**pause**<div id="10"></div></del>

<del>暂停朗读</del>

<del>pause()</del>

<del>##补充说明</del>

<del>暂停朗读</del>

<del>##可用性</del>

<del>iOS系统，Android系统</del>

<del>可提供的1.0.0及更高版本</del>

#**pauseRead**<div id="11"></div>

暂停朗读

pauseRead()

##示例代码

    var obj = api.require('speechRecognizer');
    obj.pauseRead();

##补充说明

暂停朗读

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本


<del>#**resume**<div id="12"></div></del>

<del>恢复朗读</del>

<del>resume()</del>

<del>##补充说明</del>

<del>恢复朗读</del>

<del>##可用性</del>

<del>iOS系统，Android系统</del>

<del>可提供的1.0.0及更高版本</del>

#**resumeRead**<div id="13"></div>

恢复朗读

resumeRead()

##示例代码

    var obj = api.require('speechRecognizer');
    obj.resumeRead();

##补充说明

恢复朗读

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本
