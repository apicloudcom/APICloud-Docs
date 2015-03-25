/*
Title: scanner
Description: scanner
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[openView](#2)

[closeView](#3)

[decode](#4)

[encode](#5)

[lightSwitch](#6)
</div>

#**概述**

二维码/条码扫描器，底层集成了ZXing，Zbar条码/二维码分析库，开发者可自定义扫描区域大小和位置、对图片解码，对字符串编码，将扫描结果保存到系统相册等功能，亦可自定义UI。开发者使用本模块可开发出各种自定义扫码应用

![图片说明](/img/docImage/scanner.jpg)

#**open**<div id="1"></div>

打开二维码/条码扫描器

open()

##params

needBr：

- 类型：布尔
- 默认值：false
- 描述：如果此值为true，则所扫二维码的信息字符串如果包含回车键(\n)则用<br>替换。false则直接将\n去掉。不传则默认为false，可为空

sound：

- 类型：字符串
- 默认值：无
- 描述：扫描结束后的提示音文件的路径，可为空

save：

- 类型：json对象
- 默认值：见内部字段
- 描述：所生成的图片保存位置，可为空


内部字段：

```js
{
	album:            //布尔值，是否保存到系统相册，默认false，可为空
	imgPath:          //保存的文件路径,字符串类型，无默认值,可为空,空则不保存若路径不存在文件夹则创建此目录
	imgName:          //保存的图片名字，字符串类型，无默认值,可为空,空则不保存支持png和jpg格式，若不指定格式，则默认png
	size:             //生成的图片(正方形)的边长，数字，默认200，可为空
}
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //返回扫描信息（扫码失败则返回失败信息）
}
```

##示例代码

```js
var obj = api.require('scanner');
obj.open(function(ret,err) {
	api.alert({
		title: '扫描结果', 
		msg: ret.msg
	});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**openView**<div id="2"></div>

打开自定义视图大小的二维码/条码扫描器

openView({params},callback(ret,err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：视图左上角点的坐标，可为空

y：

- 类型：数字
- 默认值：64
- 描述：视图左上角点的坐标，可为空


w：

- 类型：数字
- 默认值：200
- 描述：视图的宽，可为空


h：

- 类型：数字
- 默认值：200
- 描述：视图的高，可为空

needBr：

- 类型：布尔
- 默认值：false
- 描述：如果此值为true，则所扫二维码的信息字符串如果包含回车键(\n)则用<br>替换。false则直接将\n去掉。不传则默认为false，可为空

sound：

- 类型：字符串
- 默认值：无
- 描述：扫描结束后的提示音文件的路径，可为空

fixedOn：

- 类型：字符串
- 默认值：当前主窗口名字
- 描述：将模块视图添加到指定窗口的名字，可为空

save：

- 类型：json对象
- 默认值：见内部字段
- 描述：所生成的图片保存位置，可为空

内部字段：

```js
{
	album:            //布尔值，是否保存到系统相册，默认false，可为空
	imgPath:          //保存的文件路径,字符串类型，无默认值,可为空,空则不保存若路径不存在文件夹则创建此目录
	imgName:          //保存的图片名字，字符串类型，无默认值,可为空,空则不保存支持png和jpg格式，若不指定格式，则默认png
	size:             //生成的图片(正方形)的边长，数字，默认200，可为空
}
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //返回扫描信息（扫码失败则返回失败信息）
}
```

##示例代码

```js
var obj = api.require('scanner');
obj.openView({
	x:40,
	y:160,
	w:200,
	h:240,
	sound:'widget://res/beep.caf'
},function(ret,err){
	ret.msg
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeView**<div id="3"></div>

关闭自定义视图大小的二维码/条码扫描器

closeView()

##示例代码

	var obj = api.require('scanner');
	obj.closeview();

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**decode**<div id="4"></div>

图片解码

decode({params},callback(ret,err))

##params

needBr：

- 类型：布尔
- 默认值：false
- 描述：如果此值为true，则所扫二维码的信息字符串如果包含回车键(\n)则用<br>替换。false则直接将\n去掉。不传则默认为false，可为空

sound：

- 类型：字符串
- 默认值：无
- 描述：扫描结束后的提示音文件的路径，可为空

imgPath：

- 类型：字符串
- 默认值：无
- 描述：要解码的图片，可为空，若为空则去系统相册选取图片

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //返回扫描信息（扫码失败则返回失败信息）
}
```

##示例代码

```js
var obj = api.require('scanner');
obj.decode({
	sound:'widget://res/beep.caf'
},function(ret,err){
	ret.msg
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**encode**<div id="5"></div>

将字符串生成条码/二维码

encode({params},callback(ret,err))

##params

type：

- 类型：字符串
- 默认值：qr_image
- 描述：生成图片的类型，取值范围见[生成图片类型](!Constant)，可为空

string：

- 类型：字符串
- 默认值："test"
- 描述：所要生成的条码/二维码的字符串，可为空

save：

- 类型：json对象
- 默认值：见内部字段
- 描述：所生成的图片保存位置，可为空

内部字段：

```js
{
	album:            //布尔值，是否保存到系统相册，默认false，可为空
	imgPath:          //保存的文件路径,字符串类型，无默认值,可为空,空则不保存若路径不存在文件夹则创建此目录
	imgName:          //保存的图片名字，字符串类型，无默认值,可为空,空则不保存支持png和jpg格式，若不指定格式，则默认png
	size:             //生成的图片(正方形)的边长，数字，默认200，可为空
}
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:   //是否生成成功
}
```

##示例代码

```js
var obj = api.require('scanner');
obj.encode({
	string:"123456789",
	save:{
		imgPath:"fs://barImage",
		imgName:"barImage.png"
	}
},function(ret,err){
	ret.status
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**lightSwitch**<div id="6"></div>

闪光灯开关

lightSwitch({params})

##params

turnOn：

- 类型：布尔
- 默认值：false
- 描述：是否打开闪光灯，可为空

##示例代码

```js
var obj = api.require('scanner');
obj.lightSwitch({
	turnOn:false
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

</div>


<div id="const-content">

#**解码图片位置**

解码图片位置。字符串类型

##取值范围：

- album		//从系统相册选取图片
- custom		//自定义图片

#**生成图片类型**

生成的图片类型。字符串

##取值范围：

- bar_image		//生成条码图片
- qr_image		//生成二维码图片

