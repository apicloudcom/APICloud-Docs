/*
Title: imageClip
Description: imageClip
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

</div>

#**概述**

imageClip模块封装了屏幕截图的功能，用户可加拖动选择截图的区域，生成的图片可指定保存路径，也可保存到本地相册。用户点击已选截图区域则保存图片并取消本次截图，点击非已选区域则直接取消本次截图

#**open**<div id="a1"></div>

打开截图功能

open({params}, callback(ret, err))

##params

bg：

- 类型：字符串
- 默认值：无
- 描述：背景设置，支持#，rgb，rgba，可为空，为空则无背景

x：

- 类型：数字类型
- 默认值：0
- 描述：可截图区域视图左上角点坐标，可为空

y：

- 类型：数字类型
- 默认值：0
- 描述：可截图区域视图左上角点坐标，可为空

h：

- 类型：数字类型
- 默认值：当前设备屏幕的高
- 描述：可截图区域视图的高，可为空

w：

- 类型：数字类型
- 默认值：当前设备屏幕的宽
- 描述：可截图区域视图的宽，可为空，可为空

cornerRadius：

- 类型：数字类型
- 默认值：0
- 描述：切图的圆角大小，可为空

cutFrame：

- 类型：json对象
- 默认值：见内部字段
- 描述：截取框配置，可为空，为空则不显示截取框，只显示一个rect框

内部字段:

```js
{
	borderColor:  //边框颜色,字符串,默认#696969,支持rgb，rgba，#，可为空
	borderWidth: //边框粗细，数字类型，默认2，可为空
	cornerR:     //顶角半径，数字类型，默认3，可为空
	cornerColor：//顶角颜色，字符串类型，默认#696969,支持rgb，rgba，#，可为空
	tipsSize:   //提示文字的大小，数字类型，默认12,,可为空
	tipsPosition：//提示文字位置，字符串，默认center,取值范围见提示文字位置,可空
	tipsColor://提示文字颜色，字符串，默认#696969,支持#,rgb,rgba,img,可为空
}
```

save：

- 类型：json对象
- 默认值：见内部字段
- 描述：所生成的图片保存位置，可为空，为空则必须通过save接口保存

内部字段：

```js
{
    album:            //布尔值，是否保存到系统相册，默认false，可为空
	imgPath:          //保存的文件路径,字符串类型，无默认值,可为空,空则不保存若路径不存在文件夹则创建此目录
	imgName:         //保存的图片名字，字符串类型，无默认值,可为空,空则不保存支持png和jpg格式，若不指定格式，则默认png
}
```

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status://操作成功状态值
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
var obj = api.require('imageClip');
obj.open(function(ret, err){
	if(ret.status){
		api.alert({msg:'截图完成'});
	}else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**save**<div id="a2"></div>

保存截图到指定位置

save ({params}, callback(ret, err))

##params

album：

- 类型：布尔类型
- 默认值：false
- 描述：是否保存到系统相册，可为空

imgPath：

- 类型：字符串类型
- 默认值：无
- 描述：保存的图片路径，若路径不存在文件夹则创建此目录，可为空，为空则不保存

imgName：

- 类型：字符串类型
- 默认值：apicloud.png
- 描述：保存的图片名字，支持png和jpg格式，若不指定格式，则默认png，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:       //操作成功状态值
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
var obj = api.require('imageClip');
obj.save (function(ret, err){
	if(ret.status){
		api.alert({msg:'保存完成'});
	}else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**cancel**<div id="a3"></div>

取消截图

cancel (callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:       //操作成功状态值
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
var obj = api.require('imageClip');
obj.cancel (function(ret, err){
	if(ret.status){
		api.alert({msg:'取消屏幕截图'});
	}else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

无

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



