/*
Title: zip
Description: zip
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[archive](#1)

[unarchive](#2)
</div>

#**概述**

zip 模块封装了 zip 文件解压缩的相关操作，开发者只需简单地调用相关接口，即可实现对 zip 文件的操作，易学简单易掌握

#**archive**<div id="1"></div>

压缩文件

archive({params}, callback(ret, err))

##params

password：

- 类型：字符串
- 默认值：无
- 描述：压缩的密码，可为空

files：

- 类型：数组
- 默认值：无
- 描述：压缩的文件路径组成的数组，不能为空

内部字段：

```js
[
	'widget://res/1.docx'
]
```
toPath：

- 类型：字符串
- 默认值：无
- 描述：压缩后的文件存放路径，若未指定文件名，则默认原文件名（若源文件为多个则取第一个），可为空。为空时默认为原文件（若源文件为多个则取第一个）路径

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:			//状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:            //错误信息
    }
```

##示例代码

```js
var zip = api.require('zip');
zip.archive({
	files: [ 'fs://test.txt' ]
}, function(ret, err){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

压缩文件，如果压缩的是单个文件，则压缩后的文件放在同目录下，并且保持原文件名以 .zip 为后缀。若为多个文件，则压缩后的文件放在与第一个文件同目录文件夹下，命名为 UZArchive.zip

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**unarchive**<div id="2"></div>

解压文件

unarchive({params}, callback(ret, err))

##params

file:

- 类型：字符串
- 默认值：无
- 描述：要解压的文件路径，不可为空

pasword：

- 类型：字符串
- 默认值：无
- 描述：解压的密码，可为空

toPath：

- 类型：字符串
- 默认值：无
- 描述：解压后的文件路径，可为空。为空时默认原文件路径

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:            //状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:            //错误信息
}
```

##示例代码

```js
var zip = api.require('zip');
zip.unarchive({
	file: 'fs://fitest.zip',
	password: '123'
}, function(ret, err){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

解压文件，解压后的文件与原文件同名同目录

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
