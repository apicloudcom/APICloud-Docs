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
初次启动需要点击安卓菜单键添加一本txt图书。

#**openBookShelf**<div id="openBookShelf"></div>

打开阅读器

openBookShelf()

##示例代码

```js
var iBookReader = null;
apiready = function(){
	iBookReader = api.require('iBookReader');
}

function openBookShelf(){
	iBookReader.openBookShelf();
}
```

##补充说明

无

##可用性

Android系统

可提供的 1.0.0 及更高版本