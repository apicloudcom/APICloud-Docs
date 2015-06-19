/*
Title: contact
Description: contact
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[openContact](#1)

[addContact](#2)

[deleteContact](#3)

[updateContact](#4)

[queryContact](#5)

[addGroup](#6)

[queryContactByKey](#7)

[queryGroups](#8)

[queryContactByGroupId](#9)

[updateGroupName](#10)

[deleteGroup](#11)
</div>

#**概述**

contact模块封装了系统通讯录的相关接口，通过此模块可实现对系统通讯录的联系人增删改查操作，将底层负责的访问通讯录代码简单成一个个小接口，让开发者轻松访问通讯录

#**openContact**<div id="1"></div>

打开系统通讯录界面

openContact(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:true                 //操作成功状态值
    id:                         //联系人id
    name:                       //联系人姓名，由通讯录里该联系人的姓和名组成
    phones:                     //联系人电话组成的数组，内部字段:[{"标签":"号码"}]
    email:                      //邮箱
    company:                    //公司
    title:                      //职位
    address：
    {
        City:       	        //城市
        Country:                //国家
        CountryCode:            //国家缩写
        State:                  //省份
        Street:                 //街道
        ZIP:                    //邮编
    }
    note:                       //备注
    groupId:                    //联系人在通讯录中所属分组的id（为空时表示未分组）
    groupName:                  //所在分组的名字（为空时表示未分组）
}
```

err：

- 类型：json对象
- 内部字段：

```js
{
	msg      		 //报错信息
}
```

##示例代码

```js
var contact = api.require('contact');
contact.openContact(function(ret,err) {
	if(ret.status) {
		var array = ret.phones;
		var firstnum = array[0];
		var secondnum = array[1];
		var thirdnum = array[2];
	} else{
		api.alert({msg:'用户取消'});
	}
});
```

##补充说明

获取联系人信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addContact**<div id="2"></div>

往通讯录添加一个联系人

addContact({params}, callback(ret, err))

##params

lastName：

- 类型：字符串
- 默认值：未命名
- 描述：（可选项）联系人姓

firstName：

- 类型：字符串
- 默认值：未命名
- 描述：（可选项）联系人名

groupId：

- 类型：数字
- 默认值：无
- 描述：（可选项）分组id
- 备注：若不传则表示未分组

phones：

- 类型：JSON数组对象
- 默认值：无
- 描述：（可选项）联系人电话JSON对象组成的数组对象
- 内部字段：

```js
[{
    label:'',
    phone:''
}]
```

email：

- 类型：字符串
- 默认值：无
- 描述：（可选项）联系人邮箱

company：

- 类型：字符串
- 默认值：无
- 描述：（可选项）联系人公司

title：

- 类型：字符串
- 默认值：无
- 描述：（可选项）联系人职位

address：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）联系人地址组成的JSON对象
- 内部字段：

```js
    {
        City:       	        //（可选项）城市，字符串类型，默认空
        Country:                //（可选项）国家，字符串类型，默认空
        CountryCode:            //（可选项）国家缩写，字符串类型，默认空
        State:                  //（可选项）省份，字符串类型，默认空
        Street:                 //（可选项）街道，字符串类型，默认空
        ZIP:                    //（可选项）邮编，字符串类型，默认空
    }
```

note：

- 类型：字符串
- 默认值：无
- 描述：（可选项）联系人备注

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:true           //操作成功状态值
}
```

##示例代码

```js
var contact = api.require('contact');
contact.addContact({
	groupId:1,
	firstName:'张',
	lastName:'三',
	phones:[{label:'住宅',phone:'123'},{label:'工作',phone:'456'}],
	address: {
		Country:'中国',
		State:'北京',
		City:'北京市',
		Street:'鸟巢街',
		ZIP:'100000'
	},
	email:'zhengcuan.sun@api.com',
	company:'柚子科技',
	title:'工程师',
	note:'无'
},function(ret,err) {
	if(ret.status) {
		api.alert({msg:'添加成功'});
	} else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

添加一个联系人

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**deleteContact**<div id="3"></div>

从通讯录删除多个联系人

deleteContact({params}, callback(ret, err))

##params

ids：

- 类型：数组
- 默认值：无
- 描述：要删除的联系人的id（数字）组成的数组

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:true           //操作成功状态值
}
```

##示例代码

```js
var contact = api.require('contact');
contact.deleteContact({
	ids:[1,2]
},function(ret,err) {
	if(ret.status) {
		api.alert({msg:'删除成功'});
	}else{
		api.alert({msg:'删除失败'});
	} 
});
```

##补充说明

删除指定联系人信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**updateContact**<div id="4"></div>

修改通讯录里的一个联系人

updateContact({params}, callback(ret, err))

##params

id：

- 类型：数字
- 默认值：无
- 描述：要修改的联系人的id

groupId：

- 类型：数字
- 默认值：原值
- 描述：（可选项）要修改的联系人的分组id
- 备注：若不传或传空则不移动分组，若id为存在合法值则移动该联系人

lastName：

- 类型：字符串
- 默认值：原值
- 描述：（可选项）联系人的姓

firstName：

- 类型：字符串
- 默认值：原值
- 描述：（可选项）联系人名

phones：

- 类型：JSON对象数组
- 默认值：原值
- 描述：（可选项）联系人电话组成的JSON对象数组
- 备注：若不传则不修改此属性
- 内部字段：[{
    "标签":"号码"
 }]

email：

- 类型：字符串
- 默认值：无
- 描述：（可选项）联系人邮箱

company：

- 类型：字符串
- 默认值：无
- 描述：（可选项）联系人公司

title：

- 类型：字符串
- 默认值：无
- 描述：（可选项）联系人职位

address：

- 类型：JSON对象
- 默认值：无
- 描述：（可选项）联系人地址组成的JSON对象
- 内部字段：

```js
    {
        City:       	        //（可选项）城市，字符串类型，默认空
        Country:                //（可选项）国家，字符串类型，默认空
        CountryCode:            //（可选项）国家缩写，字符串类型，默认空
        State:                  //（可选项）省份，字符串类型，默认空
        Street:                 //（可选项）街道，字符串类型，默认空
        ZIP:                    //（可选项）邮编，字符串类型，默认空
    }
```

note：

- 类型：字符串
- 默认值：无
- 描述：（可选项）联系人备注

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:true           //操作成功状态值
}
```

##示例代码

```js
var contact = api.require('contact');
contact.updateContact({
    id:1,
    firstName:'张',
    lastName:'三',
    phones:[{label:'住宅',phone:'124'},{label:'工作',phone:'346'}],
    address: {
         Country:'',
         State:'',
         City:'',
         Street:'',
         ZIP:''
	},
	email:'',
	company:'',
	title:'',
	note:''
},function(ret,err) {
	if(ret.status) {
		api.alert({msg:'修改成功'});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明
修改指定联系人信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**queryContact**<div id="5"></div>

从通讯录查找联系人

queryContact({params}, callback(ret, err))

##params

ids：

- 类型：数组对象
- 默认值；无
- 描述：（可选项）要查找的联系人的id（数字）组成的数组
- 备注：若不传则返回全部联系人信息

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
contacts:                       //数组对象
[{
    status:true                 //操作成功状态值
    id：                        //联系人的id
    name：                      //联系人名字，由通讯录里联系人的姓和名组成
    phones：                    //联系人电话组成的数组，内部字段:[{"标签":"号码"}]
    email：                     //邮箱
    company：                   //公司
    title：                     //职位
    address：
    {
        City:                   //城市
        Country:                //国家
        CountryCode:            //国家缩写
        State:                  //省份
        Street:                 //街道
        ZIP:                    //邮编
    }
    note：                      //备注
    groupId：                   //联系人在通讯录中所属分组的id（为空时表示未分组）
    groupName：                 //所在分组的名字（为空时表示未分组）
}]
```

##示例代码

```js
var contact = api.require('contact');
contact.queryContact({
    ids:[1]
},function(ret,err) {
	if(ret.status) {
		var array =ret.contacts;
		var first = array[0]; 
		var arrayPho = first.phones;
		var firstnum = arrayPho[0];
		var secondnum = arrayPho[1];
		var thirdnum = arrayPho[2]; 
	} else{
		api.alert({msg:'获取失败'});
	}
});
```

##补充说明

获取指定联系人信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addGroup**<div id="6"></div>

创建分组

addGroup({params}, callback(ret, err))

##params

name：

- 类型：字符串
- 默认值；无
- 描述：分组名

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:true               //操作成功状态值
    id：                      //创建成功返回分组的id
}
```

##示例代码

```js
var contact = api.require('contact');
contact.addGroup({
    name:'同学'
},function(ret,err){
	if(ret.status){
		api.alert({msg:'分组创建完成'+'*'+ret.id});
	}else{
		api.alert({msg:err.msg});
	} 
});
```

##补充说明

创建分组

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**queryContactByKey**<div id="7"></div>

根据关键字从通讯录查找联系人

queryContactByKey({params}, callback(ret, err))

##params

key：

- 类型：字符串
- 默认值；无
- 描述：要查询的关键字

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
contacts:                       //数组对象
[{
    status:true                 //操作成功状态值
    id：                        //联系人的id
    name：                      //联系人名字，由通讯录里联系人的姓和名组成
    phones：                    //联系人电话组成的数组，内部字段:[{"标签":"号码"}]
    email：                     //邮箱
    company：                   //公司
    title：                     //职位
    address：
    {
        City:                   //城市
        Country:                //国家
        CountryCode:            //国家缩写
        State:                  //省份
        Street:                 //街道
        ZIP:                    //邮编
    }
    note：                      //备注
    groupId：                   //联系人在通讯录中所属分组的id（为空时表示未分组）
    groupName：                 //所在分组的名字（为空时表示未分组）
}]
```

##示例代码

```js
var contact = api.require('contact');
contact.queryContactByKey({
	key:'孙'
},function(ret,err) {
	if(ret.status) {   
		var array = ret.contacts;
		var first = array[0];
		var arrayPho = first.phones;
		var firstnum = arrayPho[0];
		var secondnum = arrayPho[1];
		var thirdnum = arrayPho[2];
	}else{
		api.alert({msg:'获取失败'});
	}
});
```

##补充说明

根据关键字获取联系人信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**queryGroups**<div id="8"></div>

获取所有分组信息

queryGroups(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON数组对象
- 内部字段：

```js
{
    groups:                 //分组名所组成的数组
    [{
        name:               //分组名
        id:                 //分组的id 
    }]
}
```

##示例代码

```js
var contact = api.require('contact');
contact.queryGroups(function(ret,err) {
    if(ret.status){
		var array =ret.groups;
		var first = array[0];
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

获取所有分组信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**queryContactByGroupId**<div id="9"></div>

查找一个分组内的联系人

queryContactByGroupId({params}, callback(ret, err))

##params

id：

- 类型：字符串对象
- 默认值；无
- 描述：（可选项）要查找的分组的id
- 备注：若不传则则返回全部联系人信息

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:true                 //操作成功状态值
    id:                         //联系人id
    name:                       //联系人姓名，由通讯录里该联系人的姓和名组成
    phones:                     //联系人电话组成的数组，内部字段:[{"标签":"号码"}]
    email:                      //邮箱
    company:                    //公司
    title:                      //职位
    address：
    {
        City:       	        //城市
        Country:                //国家
        CountryCode:            //国家缩写
        State:                  //省份
        Street:                 //街道
        ZIP:                    //邮编
    }
    note:                       //备注
    groupId:                    //联系人在通讯录中所属分组的id（为空时表示未分组）
    groupName:                  //所在分组的名字（为空时表示未分组）
}
```
##示例代码

```js
var contact = api.require('contact');
contact.findContact({
	id:1
},function(ret,err) {
	if(ret.status) {
		var array = ret.names;
		var first = array[0];
		var arrayPho = first.phones;
		var firstnum = arrayPho[0];
		var secondnum = arrayPho[1];
		var thirdnum = arrayPho[2];
	} else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

获取指定分子内联系人信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**updateGroupName**<div id="10"></div>

修改分组名

updateGroupName({params}, callback(ret, err))

##params

id：

- 类型：数字
- 默认值；无
- 描述：要修改的分组的id

name：

- 类型：字符串
- 默认值；无
- 描述：要修改成为的分组名

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:true           //操作成功状态值
}
```

##示例代码

```js
var contact = api.require('contact');
contact.updateGroupName({
	id:1,
	name:'同学'
},function(ret,err){
	if(ret.status){
		api.alert({msg:'分组修改完成'});
	}else{
		api.alert({msg:err.msg});
	}
});
```
##补充说明

目前ios暂不支持此接口，可通过删除分组，然后再创建来实现此功能

##可用性

Android系统

可提供的1.0.0及更高版本


#**deleteGroup**<div id="11"></div>

删除分组

deleteGroup({params}, callback(ret, err))

##params

id：

- 类型：数字
- 默认值；无
- 描述：要删除的分组的id

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:           //操作成功状态值
}
```

##示例代码

```js
var contact= api.require('contact');
contact.deleteGroup({
	id:1
},function(ret,err){
	if(ret.status){
		api.alert({msg:'分组删除完成'});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##补充说明

删除分组

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
