/*
Title: 数据存储开发指南
Description: 数据存储开发指南
Sort: 9
*/


[介绍](#1)

[Local Storage](#2)

[偏好数据](#3)

[文件](#4)	
- [api对象方法](#5)
- [fs对象方法](#6)

[数据库](#7)
- [说明](#8)
- [用法](#9)

#**介绍**<div id="1"></div>

APICloud为开发者提供了多种本地数据存储方案，包括Local Storage、偏好数据、文件和数据库等，以满足不同规模数据存储需求。其中Local Storage和偏好数据一般用于存储比较简单、规模较小的数据，而文件和数据库多用于存储大量数据，并且利于管理。

#**Local Storage**<div id="2"></div>

APICloud对html5的Local Storage进行了封装，在存储时更加方便。通过$api对象的setStorage方法不仅可以存储字符串，还可以直接存储JSON对象，而getStorage获取时也可以直接得到JSON对象。用法如下：

```js
var key = 'user';
var user = {};
user.name = 'kenny';
user.email = 'kenny@163.com';
$api.setStorage(key, user);
user = $api.getStorage(key);
```

#**偏好数据**<div id="3"></div>

适用于少量的偏好设置数据的存储，一般用于保存一些状态值等，不推荐大量的数据通过此方式存储。
api对象提供了setPrefs、getPrefs、removePrefs方法，以键值对的方式传入参数，进行设置、获取和移除等，例如记录应用是否是第一次启动：

    api.setPrefs({
    	firstLaunch:false
    });

具体参数及用法请参考[api文档](/端API/api)中的说明。

#**文件**<div id="4"></div>

##api对象方法<div id="5"></div>

APICloud为开发者提供了文件和文件夹相关操作API，包括创建、移动、删除文件和文件夹等，以及文本内容的读写操作。
其中api对象提供了基本的readFile、writeFile方法，支持整个文件内容的读写操作，其读写文件示例代码如下：

```js
api.readFile({
	path: 'fs://a.txt'
}, function(ret, err){
	if(ret.status){
		var data = ret.data;
	}
});

api.writeFile({
	path: 'fs://a.txt',
	data:'writeFile测试内容'
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'写入文件成功'});
	} else{
		api.alert({msg:err.msg});
	}
});
```

##fs对象方法<div id="6"></div>

若要使用更加丰富的文件操作API，则需要引入fs模块，该模块详细定义了文件和文件夹的相关操作，并且支持文本内容的指定位置读写，其写文件示例代码如下：

```js
var fs = api.require('fs');
fs.open({
	path:'fs://test.txt',
	flags:'read_write'
},function(ret, err) {
	if (ret.status) {
		var fd = ret.fd;			//fd为文件句柄
		fs.write({
			fd:fd,
			data:'text',
			offset:0
		},function(ret,err){
			if (ret.status) {
				api.alert({msg:'write操作成功'});
			} else{
				api.alert({msg:err.msg});
			}
		});
	}
});
```

其它方法请参考fs模块文档。

#**数据库**<div id="7"></div>

##说明<div id="8"></div>

APICloud为开发者提供了操作本地数据库的接口，但需要开发者熟悉基本的SQL语句，如创建表、插入和更新数据、获取数据等操作。

##用法<div id="9"></div>

db模块提供了数据库相关操作API，详见db模块文档。部分示例代码如下：

创建一张名为Persons的表：

```js
var db = api.require('db');
var sql = 'CREATE TABLE Persons(Id_P int, LastName varchar(255), FirstName varchar(255),
Address varchar(255), City varchar(255))';
db.executeSql({
	name: 'databaseName',
	sql: sql
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'创建表成功'});
    } else{
		api.alert({msg:err.msg});
    }
});
```
	
从Persons表里面查询数据：

```js
var db = api.require('db');
var sql = 'SELECT * FROM Persons';
db.selectSql({
	name:'databaseName',
	sql: sql
}, function(ret, err){
	if(ret.status){
		var data = ret.data;	
	} else{
		
	};
});
```