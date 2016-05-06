/*
Title: magneticFieldSensor
Description: magneticFieldSensor
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

magneticFieldSensor封装了android的地磁场传感器，使用此模块可轻松实现对可以让你监控在地球的磁场中的变化的功能


#**startListener**<div id="a1"></div>

打开地磁场传感器

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
	x:              //地磁场强度沿x轴(μT)
	y:              //地磁场强度沿y轴(μT)
	z:              //地磁场强度沿z轴(μT)
}
```

##示例代码

```js
	var magneticFieldSensor = api.require('magneticFieldSensor');


magneticFieldSensor.startListener({type:1},function(ret, err){api.alert("可获取状态:"+ret.state+"x轴:"+ret.x+"y轴:"+ret.y+"z轴:"+ret.z)});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

#**closeListener**<div id="a2"></div>

关闭地磁场传感器


closeListener()




##示例代码

```js
var magneticFieldSensor = api.require('magneticFieldSensor');


magneticFieldSensor.closeListener();
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


