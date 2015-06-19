/*
Title: imageCrop
Description: imageCrop
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">
[takePhoto](#a1)

[getPhoto](#a2)

[clipPhoto](#a3)

</div>

#**概述**

imageClip模块封装了Android原生图片剪切的功能，通过拍照或者从相册选取图片之后，可以调用图片剪切方法。用户可以拖放剪切剪切框改变大小，也可以通过剪切框对图片进行缩放。在选取剪切位置和大小之后，可以选择确认或者取消。

#**takePhoto**<div id="a1"></div>

拍照获取图片路径

takePhoto(callback(ret, err))


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	imgPath://拍照获取的图片路径
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:    //错误描述
}
```

##示例代码

```js
  var imageCrop = api.require('imageCrop');
  imageCrop.takePhoto(function(ret, err){
    alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err));
  });
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

#**getPhoto**<div id="a2"></div>

通过相册获取图片路径

getPhoto(callback(ret, err))


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	imgPath://拍照获取的图片路径
}
```
err：

- 类型：JSON对象

内部字段：

```js
{
	msg:       //错误描述
}
```

##示例代码

```js
/*通过相册获取图片路径*/
  var imageCrop = api.require('imageCrop');
  imageCrop.getPhoto(function(ret, err){
    alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err));
  });
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

#**clipPhoto**<div id="a3"></div>

开始截图

clipPhoto ({params},callback(ret, err))
##params

imgPath：

- 类型：字符串
- 默认值：无
- 描述：要剪切图片的路径，不能为空

height：

- 类型：数值类型
- 默认值：150
- 描述：裁剪后的图片高度，可为空，默认值为150px

width：

- 类型：数值类型
- 默认值：150
- 描述：裁剪后的图片宽度，可为空，默认值为150px

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	imgPath:       //裁剪后的图片路径，可以用于直接上传
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:       //错误描述
}
```

##示例代码

```js
/*开始截图*/
  var imageCrop = api.require('imageCrop');
  var imgPath = ""
  imageCrop.clipPhoto( {"imgPath":imgPath,"height":300,"width":300}, function(ret, err){
    alert("ret = " + JSON.stringify(ret) + "err = " + JSON.stringify(err));
  });
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

</div>





