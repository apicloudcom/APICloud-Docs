/*
Title: mcm
Description: mcm
*/

#**概述**
 使用APICloud数据云服务时，客户端需要使用mcm模块来对云端数据进行操作，mcm模块包含了model、user、relation和query等对象

<ul id="tab" class="clearfix">
	<li class="active"><a href="#attr-content">model对象</a></li>
	<li><a href="#const-content">query对象</a></li>
	<li><a href="#evt-content">relation对象</a></li>
	<li><a href="#method-content">user对象</a></li>
</ul>

<div id="attr-content">

<div class="outline">
[config](#a1)

[insert](#a2)

[deleteById](#a3)

[updateById](#a4)

[findById](#a5)

[findAll](#a6)

[count](#a7)

[exist](#a8)

[uploadFile](#a9)

[downloadFile](#a10)
</div>

#**概述**

通过model对象，可以对云端指定表内数据进行修改，以及通过查询条件进行查询。注：如果不是在云端编译的应用中测试，则需要调用config方法，配置appKey等信息

#**config**<div id="a1"></div>

全局函数，配置appKey等应用信息。设置一次即生效，直到下一次设置，不设置默认为当前应用的信息

config({param})

##params

appId：

- 类型：字符串
- 默认值：widget目录下config.xml里面的id
- 描述：应用的id，在APICloud上应用概览里获取，可以为空

appKey：

- 类型：字符串
- 默认值：无
- 描述：应用的安全校验Key，在APICloud上应用概览里获取，不能为空

host：

- 类型：字符串
- 默认值：无
- 描述：应用服务器地址，可为空，为空时默认为编译时的服务器地址

##示例代码

```js
var model = api.require('model');
model.config({
    appKey: 'A991A337-0212-A29D-0C9C-A518E39FXXXX',
    host: 'https://d.apicloud.com'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**insert**<div id="a2"></div>

向对象插入一条数据

insert({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

value：

- 类型：JSON对象
- 默认值：无
- 描述：插入的键值对，与服务器上class中键值对应，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：插入成功后对应的该条数据在服务器的所有键值

err：

- 类型：JSON对象
- 描述：错误信息

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**deleteById**<div id="a3"></div>

根据ID删除对象的一条数据

deleteById({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

id：

- 类型：字符串
- 默认值：无
- 描述：被删除数据的行ID，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**updateById**<div id="a4"></div>

根据ID更新对象的一条数据

updateById({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

id：

- 类型：字符串
- 默认值：无
- 描述：将要更新数据的行ID，不能为空

value：

- 类型：JSON
- 默认值：无
- 描述：将要更新的键值对，与服务器上class中键值对应，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：更新成功后对应的该条数据在服务器的所有键值

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
var model = api.require('model');
model.updateById({
    class: 'user',
    id: 'A000001',
    value: {
        nickname: 'Tom'
    }
}, function(ret, err){
    if(ret){
        //do something      
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**findById**<div id="a5"></div>

根据ID查找对象的一条数据

findById({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

id：

- 类型：字符串
- 默认值：无
- 描述：被查找数据的行ID，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：查找成功后对应的该条数据在服务器的所有键值

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
var model = api.require('model');
model.findById({
    class: 'user',
    id: 'A00001'
},function(ret, err){
    if(ret){
        //do something
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**findAll**<div id="a6"></div>

根据条件查找对象中所有符合条件的数据

findAll({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

qid：

- 类型：字符串
- 默认值：无
- 描述：通过query对象创建的查询条件对象ID，见query对象，不能为空

##callback(ret, err)

ret：

- 类型：JSON数组
- 描述：查找成功后对应的所有满足条件的数据

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
var model = api.require('model');
var query = api.require('query');
query.createQuery(function(ret, err) {
    if (ret && ret.qid) {
        var queryId = ret.qid;
        model.findAll({
            class: "activity",
            qid: queryId
        }, function(ret, err) {
            if (ret) {
                //do something           
            }
            
        });
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**count**<div id="a7"></div>

根据条件返回对象下满足该条件的总记录数

count({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

qid：

- 类型：字符串
- 默认值：无
- 描述：通过query对象创建的查询条件对象ID，见query对象，可以为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**exist**<div id="a8"></div>

查询某对象/对象下某行是否存在

exist({params}, callback(ret, err))

#**params**

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

id：

- 类型：字符串
- 默认值：无
- 描述：被查找数据的行ID，可为空，为空时返回对象是否存在

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**uploadFile**<div id="a9"></div>

上传文件到云端file表里面

uploadFile({params}, callback(ret, err))

#**params**

data：

- 类型：JSON对象
- 默认值：无
- 描述：提交的文件及相关数据，不能为空
- 内部字段：

```js
{
	file:			//文件对象，不能为空
	{
		url:''		//文件路径，不能为空
		name:''		//文件名
	},
	values:			//其它字段
	{
		
	}
};
```

report：

- 类型：布尔
- 默认值：false
- 描述：上传过程是否回调上传进度

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息，依赖于report字段，report为false时为上传完成时，服务器返回的数据

```js
report为true时内部字段：
{
	progress:			//上传进度，0.00-100.00
	state:				//上传状态，（0-上传中 1-上传成功 2-上传失败）
	body:				//上传完成时，服务器返回的数据
}
```

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
//report参数为true时：

var model = api.require('model');
model.uploadFile({
	report:true,
	data:{
		file:{
			name:'1.png',
			url:'widget://image/1.png'
		},
		values:{
			key1:'value1',
			key2:'value2'
		}
	}
},function(ret, err) {
    if (ret) {
        var state = ret.state;
        if (state == 1) {
            //上传完成
            var body = ret.body;
            if (body) {
                //处理服务器返回数据
            }
        } else {
        
        }
    } else {
        
    }
});


//report参数为false时：

var model = api.require('model');
model.uploadFile({
	report:false,
	data:{
		file:{
			name:'1.png',
			url:'widget://image/1.png'
		},
		values:{
			key1:'value1',
			key2:'value2'
		}
	}
},function(ret, err) {
    if (ret) {
        //处理服务器返回数据
    } else {
        
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**downloadFile**<div id="a10"></div>

下载文件

downloadFile({params}, callback(ret, err))

#**params**

url：

- 类型：字符串
- 默认值：无
- 描述：文件远程地址，url和id必须传一个

id：

- 类型：字符串
- 默认值：无
- 描述：已上传文件在云端file表中的行ID，url和id必须传一个

savePath：

- 类型：字符串
- 默认值：无
- 描述：存储路径，为空时使用自动创建的路径

report：

- 类型：布尔
- 默认值：false
- 描述：下载过程是否回调下载进度

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：下载信息
- 内部字段：

```js
{
	fileSize:			//文件大小
	progress:			//下载进度，0.00-100.00
	state:				//下载状态，（0-下载中 1-下载成功 2-下载失败）
	savePath:			//文件的本地保存路径
}
```

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
var model = api.require('model');
model.downloadFile({
	report:true,
	id:'asfdasfasfasfasf',
	savePath:'fs://1.png'
},function(ret, err) {
    if (ret) {
        var state = ret.state;
        if (state == 1) {
            //下载完成
            var savePath = ret.savePath;
            if (savePath) {
                
            }
        } else {
        
        }
    } else {
        
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
</div>


<div id="const-content">

<div class="outline">
[createQuery](#1)

[limit](#2)

[skip](#3)

[asc](#4)

[desc](#5)

[include](#6)

[whereEqual](#7)

[whereNotEqual](#8)

[whereLike](#9)

[whereUnLike](#10)

[whereStartWith](#11)

[whereEndWith](#12)

[whereExist](#13)

[whereNotExist](#14)

[whereContain](#15)

[whereContainAll](#16)

[whereNotContain](#17)

[whereGreaterThan](#18)

[whereGreaterThanOrEqual](#19)

[whereLessThan](#20)

[whereLessThanOrEqual](#21)

[justFields](#22)

[exceptFields](#23)
</div>

#**概述**
 query对象用于构建一个或多个查询条件，包含分页、排序、以及其它where语句等，设置查询条件后，传递给model对象的查询方法，以获取符合条件的记录。

#**createQuery**<div id="1"></div>

创建一个query对象

createQuery(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

字段：

```js
{
	qid：		//query对象的句柄ID，数字型
}
```

##示例代码

```js
var query = api.require('query');
query.createQuery(function(ret, err) {
    if (ret && ret.qid) {
        var queryId = ret.qid;
        //do something
    }
});
```

#补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**limit**<div id="2"></div>

设置查询返回结果限制为n条

limit({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：被限制的数目值，不能为空

##示例代码

```js
var query = api.require('query');
query.createQuery(function(ret, err){
    if(ret && ret.qid){
        var queryId = ret.qid;
        query.limit({qid:queryId, value:3});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**skip**<div id="3"></div>

设置查询返回结果中忽略前n条

skip({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：被忽略的数目值，不能为空

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**asc**<div id="4"></div>

设置查询返回结果按某列正序排列

asc({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：用于排序的列，不能为空

##补充说明

与desc互斥

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**desc**<div id="5"></div>

设置查询返回结果按某列倒序排列

desc({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：用于排序的列，不能为空

##补充说明

与asc互斥

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**include**<div id="6"></div>

设置查询返回结果中包含pointer指向的对象

include({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：pointer列名，不能为空

##示例代码

```js
var query = api.require('query');
query.createQuery(function (ret, err) {
    if (ret && ret.qid) {
        query.include({
            qid: ret.qid,
            column: 'pointer.column'
        });
    }
});
```

##补充说明

可设置多个

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereEqual**<div id="7"></div>

设置查询条件为某列等于某值

whereEqual({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，不能为空

##示例代码

```js
var query = api.require('query');
query.createQuery(function (ret, err) {
    if (ret && ret.qid) {
        query.whereEqual({
            qid: ret.qid,
            column: 'id',
            value: 'pointer.id'
        });
    }
});
```

##补充说明

可设置多个，与whereNotEqual互斥

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereNotEqual**<div id="8"></div>

设置查询条件为某列不等于某值

whereNotEqual({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，不能为空

##补充说明

可设置多个，与whereEqual互斥

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereLike**<div id="9"></div>

设置查询条件为某列内容中包含某值

whereLike({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，不能为空

##补充说明

可设置多个

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereUnLike**<div id="10"></div>

设置查询条件为某列内容中不包含某值

whereUnLike({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，不能为空

##补充说明

可设置多个

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereStartWith**<div id="11"></div>

设置查询条件为某列内容以某值开头

whereStartWith({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，不能为空

##补充说明

可设置多个

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereEndWith**<div id="12"></div>

设置查询条件为某列内容以某值结尾

whereUnLike({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，不能为空

##补充说明

可设置多个

#可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereExist**<div id="13"></div>

设置查询条件为某列内容不为空

whereExist({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

##补充说明

可设置多个

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereNotExist**<div id="14"></div>

设置查询条件为某列内容为空

whereNotExist({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

补充说明

可设置多个

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereContain**<div id="15"></div>

设置查询条件为某列内容中包含某值

whereContain({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：
- 
- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，不能为空

##补充说明

可设置多个，该列需为array型

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereContainAll**<div id="16"></div>

设置查询条件为某列内容中包含某几个值

whereContainAll({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串数组
- 默认值：无
- 描述：作为条件的多个值，不能为空

##补充说明

可设置多个，该列需为array型

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereNotContain**<div id="17"></div>

设置查询条件为某列内容中不包含某值

whereNotContain({params})

##arams

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，不能为空

##补充说明

可设置多个，该列需为array型

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereGreaterThan**<div id="18"></div>

设置查询条件为某列的内容大于某值

whereGreaterThan({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，数字或者date型，不能为空

##补充说明

可设置多个

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereGreaterThanOrEqual**<div id="19"></div>

设置查询条件为某列的内容大于等于某值

whereGreaterThanOrEqual({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，数字或者date型，不能为空

##补充说明

可设置多个

#可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereLessThan**<div id="20"></div>

设置查询条件为某列的内容小于某值

whereLessThan({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，数字或者date型，不能为空

##补充说明

可设置多个

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**whereLessThanOrEqual**<div id="21"></div>

设置查询条件为某列的内容小于等于某值

whereLessThanOrEqual({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：作为条件的列名，不能为空

value：

- 类型：字符串
- 默认值：无
- 描述：作为条件的值，数字或者date型，不能为空

##补充说明

可设置多个

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**justFields**<div id="22"></div>

设置查询仅返回需要的字段

justFields({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

value：

- 类型：字符串数组
- 默认值：无
- 描述：字段的值，不能为空

##补充说明

与exceptFields互斥

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**exceptFields**<div id="23"></div>

设置查询返回除某些字段以外的字段

exceptFields({params})

##params

qid：

- 类型：数字
- 默认值：无
- 描述：query对象句柄ID，由createQuery创建而来，不能为空

value：

- 类型：字符串数组
- 默认值：无
- 描述：字段的值，不能为空

##补充说明

与justFields互斥

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
</div>



<div id="evt-content">

<div class="outline">
[insert](#b1)

[count](#b2)

[findAll](#b3)

[deleteAll](#b4)
</div>

#**概述**
relation对象主要用于对一张表中数据类型为Relation的列进行操作

#**insert**<div id="b1"></div>

向对象的某关系列下插入一条内容

insert({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

id：

- 类型：字符串
- 默认值：无
- 描述：被插入对象ID，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：关系列的名称，对应服务器上的同名relation，不能为空

value：

- 类型：JSON对象
- 默认值：无
- 描述：插入的键值对，与服务器上class中键值对应，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**count**<div id="b2"></div>

查找对象某关系列下对应的数据总条数

count({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

id：

- 类型：字符串
- 默认值：无
- 描述：被查找对象ID，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：关系列的名称，对应服务器上的同名relation，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**findAll**<div id="b3"></div>

查找对象某关系列下对应的所有数据

findAll({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

id：

- 类型：字符串
- 默认值：无
- 描述：被查找对象ID，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：关系列的名称，对应服务器上的同名relation，不能为空

##callback(ret, err)

ret：

- 类型：JSON数组
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
var relation_m = api.require('relation');
relation_m.findAll({
    class: 'relation._class',
    id: 'relation.id',
    column: 'relation.column'
}, function (ret, err) {
    if (ret) {
        //do something
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**deleteAll**<div id="b4"></div>

删除对象某关系列下对应的所有数据

deleteAll({params}, callback(ret, err))

##params

class：

- 类型：字符串
- 默认值：无
- 描述：对象的名称，对应服务器上的同名class，不能为空

id：

- 类型：字符串
- 默认值：无
- 描述：被删除对象ID，不能为空

column：

- 类型：字符串
- 默认值：无
- 描述：关系列的名称，对应服务器上的同名relation，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
</div>


<div id="method-content">

<div class="outline">
[login](#c1)

[register](#c2)

[logout](#c3)

[updatePassword](#c4)
</div>

#**概述**
user对象提供用户相关操作，包括注册、登录、修改密码等

#**login**<div id="c1"></div>

登录

login({params}, callback(ret, err))

##params

username：

- 类型：字符串
- 默认值：无
- 描述：用户名，不能为空

password：

- 类型：字符串
- 默认值：无
- 描述：密码，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
var user = api.require('user');
user.login({
    username: 'name',
    password: '12345678'
}, function(ret, err) {
    if (ret) {
        //do something       
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**register**<div id="c2"></div>

注册

register({params}, callback(ret, err))

##params

username：

类型：字符串
默认值：无
描述：用户名，不能为空

password：

类型：字符串
默认值：无
描述：密码，不能为空

email：

类型：字符串
默认值：无
描述：邮箱，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
var user = api.require('user');
user.register({
    username: 'uname',
    password: '111111'
}, function(ret, err) {
    if (ret) {
        //do something        
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**logout**<div id="c3"></div>

注销登录

logout(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
var user = api.require('user');
user.logout(function(ret, err){
    if(ret){
        //do something        
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**updatePassword**<div id="c4"></div>

修改密码

updatePassword({params}, callback(ret, err))

##params

password：

- 类型：字符串
- 默认值：无
- 描述：密码，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 描述：成功信息

err：

- 类型：JSON对象
- 描述：错误信息

##示例代码

```js
var user = api.require('user');
user.updatePassword({
    password: 'newPwd'
}, function(ret, err) {
    if (ret) {
        //do it
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
