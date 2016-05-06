/*
Title: spModule
Description: spModule
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[writeData](#a1)

[readData](#a2)

[deleteData](#a3)

</div>

#**概述**

spModule封装了android的SharedPreferences，使用此模块可轻松实现简单数据储存读取等的功能

#**writeData**<div id="a1"></div>

储存更新数据

writeData({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：SharedPreferences文件名，不能为空

key：

- 类型：字符串
- 默认值：无
- 描述：键值，不能为空。

data：

- 类型：字符串
- 默认值：无
- 描述：内容，不能为空，对应key下的储存内容

type：

- 类型：数字
- 默认值：无
- 描述：不能为空，可选填0(字符串),1(布尔值),2(数字int),3(数字long)



##示例代码

```js
var spModule = api.require('spModule');


spModule.writeData({name:'文档',key:'姓名',data:'张三',type:0});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

#**readData**<div id="a2"></div>

读取数据

readData({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 默认值：无
- 描述：SharedPreferences文件名，不能为空

key：

- 类型：字符串
- 默认值：无
- 描述：键值，不能为空。

type：

- 类型：数字
- 默认值：无
- 描述：不能为空，可选填0(字符串),1(布尔值),2(数字int),3(数字long)

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	data:		//获取数据
}
```


##示例代码

```js
var spModule = api.require('spModule');


spModule.readData({name:'文档',key:'姓名',type:0},function(ret, err){api.alert("数据为："+ret.data);});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


#**deleteData**<div id="a3"></div>

删除数据

deleteData({params})

##params

name：

- 类型：字符串
- 默认值：无
- 描述：SharedPreferences文件名，不能为空

key：

- 类型：字符串
- 默认值：无
- 描述：键值，不能为空。






##示例代码

```js
var spModule = api.require('spModule');


spModule.deleteData({name:'文档',key:'姓名');
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本
