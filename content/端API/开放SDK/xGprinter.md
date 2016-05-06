/*
Title: xGprinter
Description: xGprinter
*/
<div class="outline">
[connect](#a1)

[printTest](#a2)

[printMultipleText](#a3)

[printImage](#a4)

[getStatus](#a5)
</div>

#**概述**

xGprinter装了佳博官方2.1.4版SDK，可通过蓝牙、usb、网口连接打印机，并支持自定义数据打印。
    
<div id="a1"></div>
#**connect**

连接打印机

connect()

##示例代码

```js
var gprinter = api.require('xGprinter');
gprinter.connect();
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

<div id="a2"></div>
#**printTest**

打印测试页

printTest()

##示例代码

```js
var gprinter = api.require('xGprinter');
gprinter.printTest();
```

##可用性

Android系统

可提供的1.0.0及更高版本

<div id="a3"></div>
#**printMultipleText**

打印自定义数据（多行文本）

printMultipleText({params}, callback(ret, err))

##params

project：

- 类型：数组
- 描述：（必填项）打印联式名称。

title：

- 类型：字符串
- 描述：（必填项）票据抬头
- 默认值：''

rows：

- 类型：数组
- 描述：（必填项）票据每行内容及样式。
- 示例：{text : '内容', style : [0,0,0,0], align:'left|center|right', lineHeight:60}
- 说明：
style 每个元素对应打印样式标志位，分别是：[是否加粗,是否倍高,是否倍宽,是否下划线]
align 对齐方式，分别是：left 左对齐, center 居中对齐, right 右对齐
lineHeight 行间距

isSubject:

- 类型：布尔
- 描述：（必填项）是否需要打印联式名称。
- 取值范围：true|false

##示例代码

```js
var gprinter = api.require('xGprinter');
gprinter.printMultipleText({
	title : '自定义数据',
	project : ['联1','联2'],
	rows : [{
		text : '内容1',
        style : [0,0,1,0,1], //不加粗,不倍高,倍宽,不采用下划线,使用
        align : 'center',
        lineHeight : 60,
        image : '图片base64编码' //当text为空时使用image
	}],
	isSubject : true
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

<div id="a4"></div>
#**printImage**

打印自定义数据（打印图片）

printImage({params}, callback(ret, err))

##params

base64:

- 类型：字符串
- 描述：（必填项）图片base64编码，注意去掉头信息。

##示例代码

```js
var gprinter = api.require('xGprinter');
gprinter.printImage({
	base64 : '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'
});
```

<div id="a5"></div>
#**getStatus**

获取打印机连接状态

getStatus(callback)

##callback

ret:

- 类型：JSON
- 描述：返回打印机状态

##示例代码

```js
var gprinter = api.require('xGprinter');
gprinter.getStatus(function(ret){
	alert(JSON.stringify(ret));
});
```

##补充说明

如果使用蓝牙连接方式，需手机打开蓝牙。目前只支持android系统。

##可用性

Android系统

可提供的1.0.0及更高版本
