/*
Title: 3DTouch
Description: 3DTouch
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

#**概述**

3DTouch封装了iPhone6s、iPhone6s plus以后版本的手机特有的3DTouch功能。使用本模块需要支持3DTouch屏幕的手机和ios9.0以上的操作系统

使用此模块之前，请先在Info.plist里面配置快捷菜单，配置方法请参考链接里面的”配置3DTouch应用快捷菜单“：http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=20

![图片说明](/img/docImage/3DTouch.jpg)

#**setListener**

监听通过快捷菜单打开应用。建议在首页的apiready方法里面进行监听。

setListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	type:				//被点击的菜单的标识，字符串类型
	title:				//被点击的菜单标题，字符串类型
	subtitle:			//（可选项）被点击的菜单副标题，字符串类型
	userInfo:			//（可选项）自定义信息，JSON对象
}
```

##示例代码

```js
var obj = api.require('3DTouch');
obj.setListener(
	function(ret,err){
		var type = ret.type;
		if (type == 'com.mycompany.myapp.openfavorites'){
		
		}
	}
);
```

##可用性

iOS9及以上系统

可提供的1.0.0及更高版本
