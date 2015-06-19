/*
Title: db
Description: db
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[openDatabase](#1)

[closeDatabase](#2)

[transaction](#3)

[executeSql](#4)

[selectSql](#5)
</div>

#**概述**

db模块封装了手机常用数据库sqlite的增删改查语句，可实现数据的本地存储，极大的简化了数据归档问题

#**openDatabase**<div id="1"></div>

打开数据库，若数据库不存在则创建数据库。

数据库打开后即使当前页面关闭了，数据库也不会关闭，除非手动调用closeDatabase()方法关闭，所以一旦打开在其它页面就可以直接使用。

若数据库放在widget目录下，那么需要先把数据库拷贝到fs://对应目录下面再使用

openDatabase({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 默认值：无
- 描述：数据库名称，不能为空

path：

- 类型：字符串
- 默认值：自动创建的路径
- 描述：数据库所在路径，不传时使用默认创建的路径。支持fs://、widget://等协议（如fs://user.db）

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
	msg:""    //错误描述
}
```

##示例代码

```js
var db = api.require('db');
db.openDatabase({
	name: 'test'
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'数据库打开成功'});
	}else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

打开数据库

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**closeDatabase**<div id="2"></div>

关闭数据库

closeDatabase({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 默认值：无
- 描述：数据库名称，不能为空

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
	msg:""    //错误描述
}
```
##示例代码

```js
var db = api.require('db');
db.closeDatabase({
	name:'test'
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'关闭数据库成功'});
    }else{
		api.alert({msg:'error'});
    }
});
```

##补充说明

关闭数据库

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**transaction**<div id="3"></div>

执行事务操作语句

transaction({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 默认值：无
- 描述：数据库名称，不能为空

operation：

- 类型：字符串
- 默认值：无
- 描述：事务操作类型（详见[事务操作类型](!Constant)常量），不能为空

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
	msg:""    //错误描述
}
```

##示例代码

```js
var db = api.require('db');
db.transaction({
	name: 'test',
	operation: 'begin'
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'事务操作成功'});
    }else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

事务操作

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**executeSql**<div id="4"></div>

执行sql

executeSql({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 默认值：无
- 描述：数据库名称，不能为空

sql：

- 类型：字符串
- 默认值：无
- 描述：sql语句，不能为空

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
	msg:""    //错误描述
}
```

##示例代码

```js
var db = api.require('db');
var sql = 'CREATE TABLE Persons(Id_P int, LastName varchar(255), FirstName varchar(255), Address varchar(255), City varchar(255))';
db.executeSql({
	name: 'test',
	sql: sql
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'执行SQL成功'});
	}else{
		api.alert({msg:err.msg});
    }
});
```

##补充说明

执行sql语句

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**selectSql**<div id="5"></div>

查询sql

selectSql({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 默认值：无
- 描述：数据库名称，不能为空

sql：

- 类型：字符串
- 默认值：无
- 描述：sql语句，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true,     //操作成功状态值
	data:[]          //查询结果数据，数组类型
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //错误描述
}
```

##示例代码

```js
var db = api.require('db');
var sql = 'SELECT * FROM Persons';
db.selectSql({
	name:'test',
	sql: sql
}, function(ret, err){
	if(ret.status){
		var data = ret.data;
	}else{
	}
});
```

##补充说明

查询sql语句

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本
</div>

<div id="const-content">
#**事务操作**

事务操作类型。字符串类型

##取值范围：

- begin         //开始事务
- commit        //提交事务
- rollback      //回滚操作
