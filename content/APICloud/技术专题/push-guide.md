/*
Title: 推送技术指南
Description: 推送技术指南
Sort: 10
*/


[推送准备](#1)

- [编译正式版App,并安装到手机](#0)
- [iOS推送证书](#2)
- [推送设置](#3)

[新建推送消息](#4)
- [即时通知](#5)
- [定时通知](#6)

[查看推送统计](#7)
- [推送概览与推送记录](#8)


[接收推送消息](#10)
- [push模块](#11)
- [绑定推送](#12)
- [设置群组](#13)
- [获取推送消息](#14)


[使用推送API](#15)


##参考视频  

入门概念篇第七节（如何使用APICloud云端应用服务）：http://docs.apicloud.com/APICloud/videos-and-codes


#**推送准备**<div id="1"></div>



##编译正式版App,并安装到手机<div id="0"></div>
推送只对正式版App有效，请先创建或上传Android ，ios 证书，然后编译App正式版。 把编译的正式版App安装到手机。

##iOS推送证书<div id="2"></div>


iOS推送证书需要从苹果开发网站上面创建，然后再转换成服务器端专用p12格式证书，详情参考[iOS证书申请教程](http://docs.apicloud.com/APICloud/%E6%8A%80%E6%9C%AF%E4%B8%93%E9%A2%98/iOS-License-Application-Guidance)


 
##推送设置<div id="3"></div>
进入APICloud官网你的应用页面，在侧边栏‘应用服务’里面选择‘推送’，进入推送页面。如下图：

![图片说明](/img/push/push1.png)

然后在页面里选择右上角的设置按钮，弹出推送证书设置页面，注意开启状态，然后<strong>上传之前创建的推送证书</strong>，并且输入密码，保存。同时，在此页面还可以设置离线消息的保存时间，之前未收到通知的设备在离线消息设定时间以内上线后会收到通知消息。 如下图：

![图片说明](/img/push/push2.png)
 
#**新建推送消息**<div id="4"></div>

##即时通知<div id="5"></div>

选择右上角的新建推送，在展开的发送页面中，选择推送类型是通知或消息，输入标题和内容，选择推送群组和平台，点击发送，通知将立即进入发送状态。

![图片说明](/img/push/push3.png)
 
##定时通知<div id="6"></div>

此项功能暂未开启。

 
#**查看推送统计**<div id="7"></div>

##推送概览与推送记录<div id="8"></div>

在推送页面的顶部‘推送概览’页，可以查看到推送条数和终端数目等相关数据。

在推送概览下面是推送记录页面，包括定时发送、正在发送和发送成功等状态的推送消息记录。

![图片说明](/img/push/push4.png)

#**接收推送消息**<div id="10"></div>

##push模块<div id="11"></div>

在APICloud网站上面创建应用时，push模块默认已经被引入。push模块提供了绑定用户，加入群组，监听消息等接口。 详情参考[push](http://docs.apicloud.com/%E7%AB%AFAPI/%E4%BA%91%E6%9C%8D%E5%8A%A1%E5%AF%B9%E6%8E%A5/push)文档。

##绑定推送<div id="12"></div>

push模块提供了bind方法，将来自业务系统的用户信息绑定至推送服务器，如果不需要关联业务系统用户信息，则可以不调用bind方法。详情参考push文档bind方法。

示例代码：

```
//  绑定用户
var push = api.require('push');
push.bind({
    userName:'testName',
    userId:'testId'
},function(ret,err){
    if(ret.status){
        api.alert({msg:'绑定成功'});
    }else{
        api.alert({msg:err.msg});
    }
});


// 解绑用户
var push = api.require('push');
push.unbind({
    userName:'testName',
    userId:'testId'
},function(ret,err){
    if(ret.status){
        api.alert({msg:'解除绑定成功'});
    }else{
        api.alert({msg:err.msg});
    }
});
```

##设置群组<div id="13"></div>

设备需要绑定到相应的群组才能收到推送消息，在应用启动时，APICloud会自动绑定设备到默认群组，push模块的joinGroup方法可以将设备添加到指定群组，leavelGroup则将设备从指定群组中移除。详情参考push文档joinGroup、leavelGroup方法。


```
// 加入群组
var push = api.require('push');
push.joinGroup({
    groupName:'department'
},function(ret,err){
    if(ret.status){
        api.alert({msg:'加入组成功'});
    }else{
        api.alert({msg:err.msg});
    }
});

// 退出群组

var push = api.require('push');
push.leaveGroup({
    groupName:'department'
},function(ret,err){
    if(ret.status){
        api.alert({msg:'退出群组成功'});
    }else{
        api.alert({msg:err.msg});
    }
});

```

##获取推送消息<div id="14"></div>

push模块提供setListener方法，当通知消息到达时会通过此方法回调给前端页面，所有未处理的消息会被添加到一个数组里面返回。 注册该监听后，在应用启动的状态下，“消息”类型的推送，将直接交给该函数的回调，由开发人员自行处理推送消息，不自动弹出通知到手机状态栏。如果移除监听，则又会自动弹出通知到手机状态栏；在应用退出的状态下，“消息”类型的推送，APICloud引擎也会自动弹出通知到手机状态栏。“通知”类型的推送则会直接弹出通知到手机状态栏，不会交给监听函数的回调。 详情参考push文档setListener方法。


示例代码：

```
//设置监听
var push = api.require('push');
push.setListener(
    function(ret,err){
        if(ret){
            api.alert({msg:ret.data});
        }
    }
);

//移除监听
var push = api.require('push');
push.removeListener();

```

#**使用推送API**<div id="15"></div>

  
请参考[推送云API](http://docs.apicloud.com/%E4%BA%91API/push-cloud-api)文档。


