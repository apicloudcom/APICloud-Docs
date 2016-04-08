/*
Title: 数据云服务开发指南
Description: 数据云服务开发指南
Sort: 9
*/


[介绍](#1)

[基本信息](#2)

[表结构管理](#3)

[API调试](#4)

[客户端API](#4)

#**介绍**<div id="1"></div>

APICloud提供从客户端到云端完整的数据存储解决方案，云端提供数据管理功能，客户端提供数据访问API，开发者只需要在云端创建好表结构和关系，云端会自动生成Restful接口，然后在客户端调用mcm模块API方法即可，不需要自己搭建服务器和写任何服务端代码。

#**基本信息**<div id="2"></div>

##应用设置

数据云服务默认为关闭状态，如下，选择开启数据云。

![图片说明](/img/docImage/29.png)
 
开启数据云后，在页面中可以设置发件邮箱地址、是否开启注册用户邮箱验证，以及密码重置邮件模板等。

![图片说明](/img/docImage/30.png)

##API分析
在API分析页面，展示了数据库、文件存储空间、数据传输的使用情况，以及整个云API请求数汇总等。

![图片说明](/img/docImage/31.png)

如下图，在Api Requests栏可以查看指定时间段、各平台不同种类api的使用情况。

![图片说明](/img/docImage/32.png)
 
在File Storage栏可以查看指定时间段内数据存储情况。

![图片说明](/img/docImage/33.png)
 
在Data Transfer栏则可以查看指定时间段内数据传输情况。

![图片说明](/img/docImage/34.png)
 
#**表结构管理**<div id="3"></div>

##数据类型

- String

	字符串类型，如"APICloud"。

- Number

	数字类型，如10。

- Boolean

	布尔类型，取值为true或false。

- Date

	日期格式，如2014-09-12 16:37:10。

- File

	文件对象，对应的是file表中的一条记录，包括文件唯一标识、文件名、文件下载地址等。

- Array

	数组类型，如[1, 2, 3]。

- Object

	JSON对象，如：{name:"APICloud"}

- GeoPoint

	位置对象，包含经度和纬度，如{"lat": 33.023, "lng": 45.932}

- Pointer

	指针对象，创建列时需要指定该列对应的目标表名即Target Class，该列的每一项的值为目标表当中一条记录的id值。

- Relation

	关系对象，同样创建列时需要指定该列对应的目标表名即Target Class，该列的每一项的值对应目标表中的N条记录。

##表操作

- 创建表

如下图，APICloud为开发者创建了几张默认的表，每个表里面都有不同的默认的字段。选择创建Class来创建一张新的表。

![图片说明](/img/docImage/35.png)

- 删除表

选择左边的表，右边会列出对应表的相关信息，在更多选项里面，选择删除Class即可删除该表。默认的表不能删除。

![图片说明](/img/docImage/36.png)
 
- 权限设置

如图，在更多选项里面选择权限设置，弹出权限设置页面，可以为不同的操作设置权限，以允许指定的用户和角色访问。

![图片说明](/img/docImage/37.png)
 
- 导入数据

选择导入数据，可以从文件里面为指定表导入数据，导入的数据格式只支持JSON。

![图片说明](/img/docImage/38.png)
 
- 导出数据

在更多选项里面选择导出数据，如图，可以设定导出数据的起始日期和截止日期，数据文件会发送到开发者的邮箱中。

![图片说明](/img/docImage/39.png)
 
##列操作

- 创建列

如图，选择添加列，在弹出的页面选择列的数据类型，指定列名，即可创建一列。

![图片说明](/img/docImage/40.png)
 
- 删除列

表里面默认的列不能删除，只能删除创建的列。选择更多，在弹出的选项列表里面选择删除列。

![图片说明](/img/docImage/41.png)

在弹出页选择相应的列即可删除。

![图片说明](/img/docImage/42.png)

##行操作

- 增加行

如图，选择添加行，表中会立即增加一空行，在该行中任意列输入合法数据以后，会自动生成行id和该行其它默认数据。

![图片说明](/img/docImage/43.png)
 
- 删除行

选中要删除的行，选择删除行可删除该行。在更多选项里面选择删除所有数据，可以删除整个表的数据。

![图片说明](/img/docImage/44.png)

##**API调试**<div id="4"></div>

通过在线API调试，开发者可以对表中的数据进行增、删、改、查等基本操作。如图为列出的操作方法：

![图片说明](/img/docImage/45.png)
 
例如，选择create a new instance，输入body对应的JSON值，即可向Person表中插入一条记录。

![图片说明](/img/docImage/46.png)
 
默认的user表除了以上图中列出的几个操作外，还有login和logout方法，如图：

![图片说明](/img/docImage/47.png)

#**客户端API**<div id="5"></div>

##MCM模块

- model对象

model对象中定义了基本的增删改查接口，扩展对象如user继承了model对象的所有方法，以下为使用model对象的insert方法：

```js
var model = api.require('model');
model.insert({
	class: 'Person',
	value:{
		name: 'kenny'
	}
}, function(ret, err) {
	if (ret) {

	} else {

	}
});
```

更多model对象方法请参考mcmRef文档中的model对象。

- user对象

user是在model对象的基础上扩展而来，拥有model对象的所有方法，同时自身定义了包括login、logout、register等方法。例如使用用户名和密码登录：

```js
var user = api.require('user');
user.login({
	username: 'kenny',
	password: '123456'
}, function(ret, err) {
	if (ret) {
	
	} else {
	
	}
});
```

登录成功后，会话信息会在本地保存，直到调用logout方法退出登录。

更多user对象方法请参考mcmRef文档中的user对象。

- query对象

query对象用于构建一个查询，包含分页、排序、以及其它where语句等，设置查询条件后，传递给model对象的查询方法，以获取符合条件的记录。例如查询Person表中name字段中姓张的前20条记录：

```js
var query = api.require('query');
query.createQuery(
	function(ret, err) {
		var qid = ret.qid;
		query.limit({
			qid:qid,
			value:20
	    });
		query.whereStartWith({
			qid:qid,
			column:'name',
	        value:'张'
	    });
		var model = api.require('model');
		model.findAll({
			class:'Person',
			qid:qid
    	}, function(ret, err) {
			if (ret) {
				
			}
    	});
	}
);
```

更多query对象方法请参考mcmRef文档中的query对象。

- relation对象

relation对象主要用于对表中数据类型为Relation的列进行操作。例如Person表中有一个数据类型为Relation、列名为book的列，其Relation的目标表为Book表，那么以下代码可以向Person表中的某人增加一本书：

```js
var relation = api.require('relation');
relation.insert({
	class: 'Person',
	id: '5412d4f50aa55bc16e48a2c5',				//id为Person表中某行的id
	column:'book',						//column为关系列的列名
	value:{
		name:'史记'					//Book表中书名为'史记'
	}
}, function(ret, err) {
	if (ret) {
	
	} else {
	
	}
});
```

以下代码则可以查询Person表中某人拥有的所有书：

```js
var relation = api.require('relation');
relation.findAll({
	class: 'Person',
	id: '5412d4f50aa55bc16e48a2c5',				//id为Person表中某行的id
	column:'book'						//column为关系列的列名
}, function(ret, err) {
	if (ret) {

	} else {

	}
});
```
