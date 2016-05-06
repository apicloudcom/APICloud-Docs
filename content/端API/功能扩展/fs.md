/*
Title: fs
Description: fs
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[createDir](#1)
[rmdir](#m1)
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
[getAttribute](#15)
[readByLength](#16)
[writeByLength](#17)
[getMD5](#18)
</div>

#**概述**

fs 封装了对文件操作的接口，通过此模块可对文件或文件夹进行创建、删除、读取、写入等相关操作。

#**createDir**<div id="1"></div>

创建目录

createDir({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：目标路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true           //布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,           //数字类型；错误码（详见文件操作错误码常量）
	msg: ''            //字符串；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.createDir({
	path: 'fs://floder'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m1"></div>

#**rmdir**

删除文件目录，**里面的所有文件将会一起被删除**

rmdir({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：目标文件路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true           //布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,           //数字类型；错误码（详见文件操作错误码常量）
	msg: ''            //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.rmdir({
	path: 'fs://floder'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**createFile**<div id="2"></div>

创建文件

createFile({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：目标路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true           //布尔类型；操作成功状态值，true| false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,              //数字类型；错误码（详见文件操作错误码常量）
	msg: ''               //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.createFile({
	path: 'fs://file.txt'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**remove**<div id="3"></div>

删除文件

remove({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：目标路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true            //布尔类型；操作成功状态值，true| false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,              //数字类型错误码（详见文件操作错误码常量）
	msg: ''               //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.remove({
	path: 'fs://file.txt'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**copyTo**<div id="4"></div>

拷贝文件

copyTo({params}, callback(ret, err))

##params

oldPath：

- 类型：字符串
- 描述：源路径

newPath：

- 类型：字符串
- 描述：目标路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true           //布尔类型；操作成功状态值，true| false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,             //数字类型；错误码（详见文件操作错误码常量）
	msg: ''              //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.copyTo({
	oldPath: 'fs://file.txt',
	newPath: 'fs://floder'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**moveTo**<div id="5"></div>

移动文件

moveTo({params}, callback(ret, err))

##params

oldPath：

- 类型：字符串
- 描述：源路径

newPath：

- 类型：字符串
- 描述：目标路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true           //布尔类型；操作成功状态值，true| false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,              //数字类型；错误码（详见文件操作错误码常量）
	msg: ''               //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.moveTo({
	oldPath: 'fs://file.txt',
	newPath: 'fs://floder'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**rename**<div id="6"></div>

重命名

rename({params}, callback(ret, err))

##params

oldPath：

- 类型：字符串
- 描述：源路径

newPath：

- 类型：字符串
- 描述：目标路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true           //布尔类型；操作成功状态值，true| false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,              //数字类型；错误码（详见文件操作错误码常量）
	msg: ''               //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.rename({
	oldPath: 'fs://file.txt',
	newPath: 'fs://rename.txt'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**readDir**<div id="7"></div>

列出目录

readDir({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：目标路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true,         //布尔类型；操作成功状态值，true| false
	data: []              //数组；文件夹内的所有子文件名称
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,              //数字类型；错误码（详见文件操作错误码常量）
	msg: ''               //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.readDir({
	path:'fs://'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**open**<div id="8"></div>

打开文件

open({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：目标路径

flags：

- 类型：字符串
- 默认值：read
- 描述：（可选项）文件打开方式（详见[文件打开方式]( !Constant )常量）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true,            //布尔类型；操作成功状态值，true| false
	fd:'14143124'            //字符串类型；操作文件的句柄
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,                //数字类型；错误码（详见文件操作错误码常量）
	msg: ''                 //字符串类型；错误描述
}
```

#示例代码

```js
var fs = api.require('fs');
fs.open({
	path: 'fs://file.txt',
	flags: 'read_write'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**read**<div id="9"></div>

读取文件

read({params}, callback(ret, err))

##params

fd：

- 类型：字符串
- 描述：open 方法得到的文件句柄

offset：

- 类型：数字
- 描述：（可选项）当前文件偏移量，**以 byte 为单位**
- 默认值：0

length：

- 类型：数字
- 描述：（可选项）读取内容长度
- 默认值：原文件文本内容的长度，**以 byte 为单位**

codingType：

- 类型：字符串
- 描述：（可选项）所要阅读的文本的编码格式，取值范围: gbk、utf8
- 默认值：utf8

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true,         //布尔类型；操作成功状态值，false |true
	data: ''              //字符串类型；文件内容
}
```

err：

类型：JSON 对象
内部字段：

```js
{
	code: 0,             //数字类型；错误码（详见文件操作错误码常量）
	msg: ''              //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.read({
	fd: 'open 方法得到的文件句柄',
	offset: 0,
	length: 0
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

该文件句柄必须是读或读写方式打开的，否则会引起异常

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**readUp**<div id="10"></div>

从当前文件句柄当前位置向上读取一页(页的大小如 length )数据

readUp({params}, callback(ret, err))

##params

fd：

- 类型：字符串
- 描述：（可选项）open 方法得到的文件句柄
- 默认值：当前文件句柄

length：

- 类型：数字
- 默认值：（可选项）当前最近一次读取数据的 length，**以 byte 为单位**
- 描述：此次向上读取数据的长度

codingType：

- 类型：字符串
- 描述：（可选项）所要阅读的文本的编码格式，取值范围: gbk、utf8
- 默认值：utf8

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true                //布尔类型；操作成功状态值，true|false
	data: ''                    //字符串类型；返回的文件内容
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,                  //数字类型；错误码（详见文件操作错误码常量）
	msg: ''                   //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.readUp(function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

该文件句柄必须是读或读写方式打开的，否则会引起异常

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**readDown**<div id="11"></div>

从当前文件句柄当前位置向下读取一页(页的大小如 length )数据

read({params}, callback(ret, err))

##params

fd：

- 类型：字符串
- 描述：（可选项）open 方法得到的文件句柄
- 默认值：当前文件句柄

length：

- 类型：数字
- 描述：（可选项）此次向下读取数据的长度，**以 byte 为单位**
- 默认值：当前最近一次读取数据的 length


codingType：

- 类型：字符串
- 描述：（可选项）所要阅读的文本的编码格式，取值范围: gbk、utf8
- 默认值：utf8


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true              //布尔类型；操作成功状态值，true|false
	data: ''                  //字符串类型；文件内容
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,               //数字类型；错误码（详见文件操作错误码常量）
	msg: ''                //字符串类型，错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.readDown(function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

该文件句柄必须是读或读写方式打开的，否则会引起异常

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**write**<div id="12"></div>

写入文件

write({params}, callback(ret, err))

##params

fd：

- 类型：字符串
- 描述：open 方法得到的文件句柄

data：

- 类型：字符串
- 描述：写入数据

offset：

- 类型：数字
- 描述：（可选项）写入内容的起始位置**以 byte 为单位**
- 默认值：原文件文本内容的长度

overwrite：

- 类型：布尔
- 描述：（可选项）是否覆盖指定偏移位置后面的内容
- 默认值：false

codingType：

- 类型：字符串
- 描述：（可选项）所要阅读的文本的编码格式，取值范围:gbk、utf8
- 默认值：utf8

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true		    //布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	code: 0,               //数字类型；错误码（详见文件操作错误码常量）
	msg: ''                //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.write({
	fd: 'open 方法得到的文件句柄',
	data: 'test',
	offset: 0
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

该文件句柄必须是写或读写方式打开的，否则会引起异常

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="13"></div>

关闭文件

close({params}, callback(ret, err))

##params

fd：

- 类型：字符串
- 描述：open 方法得到的文件句柄

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true		//布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,                //数字类型；错误码（详见文件操作错误码常量）
	msg: ''                 //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.close({
	fd: 'open 方法得到的文件句柄'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**exist**<div id="14"></div>

判断文件是否存在

exist({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：要判断的文件路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	exist: true                //布尔类型；操作成功状态值，true|false在
	directory: false           //文件是否是文件夹
}
```

##示例代码

```js
var fs = api.require('fs');
fs.exist({
	path: 'fs://file.txt'
},function(ret,err){
	if( ret.exist ){
		if( ret.directory ){
            alert( '文件夹' );
		}else {
            alert( '文件' );
		}
	}else {
        alert( JSON.stringify( err ) );
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getAttribute**<div id="15"></div>

获取指定路径下文件的属性

getAttribute({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：目标路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   status:                //布尔类型；操作状态；true||false
   attribute:             //JSON对象；文件属性
                          //内部字段：{
                            creationDate:    //字符串类型；创建日期 （时间戳），仅 IOS 支持此字段
                            modificationDate://字符串类型；修改日期（时间戳）
                            size:            //数字类型；文件大小，以 byte 为单位
                            type:            //字符串类型；表示文件类型，取值范围：folder（文件夹）、file（文件）
                           } 
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:            //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.getAttribute({
    path: 'fs://file.txt'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**readByLength**<div id="16"></div>

按照字符串长度读取文件，本接口针对纯文本文件有效。**无需 open**

readByLength({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：目标文件路径，要求本地路径（fs://、widget://）

substring： 

- 类型：JSON 对象
- 描述：(可选项) 读取字符串范围，**以字符为单位**
- 默认值：见内部字段
- 内部字段：

```js
{
	start:	0,     //（可选项）非负整数；规定要提取的子串的第一个字符在文件中的位置；默认：0
	length: 199     //（可选项）非负整数；所要读取的文本字符串长度；默认：原文件文本内容的总长
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true,         //布尔类型；操作成功状态值，false |true
	content: '',          //字符串类型；读取指定文件的内容
	codingType: 'utf8'    //字符串类型；文件编码类型，取值范围： utf8、gbk
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,             //数字类型；错误码（详见文件操作错误码常量）
	msg: ''              //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.readByLength({
	path: 'fs://file.txt',
	substring:{
	  start: 0,
	  length: 10
	}
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**writeByLength**<div id="17"></div>

将字符串写入指定位置的文件，**无需 open **

writeByLength({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：目标文件路径，要求本地路径（fs://），**不支持 widget 协议**

content：

- 类型：字符串
- 描述：写入的数据

place：

- 类型：JSON 对象
- 描述：(可选项) 写入文件位置	**以字符为单位**
- 默认值：见内部字段
- 内容字段：

```js
{
	start: 0,      //（可选项）非负的整数；写入文件起始位置；默认：0
	strategy: 199  //（可选项）数字类型；默认：-1；取值范围：
	               // -1 (覆盖起始位置后所有)
	               // 0 (不覆盖，插入)
	               //大于零的整数 (起始位置向后覆盖指定字符的长度)
}
```

codingType：

- 类型：字符串
- 描述：（可选项）保存的文本的编码格式，取值范围:gbk、utf8
- 默认值：utf8

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true		    //布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0,               //数字类型；错误码（详见文件操作错误码常量）
	msg: ''                //字符串类型；错误描述
}
```

##示例代码

```js
var fs = api.require('fs');
fs.writeByLength({
	path: 'fs://file.txt',
	content: 'test',
	place: {
	   start: 0, 
	   strategy: 0
	}
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**getMD5**<div id="18"></div>

获取文件 md5 值

getMD5({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：要获取其 md5 值的文件路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true,        //布尔类型；操作成功状态值，true|false在
	md5Str: ''           //字符串类型；文件的 md5 值
}
```

##示例代码

```js
var fs = api.require('fs');
fs.getMD5({
	path: 'fs://file.txt'
},function(ret){
	if( ret.status ){
         alert( ret.md5Str );
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

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
- write		    //只写
- read_write	//读写
