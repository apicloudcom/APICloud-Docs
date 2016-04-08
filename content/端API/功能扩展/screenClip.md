/*
Title: screenClip
Description: screenClip
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#a1)

[save](#a2)

[cancel](#a3)

[screenShot](#a4)

</div>

#**概述**

screenClip模块封装了屏幕截图的功能，用户可加拖动选择截图的区域，生成的图片可指定保存路径，也可保存到本地相册。用户点击已选截图区域则保存图片并取消本次截图，点击非已选区域则直接取消本次截图。**不支持截取视频画面**。

#**open**<div id="a1"></div>

打开截图功能

open({params}, callback(ret, err))

##params

bg：

- 类型：字符串
- 描述：（可选项）背景颜色设置，支持#，rgb，rgba

cutFrame：

- 类型：JSON对象
- 描述：（可选项）截取框配置
- 默认值：见内部字段
- 内部字段:

```js
{
    x:            //（可选项）数字类型；截图区域左上角点坐标；默认：10
    y:            //（可选项）数字类型；截图区域左上角点坐标；默认：128
    w:            //（可选项）数字类型；截图区域的宽；默认：当前屏幕宽减二十
    h:            //（可选项）数字类型；截图区域的高；默认：w
	borderColor:  //（可选项）字符串类型；边框颜色，支持rgb、rgba、#；默认：#696969
	borderWidth:  //（可选项）数字类型；边框粗细；默认：2
	tipsSize:     //（可选项）数字类型；提示文字的大小；默认：12
	tipsPosition: //（可选项）字符串类型；提示文字位置，取值范围见提示文字位置；默认：center
	tipsColor:    //（可选项）字符串类型；提示文字颜色，支持#、rgb、rgba；默认：#696969
}
```

save：

- 类型：JSON对象
- 描述：所生成的图片保存位置
- 默认值：见内部字段
- 内部字段：

```js
{
	album:            //（可选项）布尔类型；是否保存到系统相册；默认：false
	imgPath:          //（可选项）字符串类型；保存的文件路径，不传则不保存，若路径不存在文件夹则创建此目录
	imgName:         //（可选项）字符串类型；保存的图片名字，不传则不保存，支持png和jpg格式，若不指定格式，则默认png
}
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:         //布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	code:         //错误码，取值范围如下：
	              // -1：未知错误
	              // 0：保存到相册失败，无操作相册权限
	              // 1：保存到到指定路径失败，无指定保存图片路径
	              // 2：截图失败
	              // 3：用户取消
}
```

##示例代码

```js
var screenClip = api.require('screenClip');
screenClip.open(function( ret, err ){		
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


#**save**<div id="a2"></div>

截取 open 接口内 cutFrame 参数指定的当前区域的图片，并保存到指定位置

save ({params}, callback(ret, err))

##params

album：

- 类型：布尔类型
- 描述：（可选项）是否保存到系统相册
- 默认值：false

imgPath：

- 类型：字符串类型
- 描述：（可选项）保存的图片路径，若路径不存在文件夹则创建此目录，不传则不保存

imgName：

- 类型：字符串类型
- 描述：（可选项）保存的图片名字，不传则不保存，支持png和jpg格式，若不指定格式，则默认png

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:       //布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	code:       //错误码，取值范围如下：
	            //-1：未知错误
	            // 0：保存到相册失败，无操作相册权限
	            // 1：保存到到指定路径失败，无指定保存图片路径
	            // 2：截图失败
	            // 3：用户取消
}
```

##示例代码

```js
var screenClip = api.require('screenClip');
screenClip.save(function( ret, err ){		
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


#**cancel**<div id="a3"></div>

取消截图

cancel()

##示例代码

```js
var screenClip = api.require('screenClip');
screenClip.cancel();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**screenShot**<div id="a4"></div>

截屏

screenShot ({params}, callback(ret, err))

##params

album：

- 类型：布尔类型
- 描述：（可选项）是否保存到系统相册
- 默认值：false

imgPath：

- 类型：字符串类型
- 描述：（可选项）保存的图片路径，若路径不存在文件夹则创建此目录，不传则不保存

imgName：

- 类型：字符串类型
- 描述：（可选项）保存的图片名字，不传则不保存，支持png和jpg格式，若不指定格式，则默认png

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:       //布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	code:        //错误码，取值范围如下：
	             //-1：未知错误
	             // 0：保存到相册失败，无操作相册权限
	             // 1：保存到到指定路径失败，无指定保存图片路径
	             // 2：截图失败
}
```

##示例代码

```js
var screenClip = api.require('screenClip');
screenClip.screenShot(function( ret, err ){		
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

</div>

<div id="const-content">

#**提示文字位置**

截取框内提示文字的位置。字符串类型

##取值范围：

- center        //正中间
- right_up//右上角
- right_down//右下角
- left_up//左上角
- left_down//左下角
- center_up//靠上边，左右居中
- center_down//靠下边，左右居中
- right_center//靠右上下居中
- left_center//靠左上下居中




