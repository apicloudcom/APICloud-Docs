/*
Title: fileBrowser
Description: fileBrowser
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

#**概述**

fileBrowser 实现对文件的浏览功能，点击文件可返回该文件的绝对路径。该模块可对文件进行删除操作

![图片说明](/img/docImage/fileBrowser.jpg)

#**open**

打开文件浏览器

open(callback(ret, err))

##callback(ret, err)

ret：

类型：JSON 对象

##内部字段：

```js
{
	url: '文件路径'
}
```

##示例代码

```js
var fileBrowser = api.require('fileBrowser');
fileBrowser.open(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**

关闭文件浏览器

clsoe()

##示例代码

```js
var fileBrowser = api.require('fileBrowser');
fileBrowser.close();
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本