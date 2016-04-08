/*
Title: gpsState
Description: gpsState
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>

<div id="method-content">

<div class="outline">
[gpsState](#a1)

[opengps](#a2)

</div>


#**概述**

gpsState为获取手机GPS状态.


#**gpsState**<div id="a1"></div>

获取当前gps状态

gpsState(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	gps:true           //返回值为true表示当前手机gps为开启状态  false为关闭状态
}
```

##示例代码

```js
var gpsmodel = api.require('gpsState');
gpsmodel.gpsstate(function(ret) {
	alert(JSON.stringify(ret));
});
```

##补充说明

获取当前手机gps状态，对于安卓手机为当前手机gps状态，对于苹果手机则是获取当前手机是否被用户同意了gps权限。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**opengps**<div id="a2"></div>

安卓手机打开系统gps界面

opengps()


##示例代码

```js
var gpsmodel = api.require('gpsState');
gpsmodel.opengps();
```

##补充说明

打开安卓手机的gps设置界面

##可用性

Android系统

可提供的1.0.0及更高版本
