/*
Title: fs
Description: fs
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[createDir](#1)

[createFile](#2)

[remove](#3)

[copyTo](#4)

[moveTo](#5)

[rename](#6)

[readDir](#7)

[open](#8)

[read](#9)

[readUp](#10)

[readDown](#11)

[write](#12)

[close](#13)

[exist](#14)
</div>

#**概述**

fs封装了对文件操作的接口，通过此模块可对文件进行创建、删除，读取、写入等相关操作。开发者简单几个接口即可操作文件，极大简化了前端代码的组织

#**createDir**<div id="1"></div>

创建目录

createDir({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：目标路径，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,           //错误码（详见文件操作错误码常量）
	msg:""            //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.createDir({
	path:'fs://newDir'
},function(ret,err){
	var status = ret.status;
	if (status) {
		api.alert({msg:'创建目录成功'});
	}else {	
		api.alert({msg:err.msg});
	};
});
```

##补充说明

创建目录

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**createFile**<div id="2"></div>

创建文件

createFile({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：目标路径，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,              //错误码（详见文件操作错误码常量）
	msg:""              //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.createFile({
	path: 'fs://a.txt'
},function(ret,err){
	var status = ret.status;
	if (status) {
		api.alert({msg:'创建文件成功'});
	}else {		
		api.alert({msg:err.msg});
	};
});
```

##补充说明

创建文件

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**remove**<div id="3"></div>

删除文件

remove({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：目标路径，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,              //错误码（详见文件操作错误码常量）
	msg:""               //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.remove({
	path: 'fs://a.txt'
},function(ret,err){
	var status = ret.status;
	if (status) {
		api.alert({msg:'删除文件成功'});
	}else {
		api.alert({msg:err.msg});
	};
});
```

##补充说明

删除文件

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**copyTo**<div id="4"></div>

拷贝文件

copyTo({params}, callback(ret, err))

##params

oldPath：

- 类型：字符串
- 默认值：无
- 描述：源路径，不能为空

newPath：

- 类型：字符串
- 默认值：无
- 描述：目标路径，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,             //错误码（详见文件操作错误码常量）
	msg:""              //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.copyTo({
	oldPath: 'fs://a.txt',
	newPath: 'fs://newDir/a.txt'
},function(ret,err){
	var status = ret.status;
	if (status) {
		api.alert({msg:'拷贝文件成功'});
	}else {
		api.alert({msg:err.msg});
	};
});
```

##补充说明

拷贝文件

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**moveTo**<div id="5"></div>

移动文件

moveTo({params}, callback(ret, err))

##params

oldPath：

- 类型：字符串
- 默认值：无
- 描述：源路径，不能为空

newPath：

- 类型：字符串
- 默认值：无
- 描述：目标路径，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,              //错误码（详见文件操作错误码常量）
	msg:""               //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.moveTo({
	oldPath: 'fs://a.txt',
	newPath: 'fs://newDir/a.txt'
},function(ret,err){
	var status = ret.status;
	if (status) {
		api.alert({msg:'移动文件成功'});
	}else {
		api.alert({msg:err.msg});
	};
});
```

##补充说明

移动文件

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**rename**<div id="6"></div>

重命名

rename({params}, callback(ret, err))

##params

oldPath：

- 类型：字符串
- 默认值：无
- 描述：源路径，不能为空

newPath：

- 类型：字符串
- 默认值：无
- 描述：目标路径，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,               //错误码（详见文件操作错误码常量）
	msg:""                //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.rename({
	oldPath: 'fs://a.txt',
	newPath: 'fs://b.txt'
},function(ret,err){
	var status = ret.status;
	if (status) {
		api.alert({msg:'重命名文件成功'});
	}else {
		api.alert({msg:err.msg});
	};
});
```

##补充说明

重命名

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**readDir**<div id="7"></div>

列出目录

readDir({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：目标路径，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true,         //操作成功状态值
	data:[]              //文件夹内的所有子文件名称，数组类型
}
```
err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,              //错误码（详见文件操作错误码常量）
	msg:""               //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.readDir({
	path:'fs://'
},function(ret,err){
	var status = ret.status;
	if (status) {
		var data = ret.data;
		if (data) {
			var jsonStr = JSON.stringify(data);
			api.alert({msg:jsonStr});
		} else{
			api.alert({msg:'此目录下为空'});
		};
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

列出目录内容

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**open**<div id="8"></div>

打开文件

open({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：目标路径，不能为空

flags：

- 类型：字符串
- 默认值：read
- 描述：文件打开方式（详见[文件打开方式](!Constant)常量），不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status: true,            //操作状态
	fd:'14143124'            //文件句柄
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,                //错误码（详见文件操作错误码常量）
	msg:""                 //错误描述
}
```

#示例代码

```js
var fs = api.require('fs');
var fd=null;
fs.open({
	path: 'fs://a.txt',
	flags: 'read_write'
},function(ret,err){
	if (ret.status) {
		api.alert({msg:'open操做成功'});
		fd = ret.fd;
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

打开文件

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**read**<div id="9"></div>

读取文件

read({params}, callback(ret, err))

##params

fd：

- 类型：字符串
- 默认值：无
- 描述：open方法得到的文件句柄，不能为空

offset：

- 类型：数字
- 默认值：0
- 描述：当前文件偏移量

length：

- 类型：数字
- 默认值：0
- 描述：读取内容长度

codingType：

- 类型：字符串
- 默认值：utf8
- 描述：所要阅读的文本的编码格式，取值范围:gbk、utf8，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true,         //操作成功状态值
	data:""              //文件内容，字符串
}
```

err：

类型：JSON对象

内部字段：

```js
{
	code:0,             //错误码（详见文件操作错误码常量）
	msg:""              //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.read({
	fd:fd,
	offset:0,
	length:0
},function(ret,err){
	if (ret.status) {
		api.alert({msg:ret.data});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

该文件句柄必须是读或读写方式打开的，否则会引起异常

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**readUp**<div id="10"></div>

从当前文件句柄当前位置向上读取一页(页的大小如length)数据

readUp({params},callback(ret, err))

##params

fd：

- 类型：字符串
- 默认值：当前文件句柄
- 描述：open方法得到的文件句柄，可为空

length：

- 类型：数字
- 默认值：当前最近一次读取数据的length
- 描述：此次向上读取数据的长度，可为空

codingType：

- 类型：字符串
- 默认值：utf8
- 描述：所要阅读的文本的编码格式，取值范围:gbk、utf8，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true                //操作成功状态值
	data:""                    //文件内容，字符串
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,                  //错误码（详见文件操作错误码常量）
	msg:""                   //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.readUp(function(ret,err){
	if (ret.status) {
		api.alert({msg:ret.data});
	}else{
		api.alert({msg:err.msg});
	}
});

```

##补充说明

该文件句柄必须是读或读写方式打开的，否则会引起异常

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**readDown**<div id="11"></div>

从当前文件句柄当前位置向下读取一页(页的大小如length)数据

read({params},callback(ret, err))

##params

fd：

- 类型：字符串
- 默认值：当前文件句柄
- 描述：open方法得到的文件句柄，可为空

length：

- 类型：数字
- 默认值：当前最近一次读取数据的length
- 描述：此次向下读取数据的长度，可为空


codingType：

- 类型：字符串
- 默认值：utf8
- 描述：所要阅读的文本的编码格式，取值范围:gbk、utf8，可为空


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true              //操作成功状态值
	data:""                  //文件内容，字符串
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,               //错误码（详见文件操作错误码常量）
	msg:""                //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.readDown(function(ret,err){
	if (ret.status) {
		api.alert({msg:ret.data});
	}else{
		api.alert({msg:err.msg});
	}
});

```

##补充说明

该文件句柄必须是读或读写方式打开的，否则会引起异常

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**write**<div id="12"></div>

写入文件

write({params}, callback(ret, err))

##params

fd：

- 类型：字符串
- 默认值：无
- 描述：open方法得到的文件句柄，不能为空

data：

- 类型：字符串
- 默认值：无
- 描述：写入数据

offset：

- 类型：数字
- 默认值：0
- 描述：当前文件偏移量

overwrite：

- 类型：布尔
- 默认值：false
- 描述：是否覆盖指定偏移位置后面的内容

codingType：

- 类型：字符串
- 默认值：utf8
- 描述：所要阅读的文本的编码格式，取值范围:gbk、utf8，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true		//操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,                //错误码（详见文件操作错误码常量）
	msg:""                 //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.write({
	fd:fd,
	data:'testtext',
	offset:0
},function(ret,err){
	if (ret.status) {
		api.alert({msg:'write操作成功'});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

该文件句柄必须是写或读写方式打开的，否则会引起异常

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**close**<div id="13"></div>

关闭文件

close({params}, callback(ret, err))

##params

fd：

- 类型：字符串
- 默认值：无
- 描述：open方法得到的文件句柄，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true		//操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,                //错误码（详见文件操作错误码常量）
	msg:""                 //错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.close({
	fd: fd
},function(ret,err){
	if (ret.status) {
		api.alert({msg:'close操作成功'});
	}else{
		api.alert({msg:err.msg});
	};
});
```

##补充说明

关闭文件

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本



#**exist**<div id="14"></div>

判断文件是否存在

exist({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：要判断的文件路径，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	exist:true                //文件是否存在
	directory:false           //文件是否是文件夹
}
```

##示例代码

```js

var obj = api.require('fs');
obj.exist({
	path: "widget://res/test.text"
},function(ret,err){
	if(ret.exist){
		if(ret.directory){
			api.alert({msg:'该路径指向一个文件夹'});
		}else{
			api.alert({msg:'该路径指向一个文件'});
		}
	}else{
		api.alert({msg:'该路径不存在任何文件'});
	}
});
```

##补充说明

判断文件是否存在

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本
</div>


<div id="const-content">

<div class="outline">
[错误码](#a1)

[文件打开方式](#a2)
</div>

#**错误码**<div id="a1"></div>

文件操作错误码，数字类型

##取值范围：

- 0	//没有错误
- 1	//找不到文件错误
- 2	//不可读取错误
- 3	//编码格式错误
- 4	//无效操作错误
- 5	//无效修改错误
- 6	//磁盘溢出错误
- 7	//文件已存在错误

#**文件打开方式**<div id="a2"></div>

文件打开方式，字符串类型

##取值范围：
- read			//只读
- write		//只写
- read_write	//读写
