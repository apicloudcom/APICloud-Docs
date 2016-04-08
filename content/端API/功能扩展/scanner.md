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

二维码/条码扫描器，本模块底层集成了ZXing，Zbar条码/二维码分析库，调用open接口可打开默认UI的二维码/条码扫描页面，此页面内添加了闪光灯开关、从相册读取图片扫描按钮。开发者亦可通过openView接口打开自定义扫描区域（大小和位置）的扫码视图。本模块亦实现了对图片解码，对字符串编码的功能，按照接口规范调用decode、encode接口即可实现。开发者可通过调整接口参数可将扫描结果保存到系统相册、指定位置。**[FNScanner 模块](/端API/功能扩展/FNScanner)是 scanner 模块的优化版，建议使用 FNScanner 模块，此模块已停止更新。**

![图片说明](/img/docImage/scanner.jpg)

#**open**<div id="1"></div>

打开二维码/条码扫描器

open()

##params

needBr：

- 类型：布尔
- 默认值：false
- 描述：（可选项）如果本参数为true，则所扫二维码的信息字符串如果包含回车键(\n)则用<br>替换。false则直接将\n去掉

sound：

- 类型：字符串
- 默认值：无
- 描述：（可选项）扫描结束后的提示音文件的路径，暂仅支持fs://、widget://等本地路径协议

save：

- 类型：json对象
- 默认值：见内部字段
- 描述：（可选项）所生成的图片保存位置
- 内部字段：

```js
{
	album:            //（可选项）布尔值，是否保存到系统相册，默认false
	imgPath:          //（可选项）保存的文件路径，无默认值,若不传则不保存；若路径不存在文件夹，则创建此目录
	imgName:          //（可选项）保存的图片名字，字符串类型，无默认值,若不传则不保存，支持png和jpg格式，若不指定格式，则默认png
	size:             //（可选项）生成的图片(正方形)的边长，数字，默认200
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   eventType：//扫码事件类型，字符串类型，取值范围如下：
                cancel  //用户取消扫码
                image   //用户选择从系统相册读取二维码
                success//扫码成功
                fail   //扫码失败
   savePath： //若扫码成功且需保存所扫二维码图片，则返回该图片保存路径
   msg:""    //返回扫描信息（扫码失败则返回失败信息）
}
```

##示例代码

```js
var scanner = api.require('scanner');
scanner.open(function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
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
- 描述：（可选项）视图左上角点的X坐标

y：

- 类型：数字
- 默认值：0
- 描述：（可选项）视图左上角点的Y坐标


w：

- 类型：数字
- 默认值：父窗口视图的宽
- 描述：（可选项）模块视图的宽


h：

- 类型：数字
- 默认值：父窗口视图的高
- 描述：（可选项）模块视图的高


fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

needBr：

- 类型：布尔
- 默认值：false
- 描述：（可选项）如果此值为true，则所扫二维码的信息字符串如果包含回车键(\n)则用<br>替换。false则直接将\n去掉

sound：

- 类型：字符串
- 默认值：无
- 描述：（可选项）扫描结束后的提示音文件的路径，暂仅支持fs://、widget://等本地路径协议

save：

- 类型：json对象
- 默认值：见内部字段
- 描述：（可选项）所生成的图片保存位置
- 内部字段：

```js
{
	album:            //（可选项）布尔值，是否保存到系统相册，默认false
	imgPath:          //（可选项）保存的文件路径，无默认值,若不传则不保存，若路径不存在则创建此目录
	imgName:          //（可选项）保存的图片名字，字符串类型，无默认值,若不传则不保存，支持png和jpg格式，若不指定格式，则默认png
	size:             //（可选项）生成的图片(正方形)的边长，数字，默认200
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   savePath： //若扫码成功且需保存所扫二维码图片，则返回改图片保存路径
	msg:""    //返回扫描信息（扫码失败则返回失败信息）
}
```

##示例代码

```js
var scanner = api.require('scanner');
scanner.openView({
	x: 40,
	y: 160,
	w: 200,
	h: 240,
	sound: 'widget://test.wav'
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeView**<div id="3"></div>

关闭自定义视图大小的二维码/条码扫描器

closeView()

##示例代码

```js
var scanner = api.require('scanner');
scanner.closeview();
```

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
- 描述：（可选项）如果此值为true，则所扫二维码的信息字符串如果包含回车键(\n)则用<br>替换。false则直接将\n去掉

sound：

- 类型：字符串
- 默认值：无
- 描述：（可选项）扫描结束后的提示音文件的路径，暂仅支持fs://、widget://等本地路径协议
- 备注：若不传则无提示声音

imgPath：

- 类型：字符串
- 默认值：无
- 描述：（可选项）要解码的图片
- 备注：若不传则去系统相册取图片

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:""    //返回扫描信息（扫码失败则返回失败信息）
}
```

##示例代码

```js
var scanner = api.require('scanner');
scanner.decode({
	sound: 'widget://test.wav'
}, function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
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
- 描述：（可选项）生成图片的类型，取值范围见[生成图片类型](!Constant)

string：

- 类型：字符串
- 默认值："test"
- 描述：（可选项）所要生成的条码/二维码的字符串

save：

- 类型：json对象
- 默认值：见内部字段
- 描述：（可选项）所生成的图片保存位置
- 内部字段：

```js
{
	album:            //（可选项）布尔值，是否保存到系统相册，默认false
	imgPath:          //（可选项）保存的文件路径，无默认值,若不传则不保存，若路径不存在则创建此目录
	imgName:          //（可选项）保存的图片名字，字符串类型，无默认值,若不传则不保存，支持png和jpg格式，若不指定格式，则默认png
	size:             //（可选项）生成的图片(正方形)的边长，数字，默认200
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   savePath： //若扫码成功且需保存所扫二维码图片，则返回改图片保存路径
	status:   //是否生成成功
}
```

##示例代码

```js
var scanner = api.require('scanner');
scanner.encode({
	string: '123456789',
	save: {
		imgPath: 'fs://',
		imgName: 'album.png'
	}
},function( ret, err ){		
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

#**lightSwitch**<div id="6"></div>

闪光灯开关

lightSwitch({params})

##params

turnOn：

- 类型：布尔
- 默认值：false
- 描述：（可选项）是否打开闪光灯

##示例代码

```js
var scanner = api.require('scanner');
scanner.lightSwitch({
	turnOn: false
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

