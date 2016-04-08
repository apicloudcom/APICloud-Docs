/*
Title: zhuge
Description: zhuge
*/

<div class="outline">

[配置Zhuge](#a1)

[initZhuge](#a2)

[track](#a3)

[identify](#a4)

[flush](#a5)

</div>



#**概述**

zhuge是[诸葛io](https://zhugeio.com/)的统计SDK，使用此模块可以使用诸葛提供的统计分析服务。

**使用此模块之前需先配置config文件的Feature，方法如下**

- 名称：zhuge
- 参数：appKey,appChannel
- 配置示例:

```js
	<feature name="zhuge">
		<param name="appKey" value="此处填写您在诸葛申请的APPKEY" />
		<param name="appChannel" value="360" />	</feature>
```

- 字段描述:

    **appKey**：诸葛为每个app生成的专属appKey
   
    **appChannel**：app分发渠道，由开发者自定义
		
		
#**配置Zhuge**<div id="a1"></div>

openLog()

openDebug()

##示例代码

```js
var zhuge = api.require('zhuge');
zhuge.openLog();
zhuge.openDebug();
```

##补充说明

**openLog()**

打开日志输出，开启此项可以在控制台看到诸葛SDK的各项日志，帮助您掌握集成情况。默认关闭。

**openDebug()**

开启实时调试，开启此项可在诸葛实时调试页面查看收集的各项信息，默认关闭。当发布应用时，应关闭此选项，防止实际用户的信息扰乱您进行实时调试。

**以上两项设置应在调用init()之前进行。**

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**initZhuge**<div id="a2"></div>

初始化诸葛

initZhuge()

##示例代码

```js
//内容类型为music或video时，内容地址应为流媒体地址;
var zhuge = api.require('zhuge');
zhuge.initZhuge();
```

##补充说明

此接口应在以下各项接口调用之前以及每个界面的入口处被调用，防止数据丢失。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**track**<div id="a3"></div>

追踪自定义事件

track({params})

##params

eventName：

- 类型：字符串
- 描述：自定义事件名称

eventPro:

- 类型：JSON对象
- 描述：（可选项）自定义事件属性，由事件属性与事件值组成


##示例代码

```js
var zhuge = api.require('zhuge');var eventProperty = {
	'种类':'手机',
	'金额':'2000',
	'品牌':'华为'
};
zhuge.track({
	eventName : '购买',
	eventPro  : eventProperty
})
```

##补充说明

调用此接口前应确保调用过一次init接口。

##可用性

iOS系统，Android系统
可提供的1.0.0及更高版本

#**identify**<div id="a4"></div>

标识用户

identify({params})

##params

uid：

- 类型：字符串
- 描述: 用户ID

userPro:

- 类型：JSON对象
- 描述：用户属性，由用户属性与值组成

##示例代码

```js
var zhuge = api.require('zhuge');var userProperties = {
	'性别':'男',
	'年龄':'20',
	'等级':'vip'
};
zhuge.identify({
	uid : '18868885853',
	userPro : userProperties
})
```

##补充说明

调用此接口前应确保调用过一次init接口。调用此接口可以将您的用户ID与诸葛平台绑定，方便您查看您的用户。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**flush**<div id="a5"></div>

上传所有信息并退出

flush()

##示例代码

```js
var zhuge = api.require('zhuge');zhuge.flush();```


##补充说明

调用此接口将认为用户退出。如果用户行为可控，建议在用户最后退出的页面进行调用。以便更及时的收集用户数据。可选

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
