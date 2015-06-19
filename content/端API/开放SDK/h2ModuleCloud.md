/*
Title: h2ModuleCloud
Description: h2ModuleCloud
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">
[showH2Banner](#a1)

[showH2Intersitial](#a2)

[showH2Splash](#a3)
</div>

#**概述**

H2是中国领先的移动广告交易平台，集合了最先进的广告技术和理念，包括RTB购买及Non-RTB购买，为广告主和代理商提供一个全新的广告需求端平台，为开发者降低广告管理成本并大幅提升广告收入。本模块封装了SDK，只需简单调用几个接口即可实现对广告平台的集成。
本模块集成了H2、Admob、Inmobi、AdChina、Baidu、广点通、多盟等共七家广告。

#**showH2Banner**<div id="a1">

展示Banner

showH2Banner({params})

##params

adUnitId：

- 类型：字符串
- 默认值：无
- 描述：必选项.对应的要展示的广告位，用于获取对应位置的广告.

position：

- 类型：字符串
- 默认值：center_bottom
- 描述：广告位置,可选: **center_top** (上居中), **center_bottom** (下居中)

##示例代码

```js
var h2ModuleCloud = api.require('h2ModuleCloud');
h2ModuleCloud.showH2Banner({adUnitId:"778",position:"center_bottom"});
```

##补充说明


adUnitId:"778"用于Android平台测试

adUnitId:"763"用于IOS平台测试

##可用性

iOS系统，Android系统

可提供的1.0.0 及更高版本
</div>

#**showH2Intersitial**<div id="a2">

请求插屏

showH2Intersitial({params},,callback(ret))

##params

adUnitId：

- 类型：字符串
- 默认值：无
- 描述：必选项.对应的要展示的广告位，用于获取对应位置的广告.

##callback(ret)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status://操作状态值:error请求插屏失败,dismissed插屏被关闭
}
```


##示例代码

```js
/*请求插屏*/
var h2ModuleCloud = api.require('h2ModuleCloud');
h2ModuleCloud.showH2Intersitial({adUnitId:"781"},function(ret){
    alert("ret = " + JSON.stringify(ret));
});
```

##补充说明

adUnitId:"781"用于Android平台测试

adUnitId:"766"用于IOS平台测试

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**showH2Splash**<div id="a3">

请求开屏

showH2Splash({params},callback(ret))

##params

adUnitId：

- 类型：字符串
- 默认值：无
- 描述：必选项.对应的要展示的广告位，用于获取对应位置的广告.

##callback(ret)

ret：

- 类型：JSON对象

内部字段：

```js
{
  status://操作状态值:error请求开屏失败,dismissed开屏关闭
}
```

##示例代码

```js
/*请求开屏*/
var h2ModuleCloud = api.require('h2ModuleCloud');
h2ModuleCloud.showH2Splash({adUnitId:"783"},function(ret){
    alert("ret = " + JSON.stringify(ret));
});
```

##补充说明

adUnitId:"783"用于Android平台测试

adUnitId:"769"用于IOS平台测试

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
</div>