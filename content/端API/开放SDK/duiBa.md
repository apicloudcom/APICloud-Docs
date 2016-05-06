/*
Title: duiBa
Description: duiBa
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<div class="outline">
[open](#a1)

</div>

#**概述**

duiBa 封装了兑吧平台的SDK，使用此模块可实现对接兑吧积分商城功能。**duiBa 模块使用需要开发者配合开发后台相关接口供兑吧服务端调用。** 

**使用兑吧模块基本流程说明：**


1.在兑吧网站（ http://www.duiba.com.cn/ ）注册帐号，并创建应用；
2.开发者后台配置相应接口（积分消费，结果通知，虚拟商品充值）；
3.前端调用开发者自己后台接口获取到兑吧免登陆URL；
4.前端使用duiBa模块open方法打开积分商城页面供用户使用；

<div id="a1"></div>

#**open**

打开积分商城页面

open({params})

##params

url：

- 类型：字符串
- 描述：开发者后台生成的免登陆URL

navColor：

- 类型：字符串
- 描述：（可选项）兑吧页面导航条的背景颜色，请用#ffffff长格式。
- 默认值："#0acbc1"


titleColor：

- 类型：字符串
- 描述：（可选项）兑吧页面导航条的背景颜色，请用#ffffff长格式。
- 默认值："#ffffff"


##示例代码

```js
var duiba= api.require('duiBa');
duiba.open(
{
   url: "http://www.duiba.com.cn/test/demoRedirectSAdfjosfdjdsa", 
   navColor: "#0acbc1",
   titleColor: "#ffffff"
});
```

##可用性

Android系统

可提供的1.0.0及更高版本


