/*
Title: rotationVector
Description: rotationVector
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[startListener](#a1)

[closeListener](#a2)
</div>

#**概述**

rotationVector封装了android的旋转矢量传感器，使用此模块可轻松实现对各个方向旋转矢量分量获取的功能


#**startListener**<div id="a1"></div>

打开旋转矢量传感器

startListener({params}, callback(ret, err))

##params



type：

- 类型：数字
- 默认值：无
- 描述：不能为空，可选填0(特别快游戏用),1(游戏用 ),2(用户接口用 ),3( 取得倾斜度的时候使用)

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	state:		//该传感器是否可用
	x:              //沿x轴旋转矢量分量（X * SIN（θ/ 2））
	y:              //沿y轴旋转矢量分量（Y * SIN（θ/ 2））
	z:              //沿z轴旋转矢量成分（Z * SIN（θ/ 2））
	r:              //旋转向量的标量分量（（COS（θ/ 2））
}
```

##示例代码

```js
var rotationVector = api.require('rotationVector');


rotationVector.startListener({type:1},function(ret, err){api.alert("可获取状态:"+ret.state+"x轴:"+ret.x+"y轴:"+ret.y+"z轴:"+ret.z+"r:"+ret.r)});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

#**closeListener**<div id="a2"></div>

关闭旋转矢量传感器


closeListener()




##示例代码

```js
var rotationVector = api.require('rotationVector');


rotationVector.closeListener();
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


