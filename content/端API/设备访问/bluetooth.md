/*
Title: bluetooth
Description: bluetooth
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[connect](#1)

[send](#2)

[cancel](#3)
</div>

#**概述**

bluetooth 模块封装了系统的蓝牙功能，使用此模块可实现两台设备间无缝传输数据。可传输字符串、图片、视频、文件等各种数据。使用此模块需打开设备蓝牙功能

#**connect**<div id="1"></div>

打开蓝牙连接

connect(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	progress:	//发送接收数据时的进度
	message：	//收到的数据信息，如果是字符串则直接显示，如果是文件则返回其路径
}
```

##示例代码

```js
var bluetooth = api.require('bluetooth');
bluetooth.connect(function( ret, err ){
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

打开蓝牙并连接

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**send**<div id="2"></div>

发送数据

send({params})

##params

type：

- 类型：数字
- 默认值：无
- 描述：要发送的数据类型：0—字符串；1---文件；2----本地相册里的图片；3-----本地视频库里的视频。不能为空

data：
- 类型：字符串
- 默认值：无
- 描述：要发送的数据，不可为空

##示例代码

```js
var bluetooth = api.require('bluetooth');
bluetooth.send({
    type: 0,
    data: 'bluetooth send string test'
});
```

##补充说明

发送数据

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**cancel**<div id="3"></div>

取消蓝牙连接

cancel()

##示例代码

```js
var bluetooth = api.require('bluetooth');
bluetooth.cancel();
```

##补充说明

断开蓝牙连接

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
