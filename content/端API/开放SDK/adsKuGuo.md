/*
Title: adsKuGuo
Description: adsKuGuo
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">


<div class="outline">
[init](#a1)

[show](#a2)

</div>

#**概述**

捷思广告是酷果移动广告平首创无sdk的广告模式。集成更便捷，cpc计费，轻松上市场。本模块封装了酷果捷思广告的相关接口。使用此模块之前需要先注册酷果捷思广告获取cooid（用于广告计费），详情请咨询企业QQ800050224

获取cooid方法如下：在登陆界面http://jez.kuguopush.com/login.jsp 使用自己已在酷果捷思注册的管理员账号登陆捷思管理后台，在 应用中心 -->添加应用页面中，完善要添加的app信息后保存即可得到cooid用于配置。

#**init**<div id="a1"></div>

初始化捷思广告

init({params}, callback(ret, err))

##params

id：

- 类型：字符串
- 默认值：无
- 描述：注册捷思广告后，从捷思后台获得的cooid，不可为空

version：

- 类型：字符串
- 默认值：无
- 描述：如果需要渠道号标记，可以在捷思后台新增版本号，用版本号来作为渠道标记，不可为空，如果不需要，可以填写"1"

##示例代码

```js
var kgjsapi=api.require('APIKGJS');
var param = {id:"hbfklpelkpoiddfe",version:"1"};
kgjsapi.init(param);
```

##补充说明

使用此模块，必须先用init初始化，id和version替换成你在捷思后台申请到的

##可用性

Android系统

可提供的1.0.0及更高版本


#**show**<div id="a2"></div>

显示捷思广告

show({params})

##params

mode：

- 类型：字符串
- 默认值：无
- 描述：广告类型，取值范围见[广告类型](!Constant)，不能为空

##示例代码

```js
var kgjsapi=api.require('APIKGJS');
var param = {
    mode:1
};
kgjsapi.show(param);

```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本

</div>

<div id="const-content">

#**广告类型**

广告类型。字符串类型

##取值范围：

- 1		//直接显示广告详情页面
- 3		//显示插屏
- 4		//显示全屏
- 5		//显示列表

##运行环境

- 手机必须要有网络
- 手机必须要有SIM卡
- 手机必须要挂载有SDCARD 

