/*
Title: db
Description: db
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
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

db模块封装了手机常用数据库sqlite的增删改查语句，可实现数据的本地存储，极大的简化了数据持久化问题

#**openDatabase**<div id="1"></div>

打开数据库，若数据库不存在则创建数据库。

数据库打开后即使当前页面关闭了，数据库也不会关闭，除非手动调用closeDatabase()方法关闭，所以一旦打开在其它页面就可以直接使用。

若数据库放在widget目录下，那么需要先把数据库拷贝到fs://对应目录下面再使用

openDatabase({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 描述：数据库名称

path：

- 类型：字符串
- 描述：（可选项）数据库所在路径，不传时使用默认创建的路径。支持fs://、widget://等协议（如fs://user.db）
- 默认值：自动创建的路径

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true		//布尔类型；操作成功状态值，true|false
}
```
err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg: ''          //字符串类型；错误描述
}
```

##示例代码

```js
var db = api.require('db');
db.openDatabase({
	name: 'test'
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**closeDatabase**<div id="2"></div>

关闭数据库

closeDatabase({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 描述：数据库名称

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:true           //布尔类型；操作成功状态值，true|false
}
```
err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg: ''               //字符串类型；错误描述
}
```
##示例代码

```js
var db = api.require('db');
db.closeDatabase({
	name: 'test'
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**transaction**<div id="3"></div>

执行事务操作语句

transaction({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 描述：数据库名称

operation：

- 类型：字符串
- 描述：事务操作类型，取值范围如下：
	- begin         //开始事务
	- commit        //提交事务
	- rollback      //回滚操作

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:true           //布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:""                //字符串类型；错误描述
}
```

##示例代码

```js
var db = api.require('db');
db.transaction({
	name: 'test',
	operation: 'begin'
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**executeSql**<div id="4"></div>

执行sql

executeSql({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 描述：数据库名称

sql：

- 类型：字符串
- 描述：sql语句

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:true           //布尔类型；操作成功状态值，true|false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg:""                //字符串类型；错误描述
}
```

##示例代码

```js
var db = api.require('db');
db.executeSql({
	name: 'test',
	sql: 'CREATE TABLE Persons(Id_P int, LastName varchar(255), FirstName varchar(255), Address varchar(255), City varchar(255))'	
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本


#**selectSql**<div id="5"></div>

查询sql

selectSql({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 描述：数据库名称

sql：

- 类型：字符串
- 描述：sql语句

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status: true,     //布尔类型；操作成功状态值，true|false
	data: []          //数组类型；查询结果数据
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
	msg: ''           //字符串类型；错误描述
}
```

##示例代码

```js
var db = api.require('db');
db.selectSql({
	name: 'test',
	sql: 'SELECT * FROM Persons'
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统，PC模拟器

可提供的1.0.0及更高版本
</div>