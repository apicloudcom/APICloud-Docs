/*
Title: uscSpeechRecognizer
Description: uscSpeechRecognizer
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[startRecord](#1)

[stopRecord](#2)

[cancelRecord](#3)

[play](#4)

[stopPlay](#5)
</div>

#**概述**

uscSpeechRecognizer模块封装了云知声语音识别的sdk，开发者只需调用此模块即可实现语音识别，语音合成，语义理解的相关功能，省去了开发者去云知声官网注册创建app的复杂流程。

暂 仅支持 Android. 

#**startRecord**<div id="1"></div>

开始语音识别，识别完成后返回识别文字

startRecord(params, callback)

##params

frontTime：

- 类型：数字
- 默认值：3000
- 描述：用户不说话超时时间，范围为2000~5000,单位ms，可以为空

backTime：

- 类型：数字
- 默认值：1000
- 描述：用户停止说话自动停止录音时间，范围为200~3000,单位ms，可以为空

rate：

- 类型：字符串
- 默认值：RATE_16K
- 描述：录音采样率，支持RATE_8K，RATE_16K，BANDWIDTH_AUTO，可以为空

domain：

- 类型：字符串
- 默认值：general
- 描述：录音采样率，支持general（通用识别），poi(地名识别)，song(歌名识别)，movietv(影视名识别)，medical (医药领域识别)，可以为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true		//操作成功状态值
	resultStr：		//识别语音后的文字
    nluStr:         //语义理解结果
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:           //错误信息
}
```

##示例代码

```js
var obj = api.require('uscSpeechRecognizer');obj.startRecord({},function(ret,err){    if(ret.status){        ret.resultStr;        ret.nluStr;    }else{        err.msg;    }});
```

##补充说明

解析语义理解结果请下载<<云知声语义云平台API规范文档>>
下载地址：[dev.hivoice.cn/download_file/USC_Semantic_Parsing_Service_Protocol.pdf](http://dev.hivoice.cn/download_file/USC_Semantic_Parsing_Service_Protocol.pdf)


##可用性

Android系统

可提供的1.0.1及更高版本


#**stopRecord**<div id="2"></div>

停止录音

stopRecord()

##示例代码

```
var obj = api.require('uscSpeechRecognizer');obj.stopRecord();
```

##补充说明

停止录音

##可用性

Android系统

可提供的1.0.1及更高版本


#**cancelRecord**<div id="3"></div>

取消本次语音识别

cancelRecord()

##示例代码

```
var obj = api.require('speechRecognizer');
obj.cancelRecord();
```

##补充说明

取消语音识别

##可用性

Android系统

可提供的1.0.1及更高版本


#**play**<div id="4"></div>

播放合成的文字

play(params, callback)

##params

text：

- 类型：字符串
- 默认值：北京云知声信息技术有限公司
- 描述：需要合成的文字，可以为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    status: true		//操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:           //错误信息
}
```
##示例代码

```
var obj = api.require('uscSpeechRecognizer');obj.play({    text:'北京云知声信息技术有限公司'},function(ret,err) {    if(ret.status) {    }else{        err.msg    }});
```


##补充说明

无

##可用性

Android系统

可提供的1.0.1及更高版本


#**stopPlay**<div id="5"></div>

停止播放

stopPlay()

##示例代码

```
var obj = api.require('uscSpeechRecognizer');obj.stopPlay();
```

##补充说明

无

##可用性

Android系统

可提供的1.0.1及更高版本
