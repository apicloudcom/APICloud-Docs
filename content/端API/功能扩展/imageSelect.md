/*
Title: imageSelect
Description: imageSelect
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
    <li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[select](#1)

[crop](#2)
</div>

#**概述**

imageSelect封装了安卓原生图片拍照、裁剪功能，通过拍照或者从相册选取图片之后，可以调用图片剪切方法。本模块暂仅支持安卓平台。

#**select**<div id="1"></div>

通过拍照或相册获取图片

select(callback(ret, err))



##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:			//状态值
    image:          //拍照或相册获取的图片路径
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,	  //错误码 （详见错误码常量）
    msg:            //错误信息
    }
```

##示例代码

```js
var imageSelect = api.require('imageSelect');
imageSelect.select(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


#**crop**<div id="2"></div>

图片裁剪。可以单独裁剪图片，也可以先选取图片再裁剪图片。

crop({params },callback(ret,err))

##params

imgPath:

- 类型：字符串
- 默认值：“”
- 描述：要裁剪的图片地址，可以是空值，直接裁剪select获取的图片


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:            //状态值
    image:””   //截取后的图片路径
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0,	  //错误码 （详见错误码常量）
	msg:            //错误信息
}
```

##示例代码

```js
var imageSelect = api.require('imageSelect');
imageSelect.crop({
	imgPath: 'fs://album.png',
},function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```


##补充说明

crop的参数imgPath为''（空）表示使用上传select的图片。即：select和crop连着使用，通过拍照或相册获取图片，再进行图片裁剪。

##可用性

Android系统

可提供的1.0.0及更高版本

</div>

<div id="const-content">

错误码

##取值范围：

- 0	//没有错误
- 1	//没有内存卡错误
- 2	//图片剪裁失败错误
- 3	//图片获取失败错误