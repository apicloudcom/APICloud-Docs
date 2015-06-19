/*
Title: iBookReader
Description: iBookReader
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">
[openBookShelf](#openBookShelf)
</div>

#**概述**

一款文本阅读器，自带书架、翻页、书架、进度设置功能。
设置：
点击安卓菜单键可以弹出设置菜单
阅读界面采用羊皮纸风格，翻页采用模拟iReader的仿真翻页方式。
在添加图书菜单内可以对手机图书进行移动、重命名等操作。

#**openBookShelf**<div id="openBookShelf"></div>

打开阅读器

openBookShelf()

##示例代码

```js
var iBookReader = null;
apiready = function(){
	iBookReader = api.require('iBookReader');
};

function openBookShelf(){
	iBookReader.openBookShelf();
}
```

##补充说明

无

##可用性

Android系统

可提供的 1.0.0 及更高版本