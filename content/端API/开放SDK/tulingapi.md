/*
Title: tulingapi
Description: 图灵机器人
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#basic-content">方法</a></li>
	<li class=""><a href="#const-content">常量</a></li>
</ul>
<div id="basic-content">

<div class="outline">
[getTulingResult](#a1)
</div>

#**概述**

图灵机器人是光年无限旗下领先的智能机器人引擎开放平台，为广大开发者提供免费的智能机器人API端口。图灵机器人基于DeepQA深度问答技术，对中文的识别准确率高达90%，是目前中文语境下智能度最高的机器人。图灵机器人具有完全免费、高智能、一键接入、个性化、跨平台五大特点，通过图灵机器人开放平台，开发者可以方便快捷的为微信公众号、微博、QQ群、WEB网站、智能客服系统以及智能家居系统、智能车载系统等软硬件领域接入一位聪明的图灵机器人。
tulingDemo封装了图灵开放平台的SDK，使用此模块可轻松实现接入图灵SDK，使用强大的人工智能相关的功能。

暂仅支持安卓.

#**getTulingResult**<div id="a1"></div>

模块进行初始化

getTulingResult(params, callback)

##params

### appkey

- 类型：字符串
- 默认值: 无
- 描述: 从图灵开发者官网上注册账户，并获取的key，不可为null

### cmd

- 类型：字符串
- 默认值: 无
- 描述: 请求图灵接口的命令，例如”北京天气”，不可为null

##callBack

### ret

- 类型：JSON 对象
- 默认值: 无
- 内部字段: 

```
	{
		status:true ,//操作是否成功状态码
		code: 10000, //图灵API返回码
		text:”你好吗”//图灵API解析结果
	}
```
图灵API返回码, 详见[返回码](!Constant)常量

### err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""       //错误描述
}
```

##示例代码

```js
var tulingapi = api.require('tulingapi');

var input="北京天气";

var param={appkey:"60a4f78f5391dcde946cc8c5d00f7b52",cmd:input};

var resultCallback = function(ret, err)
{
    if(ret.status){
        alert(JSON.stringify(ret));
    }else{
        alert(err.msg);
    }
};

tulingapi.getTulingResult(param,resultCallback);
```

##补充说明

无

##可用性

Android系统

可提供的1.1.0及更高版本

</div>

<div id="const-content">

<div class="outline">
[返回码](#1)
</div>


#**错误码**<div id="3"></div>

错误类型

##取值范围：

code	| 说明 |
------|------|
100000|	文本类数据
200000|	网址类数据
302000	|新闻
304000|	应用、软件、下载
305000	|列车
306000	| 航班
308000 |菜谱、视频、小说
309000 | 酒店
311000 | 价格
40001	| key的长度错误（32位）
40002 | 请求内容为空
40003 | key错误或帐号未激活
40004	|当天请求次数已用完
40005 |暂不支持该功能
40006	|服务器升级中
40007	| 服务器数据格式异常

</div>