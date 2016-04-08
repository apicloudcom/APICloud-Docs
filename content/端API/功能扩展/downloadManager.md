/*
Title: downloadManager
Description: downloadManager
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[openManagerView](#a1)

[closeManagerView](#a2)

[enqueue](#a3)

[pause](#a4)

[resume](#a5)

[remove](#a6)

[query](#a7)

[openDownloadedFile](#a8)
</div>

#**概述**

通过 downloadManager 模块，能够对所有的下载进程进行管理，并可以通过界面来查看下载进度等信息，同时还提供压缩包解压、快速查看下载完成文件等功能

#**openManagerView**<div id="a1"></div>

打开下载管理界面

openManagerView({params}, callback(ret))

##params

title：

- 类型：字符串
- 默认值：下载管理
- 描述：显示在下载界面顶部栏的标题，不能为空

##callback(ret)

ret：

- 类型：JSON对象
- 描述：点击列表中下载完成项的回调

内部字段：

```js
{
	id:'',                          //下载记录id
	mimeType:'',                    //文件类型
	savePath:'',                    //下载文件的本地存储路径
	uncompressPath:''               //压缩文件解压缩后路径
	event:true                      //下载管理界面返回时的事件，布尔类型
}
```

##示例代码

```js
var downloadManager = api.require('downloadManager');
downloadManager.openManagerView({
	title: '下载管理'
},function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeManagerView**<div id="a2"></div>

关闭下载管理界面

closeManagerView()

##示例代码

```js
var downloadManager = api.require('downloadManager');
downloadManager.closeManagerView();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**enqueue**<div id="a3"></div>

开始一个下载

enqueue({params}, callback(ret, err))

##params

url：

- 类型：字符串
- 默认值：无
- 描述：资源地址，不能为空

savePath：

- 类型：字符串
- 默认值：无
- 描述：存储路径，为空时使用自动创建的路径

cache：

- 类型：布尔
- 默认值：true
- 描述：是否使用缓存

allowResume：

- 类型：布尔
- 默认值：false
- 描述：是否开启断点续传，需要服务器支持

uncompress：

- 类型：布尔
- 默认值：false
- 描述：下载完成时是否解压缩文件

headers：

- 类型：JSON对象
- 默认值：无
- 描述：请求头

mimeType：

- 类型：字符串
- 默认值：通过响应头获取
- 描述：被下载目标的类型（*/*）

title：

- 类型：字符串
- 默认值：通过资源地址截取
- 描述：展示在managerView列表中的文件标题

iconPath：

- 类型：字符串
- 默认值：无
- 描述：该项下载显示在managerView中对应的图标

networkTypes：

- 类型：字符串
- 默认值：all
- 描述：允许自动下载的网络环境，参考[网络环境](!Constant)常量

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	id:'123456'		//新下载记录的id
}
```

##示例代码

```js
var downloadManager = api.require('downloadManager');
downloadManager.enqueue({
	url: 'http://xxx.zip',
	savePath: 'fs://xxx.zip',
	cache: true,
	allowResume: true,
	title: '教程',
	networkTypes: 'all'
},function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


##pause<div id="a4"></div>

暂停下载

pause({params}, callback(ret, err))

##params

id：

- 类型：字符串
- 默认值：无
- 描述：下载记录的id，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:false,            //操作状态
	msg:''                   //操作失败时的描述
}
```

##示例代码

```js
var downloadManager = api.require('downloadManager');
downloadManager.pause({
	id: '123'
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**resume**<div id="a5"></div>

继续下载

resume({params}, callback(ret, err))

##params

id：

- 类型：字符串
- 默认值：无
- 描述：下载记录的id，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:false,		//操作状态
	msg:''           	//操作失败时的描述
}
```

##示例代码

```js
var downloadManager = api.require('downloadManager');
downloadManager.resume({
	id: '123'
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**remove**<div id="a6"></div>

删除下载

remove({params}, callback(ret, err))

##params

ids：

- 类型：数组
- 默认值：无
- 描述：下载记录的id数组，不能为空

deleteFiles：

- 类型：布尔
- 默认值：false
- 描述：是否同时删除本地文件

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	number:1          //成功完成删除操作的总数，没有则返回-1
}
```

##示例代码

```js
var downloadManager = api.require('downloadManager');
downloadManager.remove({
	ids: [ '123456', '1234567' ]
},function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**query**<div id="a7"></div>

查询下载状态

query({params}, callback(ret, err))

##params

ids：

- 类型：数组
- 默认值：无
- 描述：下载记录的id数组

status：

- 类型：数字
- 默认值：无
- 描述：下载状态，详见下载状态[下载状态](!Constant)常量

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	data:
	[{
		id:'123456',                  //下载id
    	status:1,                     //下载状态
		url:'',                       //资源地址
		savePath,                     //下载文件本地存储路径
		title:'教程',                  //下载文件标题
		totalSize:1000,               //文件总大小，单位byte
		finishSize:500,               //已完成下载大小，单位byte
		mimeType:'audio/mp4',         //文件类型
		iconPath:''                   //图片路径
		reason:''                     //当下载发生错误时，错误的描述。详见下载错误常量表
	}]
}
```

##示例代码

```js
var downloadManager = api.require('downloadManager');
downloadManager.query({
	ids: [ '123456', '1234567' ],
	status: 1
},function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

当两个查询条件均为空时，返回所有下载记录信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**openDownloadedFile**<div id="a8"></div>

打开下载文件

openDownloadedFile({params}, callback(ret, err))

##params

id：

- 类型：字符串
- 默认值：无
- 描述：下载记录的id，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:false,		//操作状态
	msg:''           	//操作失败时的描述
}
```

##示例代码

```js
var downloadManager = api.require('downloadManager');
downloadManager.openDownloadedFile({
	id: '123456'
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
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
[网络环境](#1)

[下载状态](#2)

[下载错误](#3)
</div>

#**网络环境**<div id="1"></div>

网络环境

##取值范围：

- mobile        //手机网络
- wifi          //wifi网络
- all           //手机和wifi网络

#**下载状态**<div id="2"></div>

下载状态

##取值范围：

- 0             //等待下载
- 1             //正在下载
- 2             //暂停状态，等待恢复或被重新唤醒
- 3             //下载成功
- 4             //下载发生错误

#**下载错误**<div id="3"></div>

下载错误

##取值范围：
- 1000          //未知错误
- 1001          //存储已满
- 1002          //未发现存储设备
- 1003          //目标资源发生了重定向
- 1004          //网络资源错误
