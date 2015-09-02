/*
Title: FNScanner
Description: FNScanner
*/
<div class="outline">
[openScanner](#1)

[openView](#2)

[closeView](#3)

[decodeImg](#4)

[encodeImg](#5)

[switchLight](#6)
</div>

#**概述**

FNScanner模块是一个二维码/条形码扫描器，底层集成了ZXing，Zbar条形码/二维码分析库。调用 openScanner 接口打开默认UI的二维码/条形码扫描页面，可控制闪光灯开关、从相册读取图片；开发者亦可通过 openView 接口打开扫描区域，自定义其 UI；本模块还实现了图片解码、字符串编码功能；开发者可将扫描结果保存到系统相册或指定位置。**FNScanner 模块是 scanner 模块的优化版。**

![图片说明](/img/docImage/scanner.jpg)

<div id="1"></div>

#**openScanner**

打开二维码/条码扫描器

openScanner({params}, callback(ret))

##params

sound：

- 类型：字符串
- 描述：（可选项）扫描结束后的提示音文件路径，要求本地路径（fs://，widget://），**为保证兼容性，推荐使用  wav 格式的短音频文件**

autoLight:

- 类型：布尔
- 描述：（可选项）闪光灯是否自动打开，如果本参数为true，视当前光线环境自动打开闪光灯，**本参数仅对 iOS 有效**
- 默认值：false

saveToAlbum:

- 类型：布尔
- 描述：（可选项）扫描的二维码/条形码图片是否自动保存到相册
- 默认值：false

saveImg：

- 类型：JSON对象
- 描述：（可选项）扫描的二维码/条形码图片保存所需要的参数，若不传则不保存
- 内部字段：

```js
{
    path: 'fs://a.jpg',  //字符串类型；保存的文件路径；若路径不存在，则创建此路径，只支持fs://协议
    w: 200,              //（可选项）数字类型；生成图片的宽度，默认：200
    h: 200               //（可选项）数字类型；生成图片的高度，默认：200
}
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   eventType: 'cancel',     //字符串类型；扫码事件类型
                            //取值范围：
                            //show（模块显示）
                            //cancel（用户取消扫码）
                            //selectImage（用户从系统相册选取二维码图片）
                            //success（识别二维码/条码图片成功）
                            //fail（扫码失败）
   imgPath: '',             //字符串类型；需要保存的二维码图片绝对路径（自定义路径）
   albumPath: '',           //字符串类型；需要保存的二维码图片绝对路径（相册路径）
   content: ''              //扫描的二维码/条形码信息
}
```

##示例代码

```js
var obj = api.require('FNScanner');
obj.openScanner({
    sound: 'widget://res/beep.wav',
    autoLight: true,
    saveToAlbum: false,
    saveImg: {
        path: '',
        w: 200,
        h: 200
    }
}, function(ret) {
	 if(ret){
        alert(JSON.stringify(ret));
     }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="2"></div>

#**openView**

打开可自定义的二维码/条形码扫描器

openView({params},callback(ret))

##params

rect：

- 类型：JSON对象
- 描述：（可选项）扫描器的位置及尺寸，**在安卓平台宽高比须跟屏幕宽高比一致，否则摄像头可视区域的图像可能出现少许变形**
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320, //（可选项）数字类型；模块的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 480  //（可选项）数字类型；模块的高度；默认：所属的 Window 或 Frame 的高度
}
```

sound：

- 类型：字符串
- 描述：（可选项）扫描结束后的提示音文件路径，要求本地路径（fs://，widget://），**为保证兼容性，推荐使用  wav 格式的短音频文件**

autoLight:

- 类型：布尔
- 描述：（可选项）闪光灯是否自动打开，如果本参数为true，视当前光线环境自动打开闪光灯，**本参数仅对 iOS 有效**
- 默认值：false

saveToAlbum:

- 类型：布尔
- 描述：（可选项）扫描的二维码/条形码图片是否自动保存到相册
- 默认值：false

saveImg：

- 类型：JSON对象
- 描述：（可选项）扫描的二维码/条形码图片保存所需要的参数，若不传则不保存
- 内部字段：

```js
{
    path: 'fs://a.jpg',   //字符串类型；保存的文件路径；若路径不存在，则创建此路径，只支持fs://协议
    w: 200,               //（可选项）数字类型；生成图片的宽度，默认：200
    h: 200                //（可选项）数字类型；生成图片的高度，默认：200
}
```

fixedOn：

- 类型：字符串
- 描述：（可选项）模块所属 Frame 的名字，若不传则模块归属于当前 Window

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 Window 或 Frame 滚动
- 默认值：true（不随之滚动）

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    eventType: 'success',    //字符串类型；扫码事件类型
                             //取值范围：
                             //show（模块显示）
                             //success（扫码成功）
                             //fail（扫码失败）
    imgPath: '',             //字符串类型；需要保存的二维码图片绝对路径（自定义路径）
    albumPath: '',           //字符串类型；需要保存的二维码图片绝对路径（相册路径）
    content: ''              //扫描的二维码/条形码信息
}
```

##示例代码

```js
var obj = api.require('FNScanner');
obj.openView({
    rect: {
        x: 0,
        y: 0,
        w: 320,
        h: 480
    },
	sound: 'widget://res/beep.wav',
    autoLight: false,
    saveToAlbum: false,
    saveImg: {
        path: 'fs://a.jpg',
        w: 200,
        h: 200
    },
    fixedOn: '',
    fixed: true
},function(ret){
	if(ret){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="3"></div>

#**closeView**

关闭自定义大小的二维码/条码扫描器

closeView()

##示例代码

```js
var obj = api.require('FNScanner');
obj.closeView();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="4"></div>

#**decodeImg**

二维码/条形码图片解码

decodeImg({params},callback(ret))

##params

sound：

- 类型：字符串
- 描述：（可选项）扫描结束后的提示音文件路径，要求本地路径（fs://，widget://），**为保证兼容性，推荐使用  wav 格式的短音频文件**

path：

- 类型：字符串
- 描述：（可选项）要识别的图片路径，要求本地路径（fs://，widget://），**若不传则打开系统相册**

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,        //布尔型；是否解码成功
	content: ''          //扫描的二维码/条形码信息
}
```

##示例代码

```js
var obj = api.require('FNScanner');
obj.decodeImg({
	sound: 'widget://res/beep.wav',
    path: 'fs://a.jpg'
},function(ret){
    if(ret.status){
        alert(ret.content);
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="5"></div>

#**encodeImg**

将字符串生成二维码/条形码图片

encodeImg({params},callback(ret))

##params

type：

- 类型：字符串
- 描述：（可选项）生成图片的类型，默认值：'qr_image'
- 取值范围
    - bar_image（生成条形码图片）
	- qr_image（生成二维码图片）	

content：

- 类型：字符串
- 描述：所要生成的二维码/条形码字符串，**当 type 为 bar_image 时，该值只能为数字字符串**

saveToAlbum:

- 类型：布尔
- 描述：（可选项）扫描的二维码/条形码图片是否自动保存到相册
- 默认值：false

saveImg：

- 类型：JSON对象
- 描述：（可选项）扫描的二维码/条形码图片保存所需要的参数，若不传则不保存
- 内部字段：

```js
{
    path: 'fs://a.jpg',  //字符串类型；保存的文件路径；若路径不存在，则创建此路径，只支持fs://协议
    w: 200,              //（可选项）数字类型；生成图片的宽度，默认：200
    h: 200               //（可选项）数字类型；生成图片的高度，默认：200
}
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,        //布尔型；是否生成成功
    imgPath: '',         //字符串类型；需要保存的二维码图片绝对路径（自定义路径）
    albumPath: '',       //字符串类型；需要保存的二维码图片绝对路径（相册路径）
}
```

##示例代码

```js
var obj = api.require('FNScanner');
obj.encodeImg({
    type: 'qr_image',
	content: "123456789",
    saveToAlbum: false,
    saveImg: {
        path: 'fs://a.jpg',
        w: 200,
        h: 200
    }
},function(ret){
	if(ret.status){
        alert(JSON.stringify(ret));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="6"></div>

#**switchLight**

打开/关闭闪光灯

switchLight({params})

##params

status：

- 类型：字符串
- 描述：（可选项）打开/关闭闪光灯，默认值：'off'
- 取值范围：
    - on（打开）
    - off（关闭）

##示例代码

```js
var obj = api.require('FNScanner');
obj.switchLight({
	status: 'on'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

