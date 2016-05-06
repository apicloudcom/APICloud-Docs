/*
Title: gyroscopeSensor
Description: gyroscopeSensor
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[startListener](#a1)
[closeListener](#a2)
</div>

#**概述**

gyroscopeSensor封装了android的陀螺仪，使用此模块可轻松实现对各个方向旋转速率获取的功能


#**startListener**<div id="a1"></div>

打开陀螺仪

startListener({params}, callback(ret, err))

##params



type：

- 类型：数字
- 默认值：无
- 描述：不能为空，可选填0(特别快游戏用),1(游戏用 ),2(用户接口用 ),3( 取得倾斜度的时候使用)

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	state:		//该传感器是否可用
	x:              //速率绕x轴的旋转(弧度/秒)
	y:              //速率绕y轴的旋转(弧度/秒)
	z:              //速率绕z轴的旋转(弧度/秒)
}
```

##示例代码

```js
var gyroscopeSensor = api.require('gyroscopeSensor');


gyroscopeSensor.startListener({type:1},function(ret, err){api.alert("可获取状态:"+ret.state+"x轴:"+ret.x+"y轴:"+ret.y+"z轴:"+ret.z)});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

#**closeListener**<div id="a2"></div>

关闭陀螺仪


closeListener()




##示例代码

```js
var gyroscopeSensor = api.require('gyroscopeSensor');


gyroscopeSensor.closeListener();
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


