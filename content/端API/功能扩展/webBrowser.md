/*
Title: webBrowser
Description: webBrowser
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[openView](#2)

[closeView](#3)

[loadUrl](#4)

[loadScript](#5)

[historyBack](#6)

[historyForward](#7)
</div>

#**概述**

webBrowser提供应用内置Web浏览器功能，Android使用腾讯X5引擎提供服务，iOS使用WKWebView（iOS8.0以下系统仍使用UIWebView）提供服务。使用腾讯X5引擎加载远程H5页面，将有更强大的兼容性和多媒体支持能力，更流畅的H5体验，同时X5引擎的云服务能力将为你的H5站点实现加速，响应更快，加载更快。
[实现应用内置浏览器的完整源码](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=30023)

#**open**<div id="1"></div>

直接打开已定制的带标题栏的浏览器组件，类似微信中的效果

open({params})

##params

url：

- 类型：字符串
- 默认值：无
- 描述：页面请求地址，支持http、https等远程地址

titleBar:

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：标题栏样式设置，可以不传
- 内部字段：

```js
{
        visible:      //标题栏是否隐藏，只支持Android，布尔类型，默认值false
        bg:    		  //标题栏背景颜色，支持 rgb，rgba，#fff等，默认值#393A3F
        textColor:    //标题栏文字颜色，支持 rgb，rgba，#fff等，默认值#FFF
}
```

progress:

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：加载进度条样式设置，可以不传
- 内部字段：

```js
{
        color:    //加载进度条颜色，支持 rgb，rgba，#fff等，默认值#45C01A
}
```

##示例代码

```js
var browser = api.require('webBrowser');
browser.open({
	url:'http://m.apicloud.com'
});

```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**openView**<div id="2"></div>

打开一个可指定大小和位置等属性的浏览器视图到当前window。

openView({params}, callback(ret, err))

##params

url：

- 类型：字符串
- 默认值：无
- 描述：页面请求地址，支持http、https等远程地址

rect：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）浏览器窗口的位置和大小，设置margin后，在不同手机上面会保持与父页面的各方向边距一致，而中间区域会自动扩充。建议使用margin布局，可以完美适配带smartBar的手机。
- 内部字段：

```js
{
    x:0,             //左上角x坐标，默认0
    y:0,             //左上角y坐标，默认0
    w:320,           //宽度，默认'auto'，页面从x位置开始自动充满父页面宽度
    h:480            //高度，默认'auto'，页面从y位置开始自动充满父页面高度
    
    marginLeft:0,	//相对父页面左外边距的距离，默认0
    marginTop:0,	//相对父页面上外边距的距离，默认0
    marginBottom:0,	//相对父页面下外边距的距离，默认0
    marginRight:0	//相对父页面右外边距的距离，默认0
}
```

progress:

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：加载进度条样式设置，可以不传
- 内部字段：

```js
{
        color:    //加载进度条颜色，支持 rgb，rgba，#fff等，默认值#45C01A
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 描述：页面加载状态、加载进度等发生变化时的回调
- 内部字段：

```js
{
	state:0,			//加载状态，数字类型，取值范围：0-开始加载；1-加载进度发生变化；2-结束加载；3-title发生变化；4-url发生变化
	progress:0,			//state为1时，页面的加载进度，数字类型，取值范围 0-100
	title:'',			//state为3时，页面当前的title，字符串类型
	url:''				//state为0|2|4时，页面当前的url，字符串类型
}
```

##示例代码

```js
var browser = api.require('webBrowser');
browser.openView({
	url:'http://m.apicloud.com',
	rect:{
		x:0,
		y:64,
		w:'auto',
		h:'auto'
	}
}, function(ret, err){
	switch (ret.state) {
		case 0:
			break;
		case 1:
			break;
		case 2:
			break;
		case 3:
			break;
		case 4:
			break;
		default:
			break;
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**closeView**<div id="3"></div>

关闭浏览窗口，只在使用openView时有效

closeView()

##params

##示例代码

```js
var browser = api.require('webBrowser');
browser.closeView();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**loadUrl**<div id="4"></div>

加载指定url，只在使用openView时有效

loadUrl({params})

##params

url：

- 类型：字符串
- 默认值：无
- 描述：页面请求地址，支持http、https等远程地址

##示例代码

```js
var browser = api.require('webBrowser');
browser.loadUrl({
    url: 'http://m.apicloud.com'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**loadScript**<div id="5"></div>

在页面执行js脚本，只在使用openView时有效

loadScript({params})

##params

script ：

- 类型：字符串
- 默认值：无
- 描述：js脚本代码

##示例代码

```js
var browser = api.require('webBrowser');
browser.loadScript({
    script: 'location.reload();'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**historyBack**<div id="6"></div>

历史记录后退一页，只在使用openView时有效

historyBack(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:true		//后退是否成功，失败时说明不能再后退了
}
```

##示例代码

```js
var browser = api.require('webBrowser');
browser.historyBack(
	function(ret,err){
		if(!ret.status){
			api.closeWin();
		}
	}
);
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**historyForward**<div id="7"></div>

历史记录前进一页，只在使用openView时有效

historyForward(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:true		//前进是否成功，失败时说明不能再前进了
}
```

##示例代码

```js
var browser = api.require('webBrowser');
browser.historyForward(
	function(ret,err){
		if(!ret.status){
		
		}
	}
);
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本