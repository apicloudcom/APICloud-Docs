/*
Title: FNScanner
Description: FNScanner
*/
<div class="outline">
[openScanner](#1)

[openView](#2)

[setFrame](#222)

[closeView](#3)

[decodeImg](#4)

[encodeImg](#5)

[switchLight](#6)

</div>

#**概述**

FNScanner 模块是一个二维码/条形码扫描器，是 scanner 模块的优化升级版。在 iOS 平台上本模块底层集成了 Zbar 和系统自带的条形码/二维码分析库，由于 iOS 系统平台在 iOS7.0 以上才开放了二维码/条码的相关接口，所以在 iOS6 上运行时模块会调用开源库 Zbar 去读取解析二维码/条码。只有在 iOS7 以上版本才会调用系统自带扫码功能。

**本模块封装了两套扫码方案：**

***方案一***

开发者通过调用 openScanner 接口直接打开自带默认 UI 效果的二维码/条形码扫描页面，本界面相当于打开一个 window 窗口，其界面内容不支持自定义。用户可在此界面实现功能如下：
 
1.打开关闭闪关灯

2.从系统相册选取二维码/条码图片进行解密操作

3.打开摄像头，自动对焦扫码想要解析的二维码/条码

***方案二***

通过 openView 接口打开一个自定义大小的扫描区域（本区域相当于打开一个 frame）进行扫描。开发者可自行 open 一个 frame 贴在模块上，从而实现自定义扫描界面的功能。然后配合使用serFrame、closeView、switchLight等接口实现开关闪光灯、重设扫描界面位置大小、图片解码、字符串编码等相关功能。详情请参考模块接口参数。

![图片说明](/img/docImage/scanner.jpg)

##**模块接口**

<div id="1"></div>

#**openScanner**

打开二维码/条码扫描器

openScanner({params}, callback(ret))

##params

sound：

- 类型：字符串
- 描述：（可选项）扫描结束后的提示音文件路径，要求本地路径（fs://，widget://），**为保证兼容性，推荐使用  wav 格式的短音频文件**

autorotation:

- 类型：布尔
- 描述：（可选项）扫描页面是否自动旋转（横竖屏）
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
var FNScanner = api.require('FNScanner');
FNScanner.openScanner({
    autorotation: true,
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

autorotation:

- 类型：布尔
- 描述：（可选项）扫描页面是否自动旋转（横竖屏）
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

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

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
var FNScanner = api.require('FNScanner');
FNScanner.openView({
    autorotation: true
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

<div id="222"></div>

#**setFrame**

重设可自定义的二维码/条形码扫描器的大小和位置

setFrame({params})

##params

x:

- 类型：数字
- 描述：（可选项）模块左上角的 x 坐标（相对于所属的 Window 或 Frame）
- 默认值：原值

y:

- 类型：数字
- 描述：（可选项）模块左上角的 y 坐标（相对于所属的 Window 或 Frame）
- 默认值：原值

w：

- 类型：数字
- 描述：（可选项）模块的宽度
- 默认值：原值

h:

- 类型：数字
- 描述：（可选项）模块的高度
- 默认值：原值

##示例代码

```js
var FNScanner = api.require('FNScanner');
FNScanner.setFrame({
   x: 10,
   y: 64,
   w: 300,
   h: 300
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
var FNScanner = api.require('FNScanner');
FNScanner.closeView();
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
var FNScanner = api.require('FNScanner');
FNScanner.decodeImg({
    path: 'widget://res/img/apicloud.png'
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
var FNScanner = api.require('FNScanner');
FNScanner.encodeImg({
	content: 'http://www.apicloud.com/',
    saveToAlbum: true,
    saveImg: {
        path: 'fs://album.png',
        w: 200,
        h: 200
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
var FNScanner = api.require('FNScanner');
FNScanner.switchLight({
	status: 'on'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

