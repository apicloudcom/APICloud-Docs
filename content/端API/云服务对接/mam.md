/*
Title: mam
Description: mam
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[checkUpdate](#1)

[addEvent](#2)
</div>

#**概述**

默认APICloud会自动检测版本更新，用户也可以在[config.xml](/APICloud/技术专题/app-config-manual)里配置autoUpdate为false，然后使用mam模块来检测更新，mam模块还提供自定义事件功能

#**checkUpdate**<div id="1"></div>

检测当前版本是否有更新或者被强制关闭

checkUpdate(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true,				//操作成功状态值
	result:
	{
		update:true,			//是否有更新
		closed:true,			//设备上当前版本是否被强行关闭
	    version:'1.0',			//新版本版本号
		versionDes:'',			//新版本更新描述
		closeTip:'',			//提示用户应用版本被强行关闭时弹框的提示语
		updateTip:'',			//提示用户有更新时弹框的提示语
	    source:'',				//新版本安装包的下载地址
	    time:''					//新版本的发布时间
	}
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:””    //错误描述
}
```

##示例代码

```js
var mam = api.require('mam');
mam.checkUpdate(function( ret, err ){
	if (ret) {
		alert( JSON.stringify( ret ) );
    } else{
		alert( JSON.stringify( err ) );
    }
});
```
##补充说明

回调值中：

```js
update和closed字段是‘或’和‘与’的关系：
   -无更新：{update:false,closed:false}
   -有更新：{update:true,closed:false}
   -有更新，强制更新：{update:true,closed:true}
   -无更新，强制关闭：{update:false,closed:true}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addEvent**<div id="2"></div>

添加自定义事件，用于后端统计

addEvent({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：事件名称，不能为空

##示例代码

```js
var mam = api.require('mam');
mam.addEvent({
    name: 'shopping'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
