/*
Title: contacts
Description: contacts
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<div class="outline">
[select](#m1)

[add](#m2)

[delete](#m3)

[update](#m4)

[move](#n2)

[query](#m5)

[queryByKeyword](#m7)

[queryByPage](#n1)

[createGroup](#m6)

[deleteGroup](#m11)

[queryGroups](#m8)

[queryByGroupId](#m9)
</div>

#**概述**

contacts 模块封装了系统通讯录的相关接口；可实现联系人的增、删、改、查的操作，创建、管理分组、移动联系人等功能；用于读取或管理通讯录联系人的数据。**contacts 模块是 contact 模块的优化版。注意在 Android 平台上使用此模块云编译时请添加通讯录访问权限**

<div id="m1"></div>
#**select**

打开系统通讯录界面，选择单个联系人，返回已选的联系人信息

select(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,                //布尔型；true||false
    id: 0,                       //数字类型；系统分配的联系人 id
    lastName: '',                //字符串类型；联系人姓氏，若该联系人此信息缺少则本字段为undefine
    firstName: '',               //字符串类型；联系人名字，若该联系人此信息缺少则本字段为undefine
    middleName: '',              //字符串类型；联系人中间名，若该联系人此信息缺少则本字段为undefine
    prefix: '',                  //字符串类型；名称前缀，若该联系人此信息缺少则本字段为undefine
    suffix: '',                  //字符串类型；名称后缀，若该联系人此信息缺少则本字段为undefine
    fullName: '',                //字符串类型；联系人全名，若该联系人此信息缺少则本字段为undefine
    phones: [{'工作': '10086'}], //数组类型；联系人电话组成的数组
                                 //内部字段：[{"标签": '号码'}]                    
    email: '',                   //字符串类型；邮箱
    company: '',                 //字符串类型；公司
    title: '',                   //字符串类型；职位
    address: {                   
        City: '',       	     //字符串类型；城市
        Country: '',             //字符串类型；国家
        State: '',               //字符串类型；省份
        Street: '',              //字符串类型；街道
        ZIP: '100020'            //字符串类型；邮编
    },
    note: '',                    //字符串类型；备注
    groupId: 1,                  //数字类型；联系人在通讯录中所属分组 id
    groupName: ''                //字符串类型；所在分组的名字
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本app访问通讯录）
                 0：（获取成功）
                 1：（用户取消）
}
```

##示例代码

```js
var contacts = api.require('contacts');
contacts.select(function( ret, err ){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>
#**add**

向通讯录添加一个联系人，所有参数不可同时为空。

add({params}, callback(ret, err))

##params

groupId：

- 类型：数字
- 描述：（可选项）分组 id，若不传则表示未分组

lastName：

- 类型：字符串
- 描述：（可选项）联系人姓氏

firstName：

- 类型：字符串
- 描述：（可选项）联系人名字

middleName：

- 类型：字符串
- 描述：（可选项）联系人中间名

prefix：

- 类型：字符串
- 描述：（可选项）联系人名称前缀

suffix：

- 类型：字符串
- 描述：（可选项）联系人名称后缀

phones：

- 类型：数组
- 描述：（可选项）联系人电话组成的数组
- 内部字段：

```js
//数组类型；内部字段：[{"标签": '号码'}]
[{
    '工作': '13512345678'         
},{
    '家庭': '13512345678'
}]
```

email：

- 类型：字符串
- 描述：（可选项）联系人邮箱

company：

- 类型：字符串
- 描述：（可选项）联系人公司

title：

- 类型：字符串
- 描述：（可选项）联系人职位

address：

- 类型：JSON 对象
- 描述：（可选项）联系人地址
- 内部字段：

```js
{
    City: '',              //（可选项）字符串类型；城市；
    Country: '',           //（可选项）字符串类型；国家；
    State: '',             //（可选项）字符串类型；省份；
    Street: '',            //（可选项）字符串类型；街道；
    ZIP: ''                //（可选项）字符串类型；邮编；
}
```

note：

- 类型：字符串
- 描述：（可选项）联系人备注

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,         //布尔型；true||false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本app访问通讯录）
                 0：（添加成功）
                 1：（分组不存在）
}
```
##示例代码

```js
var contacts = api.require('contacts');
contacts.add({
	groupId: 1,
	lastName: '张',
    firstName: '三丰',
	middleName: '太极',
    prefix: '他',
	suffix: '牛',
	phones: [{
        '住宅': '12345678'
    },{
        '工作': '87654321'
    }],
    email: 'zhengcuan@api.com',
    company: '柚子科技',
    title: '工程师',
	address: {
		Country: '中国',
		State: '北京',
		City: '北京市',
		Street: '鸟巢街',
		ZIP: '100000'
	},
	note: '无'
}, function(ret, err){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>
#**delete**

从通讯录删除一个或多个联系人

delete({params}, callback(ret, err))

##params

ids：

- 类型：数组, 数组元素为整型
- 描述：联系人的 id 组成的数组，若传入的 id 不存在，则忽略此id

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true           //布尔型；true||false
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本app访问通讯录，Android 平台忽略此错误码）
                 0：（删除成功）
}
```

##示例代码

```js
var contacts = api.require('contacts');
contacts.delete({
	ids: [1, 2]
}, function(ret, err){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>
#**update**

根据 id 更新通讯录的联系人信息

update({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：联系人 id

lastName：

- 类型：字符串
- 描述：（可选项）联系人的姓氏

firstName：

- 类型：字符串
- 描述：（可选项）联系人名字

middleName：

- 类型：字符串
- 描述：（可选项）联系人中间名

prefix：

- 类型：字符串
- 描述：（可选项）联系人名称前缀

suffix：

- 类型：字符串
- 描述：（可选项）联系人名称后缀

phones：

- 类型：数组
- 描述：（可选项）联系人电话组成的数组，**注意：若本参数不为空，则重置已存在的所有电话及其标签**
- 内部字段：

```js 
//数组类型；内部字段：[{"标签": '号码'}]
[{
    '工作': '10086'
}]
```

email：

- 类型：字符串
- 描述：（可选项）联系人邮箱

company：

- 类型：字符串
- 描述：（可选项）联系人公司

title：

- 类型：字符串
- 描述：（可选项）联系人职位

address：

- 类型：JSON 对象
- 描述：（可选项）联系人地址
- 内部字段：

```js
{
    City: '',              //（可选项）字符串类型；城市；
    Country: '',           //（可选项）字符串类型；国家；
    State: '',             //（可选项）字符串类型；省份；
    Street: '',            //（可选项）字符串类型；街道；
    ZIP: ''                //（可选项）字符串类型；邮编；
}
```

note：

- 类型：字符串
- 描述：（可选项）联系人备注

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: true        //布尔型；true||false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本应用访问通讯录）
                 0：（更新成功）
                 1：（联系人 id 不存在）
}
```

##示例代码

```js
var contacts = api.require('contacts');
contacts.update({
    id: 1,
    lastName: '李',
    firstName: '四',
	middleName: 'Cloud',
    prefix: 'API',
	suffix: '柚子',
    phones: [{
        '住宅': '12345678'
    },{
        '工作': '87654321'
    }],
    email: 'zhengcuan@api.com',
    company: '柚子科技',
    title: '工程师',
    address: {
        Country: '中国',
        State: '北京',
        City: '北京市',
        Street: '鸟巢街',
        ZIP: '100000'
    },
    note: '无'
}, function(ret, err){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="n2"></div>
#**move**

根据 id 移动联系人至指定分组

move({params}, callback(ret, err))

##params

id：

- 类型：数字
- 描述：联系人 id

groupId：

- 类型：数字
- 描述：联系人的分组 id；若分组不存在则不移动分组

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true       //布尔型；true||false
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本应用访问通讯录）
                 0：（移动成功）
                 1：（联系人 id 不存在）
                 2：（所传分组 id 不存在）
}
```
##示例代码

```js
var contacts = api.require('contacts');
contacts.move({
    id: 10,
    groupId: 20
}, function(ret, err){
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>
#**query**

根据联系人 id 查找联系人

query({params}, callback(ret, err))

##params

ids：

- 类型：数组
- 描述：联系人 id 组成的数组，若 id 不存在则不处理

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,                   //布尔型；true||false
    contacts: [{                    
        id: 1,                      //数字类型；联系人的 id
	    lastName: '',                //字符串类型；联系人姓氏，若该联系人此信息缺少则本字段为undefine
	    firstName: '',               //字符串类型；联系人名字，若该联系人此信息缺少则本字段为undefine
	    middleName: '',              //字符串类型；联系人中间名，若该联系人此信息缺少则本字段为undefine
	    prefix: '',                  //字符串类型；名称前缀，若该联系人此信息缺少则本字段为undefine
	    suffix: '',                  //字符串类型；名称后缀，若该联系人此信息缺少则本字段为undefine
       fullName: '',                //字符串类型；联系人全名，若该联系人此信息缺少则本字段为undefine
        phones: [{'工作', '123'}],  //数组类型；联系人电话组成的数组
                                    //内部字段：[{"标签":"号码"}]
        email: '',                  //字符串类型；邮箱
        company: '',                //字符串类型；公司
        title: '',                  //字符串类型；职位
        address: {
            City: '',               //字符串类型；城市
            Country: '',            //字符串类型；国家
            State: '',              //字符串类型；省份
            Street: '',             //字符串类型；街道
            ZIP: ''                 //字符串类型；邮编
        },
        note: '',                   //字符串类型；备注
        groupId: 1,                 //数字类型；联系人所属分组的 id
        groupName: ''               //字符串类型；所在分组的名字
    }]
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本应用访问通讯录，Android 平台忽略此错误码）
                 0：（获取成功）
}
```
##示例代码

```js
var contacts = api.require('contacts');
contacts.query({
    ids: [1, 2]
}, function(ret, err){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m7"></div>
#**queryByKeyword**

根据关键字从通讯录查找联系人

queryByKeyword({params}, callback(ret, err))

##params

keyword：

- 类型：字符串
- 描述：要查询的关键字 **注意：仅搜索 lastName 和 firstName 包含的关键字**

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,                   //布尔型；true||false
    contacts: [{                    
        id: 1,                      //数字类型；联系人的 id
	    lastName: '',                //字符串类型；联系人姓氏，若该联系人此信息缺少则本字段为undefine
	    firstName: '',               //字符串类型；联系人名字，若该联系人此信息缺少则本字段为undefine
	    middleName: '',              //字符串类型；联系人中间名，若该联系人此信息缺少则本字段为undefine
	    prefix: '',                  //字符串类型；名称前缀，若该联系人此信息缺少则本字段为undefine
	    suffix: '',                  //字符串类型；名称后缀，若该联系人此信息缺少则本字段为undefine
       fullName: '',                //字符串类型；联系人全名，若该联系人此信息缺少则本字段为undefine
        phones: [{'工作', '123'}],  //数组类型；联系人电话组成的数组
                                    //内部字段：[{"标签":"号码"}]
        email: '',                  //字符串类型；邮箱
        company: '',                //字符串类型；公司
        title: '',                  //字符串类型；职位
        address: {
            City: '',               //字符串类型；城市
            Country: '',            //字符串类型；国家
            State: '',              //字符串类型；省份
            Street: '',             //字符串类型；街道
            ZIP: ''                 //字符串类型；邮编
        },
        note: '',                   //字符串类型；备注
        groupId: 1,                 //数字类型；联系人在通讯录所属分组的 id
        groupName: ''               //字符串类型；所在分组的名字
    }]
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本应用访问通讯录，Android 平台忽略此错误码）
                 0：（获取成功）
}
```
##示例代码

```js
var contacts = api.require('contacts');
contacts.queryByKeyword({
    keyword: '孙'
}, function(ret, err){
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="n1"></div>
#**queryByPage**

根据页码查找指定数量的联系人

queryByPage({params}, callback(ret, err))

##params

count：

- 类型：数字
- 描述：（可选项）每页联系人的数量，若不传则返回全部联系人，**不建议不传本参数**

pageIndex：

- 类型：数字
- 描述：（可选项）联系人的分页索引
- 默认值：0

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,                   //布尔型；true||false
    total: 100,                     //数字类型；联系人的总数
    pages: 10,                      //数字类型；联系人总页数
    contacts: [{                    
        id: 1,                      //数字类型；联系人的 id
	    lastName: '',                //字符串类型；联系人姓氏，若该联系人此信息缺少则本字段为undefine
	    firstName: '',               //字符串类型；联系人名字，若该联系人此信息缺少则本字段为undefine
	    middleName: '',              //字符串类型；联系人中间名，若该联系人此信息缺少则本字段为undefine
	    prefix: '',                  //字符串类型；名称前缀，若该联系人此信息缺少则本字段为undefine
	    suffix: '',                  //字符串类型；名称后缀，若该联系人此信息缺少则本字段为undefine
       fullName: '',                //字符串类型；联系人全名，若该联系人此信息缺少则本字段为undefine
        phones: [{'工作', '123'}],  //数组类型；联系人电话组成的数组
                                    //内部字段：[{"标签":"号码"}]
        email: '',                  //字符串类型；邮箱
        company: '',                //字符串类型；公司
        title: '',                  //字符串类型；职位
        address: {
            City: '',               //字符串类型；城市
            Country: '',            //字符串类型；国家
            State: '',              //字符串类型；省份
            Street: '',             //字符串类型；街道
            ZIP: ''                 //字符串类型；邮编
        },
        note: '',                   //字符串类型；备注
        groupId: 1,                 //数字类型；联系人所属分组的 id
        groupName: ''               //字符串类型；所在分组的名字
    }]
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本应用访问通讯录，Android 平台忽略此错误码）
                 0：（获取成功）
}
```
##示例代码

```js
var contacts = api.require('contacts');
contacts.queryByPage({
    count: 20,
    pageIndex: 0
}, function(ret, err){
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>
#**createGroup**

创建分组

createGroup({params}, callback(ret, err))

##params

groupName：

- 类型：字符串
- 描述：分组名

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,         //布尔型；true||false
    groupId: 1            //创建成功返回的分组 id
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本应用访问通讯录，Android 平台忽略此错误码）
                 0：（创建成功）
}
```
##示例代码

```js
var contacts = api.require('contacts');
contacts.createGroup({
    groupName: '同学'
}, function(ret, err){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m11"></div>
#**deleteGroup**

删除分组，只删除分组，不删除其中的联系人

deleteGroup({params}, callback(ret, err))

##params

groupId：

- 类型：数字
- 描述：分组 id

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true         //布尔型；true||false
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本应用访问通讯录，Android 平台忽略此错误码）
                 0：（删除成功）
                 1：（分组不存在）
}
```
##示例代码

```js
var contacts = api.require('contacts');
contacts.deleteGroup({
    groupId: 1
}, function(ret, err){
   if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m8"></div>
#**queryGroups**

获取所有分组信息

queryGroups(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true,       //布尔型；true||false
    groups: [{         
        name: '',       //字符串类型；分组名
        id: 1           //数字类型；分组 id 
    }]
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本应用访问通讯录，Android 平台忽略此错误码）
                 0：（获取成功）
}
```
##示例代码

```js
var contacts = api.require('contacts');
contacts.queryGroups(function( ret, err ){
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m9"></div>
#**queryByGroupId**

根据分组 id 查找联系人

queryByGroupId({params}, callback(ret, err))

##params

groupId：

- 类型：数字
- 描述：（可选项）要查找的分组 id

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true                    //布尔型；true||false
    groups: [{
        id: 1,                      //数字类型；联系人的 id
	    lastName: '',                //字符串类型；联系人姓氏，若该联系人此信息缺少则本字段为undefine
	    firstName: '',               //字符串类型；联系人名字，若该联系人此信息缺少则本字段为undefine
	    middleName: '',              //字符串类型；联系人中间名，若该联系人此信息缺少则本字段为undefine
	    prefix: '',                  //字符串类型；名称前缀，若该联系人此信息缺少则本字段为undefine
	    suffix: '',                  //字符串类型；名称后缀，若该联系人此信息缺少则本字段为undefine
       fullName: '',                //字符串类型；联系人全名，若该联系人此信息缺少则本字段为undefine
        phones: [{'工作', '123'}],  //数组类型；联系人电话组成的数组
                                    //内部字段：[{"标签":"号码"}]
        email: '',                  //字符串类型；邮箱
        company: '',                //字符串类型；公司
        title: '',                  //字符串类型；职位
        address: {
            City: '',               //字符串类型；城市
            Country: '',            //字符串类型；国家
            State: '',              //字符串类型；省份
            Street: '',             //字符串类型；街道
            ZIP: ''                 //字符串类型；邮编
        },
        note: '',                   //字符串类型；备注
        groupId: 1,                 //数字类型；联系人在通讯录所属分组的 id
        groupName: ''               //字符串类型；所在分组的名字
    }]
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code: 0      //数字类型；
                 //错误码：
                 -1：（用户未授权本应用访问通讯录，Android 平台忽略此错误码）
                 0：（获取成功）
                 1：（分组不存在）
}
```
##示例代码

```js
var contacts = api.require('contacts');
contacts.queryByGroupId({
	groupId: 1
},function(ret,err){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
